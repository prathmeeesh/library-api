# System Architecture

```mermaid
flowchart LR

Client[Client / Browser / Swagger]
API[ASP.NET Controllers]
Auth[JWT Authentication Middleware]
Service[Business Logic & TokenService]
DB[(SQL Server Database)]

Client --> API
API --> Auth
Auth --> API
API --> Service
Service --> DB
DB --> API
API --> Client
```
