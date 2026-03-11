# 7. Deployment View

## 7.1 Primary Deployment

```plantuml
@startuml
skinparam shadowing false

node "Host / Cloud" #lightgreen {
  node "Container Runtime" #white {
    artifact "Frontend\n(container)" as UI
    artifact "Backend\n(container)" as Backend
  }
  database "Database" as DB
}

cloud "External Systems" #lightblue {
  node "External API" as ExtApi
}

UI --> Backend : HTTPS
Backend --> DB : SQL
Backend --> ExtApi : REST
@enduml
```

### Mapping

| Building block | Runs on | Notes |
|---------------|---------|-------|
| | | |

### Runtime Configuration

<!-- Document deployment-owned settings that affect behavior. -->

```json
{
  "App": {
    "Setting": "value"
  }
}
```
