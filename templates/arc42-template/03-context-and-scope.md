# 3. Context and Scope

<!-- What is inside vs outside the system boundary? -->

## 3.1 Business Context

<!-- Shows the system in its environment: who interacts with it and what they exchange. -->

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

actor "User Role A" as UserA
actor "User Role B" as UserB

rectangle "External System A" as ExtA
rectangle "«Your System»" as System #LightBlue
rectangle "External System B" as ExtB

UserA --> System : action
UserB --> System : action
ExtA --> System : data in
System --> ExtB : data out
@enduml
```

| Actor / System | Responsibility | Exchanges with system |
|----------------|---------------|-----------------------|
| | | |

## 3.2 Technical Context

<!-- Shows technical interfaces: protocols, APIs, data formats. -->

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

rectangle "External System A" as ExtA
rectangle "Your Backend" as Backend #LightBlue
rectangle "Frontend" as UI

ExtA --> Backend : REST/JSON
UI --> Backend : HTTPS/JSON
Backend --> UI : WebSocket
@enduml
```

| Peer | Interface | Direction | Protocol/Format | Notes |
|------|-----------|-----------|-----------------|-------|
| | | | | |
