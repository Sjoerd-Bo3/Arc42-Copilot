# 5. Building Block View

## 5.1 Level 1 — White-box Overall System

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

rectangle "External System" as Ext

package "Your System" #LightBlue {
  rectangle "Component A" as A
  rectangle "Component B" as B
  rectangle "Component C" as C
  database "Database" as DB
}

Ext --> A : input
A --> B : internal
B --> C : internal
C --> DB : persist
@enduml
```

| Block | Responsibility | Key Interfaces |
|-------|---------------|----------------|
| | | |

## 5.2 Level 2 — Component Detail

<!-- Decompose the most important Level 1 blocks. Only add levels that provide value. -->

```plantuml
@startuml
skinparam shadowing false
skinparam componentStyle rectangle

package "Component A (white-box)" {
  rectangle "Sub-module 1" as S1
  rectangle "Sub-module 2" as S2
  rectangle "Sub-module 3" as S3
}

S1 --> S2
S2 --> S3
@enduml
```

| Element | Responsibility | Depends on |
|---------|---------------|------------|
| | | |
