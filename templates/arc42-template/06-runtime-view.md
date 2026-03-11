# 6. Runtime View

<!-- Show 2-4 key scenarios as sequence or activity diagrams. Pick scenarios that:
     - Hit multiple building blocks
     - Illustrate a quality goal (e.g., consistency, failure recovery)
     - Stakeholders ask about
-->

## 6.1 Scenario: «Happy path»

**Why this scenario matters:** <!-- link to a quality goal or stakeholder concern -->

```plantuml
@startuml
hide footbox
skinparam shadowing false

participant "Client" as Client
participant "API" as Api
participant "Service" as Service
database "Database" as DB

Client -> Api ++ : request(data)
Api -> Service --++ : processCommand(cmd)
Service -> DB : persist
Service --> Api --++ : result
Api --> Client -- : response
@enduml
```

**Failure / exception notes:**

- <!-- What happens when X fails? -->

## 6.2 Scenario: «Error / edge case»

```plantuml
@startuml
skinparam shadowing false

|Client|
start
:Perform action;
if (Online?) then (yes)
  :Send to server;
else (no)
  :Queue locally;
endif

|Server|
if (Request received?) then (yes)
  :Validate and persist;
  :Broadcast update;
endif

|Client|
if (Connection restored?) then (yes)
  :Replay queued items;
endif
stop
@enduml
```
