# 6. Runtime View

## 6.1 Scenario: Create/update order on appointment import

**Why this scenario matters:** It hits the core value — planning-to-execution sync. It exercises consistency, auditability, and integration boundaries.

```plantuml
@startuml
hide footbox
skinparam shadowing false

participant "Planning Service" as Planning
participant "Sync Adapter" as Sync
participant "Backend API" as Api
participant "Work Order Module" as WOD
database "Pitstop DB" as DB
participant "Audit/Event Log" as Audit
participant "Workshop View UI" as UI

== Import appointment ==
Planning -> Sync ++ : appointmentChanged(appointment)
Sync -> Api --++ : upsertAppointment(mapped)

Api -> WOD --++ : UpsertWorkOrderFromAppointment(cmd)
WOD -> DB : load/update work order
WOD -> Audit : appendEvent(WorkOrderUpserted)
WOD --> Api --++ : result(workOrderId, state)

Api -> UI -- : pushUpdate(workOrder summary)\n(WS, target: 2s)

== Workshop progress ==
UI -> Api ++ : updateStatus(WO-7781, WaitingForParts, note)
Api -> WOD --++ : ChangeStatus(cmd)
WOD -> DB : persist new state
WOD -> Audit : appendEvent(StatusChanged)

WOD -> Sync --++ : integrationEvent(StatusChanged)
Sync -> Planning -- : statusUpdate(delay/ready/reschedule)
@enduml
```

**Failure / exception notes:**

- **Planning API unavailable**: Sync queues outbound updates with retry + backoff.
- **Duplicate appointment updates**: Idempotency key (appointmentId + version/timestamp).
- **Conflicting edits**: "Last-write-wins" only for safe fields; status changes may require foreman override.

## 6.2 Scenario: Degraded-mode workshop updates (offline then sync)

**Why this scenario matters:** Mechanic keeps working even if Wi-Fi is spotty. Updates are queued locally and reconciled when online. Exercises availability and conflict handling.

```plantuml
@startuml
skinparam shadowing false

|Workshop View UI|
start
:Mechanic updates status + note;
:Store update in local queue;
if (Online?) then (yes)
  :Send update to Backend;
else (no)
  :Show "Queued" indicator;
endif

|Backend|
if (Update received?) then (yes)
  :Validate permissions + state rules;
  :Persist + append audit event;
  :Broadcast to other clients;
endif

|Workshop View UI|
if (Connection restored?) then (yes)
  :Replay queued updates;
  :Handle conflicts (merge rules);
endif
stop
@enduml
```

**Conflict handling rules:**

- **Notes**: append (safe merge).
- **Status changes**: validate allowed transitions; reject invalid transitions with a clear "needs foreman review" message.
