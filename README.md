# Library API — Original Source Prototype

> **Live Folio demo:** [Folio — Library Management System](https://prathmesh-library.runasp.net/) is a non-commercial **read-only portfolio demonstration** with 15 synthetic books. Visitors can browse and search; registration, login, borrowing, returns, and administration are disabled on the hosted site.

> **Source status:** This branch currently contains the original API-era prototype, **not** the full ASP.NET Core 10 Folio implementation behind the live demonstration. The completed local implementation has been tested separately and awaits a reviewed GitHub source publication. Do not treat the runtime or endpoints below as documentation for the deployed demo.

> **Security note:** Commits `50fa502` and `034580f` committed a JWT signing key in `appsettings.json`. That key is treated as **compromised** and must never be used. It has been removed from the current branch, but it remains in Git history, so removing it does not make it safe again. Supply your own secrets through environment variables or other untracked configuration (see [Running the Project](#running-the-project)). The Folio application refuses to start with the historical key. See [SECURITY.md](SECURITY.md).

> **Runtime status:** This prototype targets .NET 8, which reached end of support on 10 November 2026. It is kept for reference and is not maintained.

---

# Library Management API (original prototype)

Learning-prototype REST API built with ASP.NET Core 8 and SQL Server, demonstrating JWT authentication and protected endpoints.

---

## Key Features
- User Registration & Login
- Password hashing using BCrypt
- JWT Token authentication
- Protected endpoints
- Entity Framework Core database integration
- Role claim included in issued JWTs (no role-restricted endpoints)

---

## Tech Stack
- ASP.NET Core 8 Web API
- SQL Server
- Entity Framework Core
- JWT Authentication
- Swagger API documentation

---

## System Architecture
See: docs/architecture.md

## Database Schema
See: docs/database.md

## Authentication Flow
See: docs/sequence.md

---

## API Endpoints

### Auth
POST /api/auth/register  
POST /api/auth/login  

### Books (Protected)
GET /api/books  
POST /api/books  

---

## Known Limitations
- Any authenticated user can add books; there are no administrator-only endpoints.
- `POST /api/books` binds the `Book` entity directly, so clients can set fields such as `Id` and `IsBorrowed`.
- Token audience validation uses the issuer value.
- Borrowing is modelled in the database but has no endpoints.

The Folio implementation addresses these; its source is not yet published here.

---

## Running the Project

Configuration is supplied outside source control. The application does not start without `Jwt:Key`.

1. Clone the repository.
2. Provide configuration as environment variables, or in an untracked `appsettings.Development.json` (git-ignored):
   - `ConnectionStrings__Default`: your SQL Server connection string
   - `Jwt__Key`: a new random key of at least 32 bytes. Never reuse the historical key.
   - `Jwt__Issuer`: an issuer name (also used as the token audience)

   PowerShell example for the session that runs the app (the key is generated and never displayed):
   ```powershell
   $rng = [System.Security.Cryptography.RandomNumberGenerator]::Create()
   $bytes = [byte[]]::new(64); $rng.GetBytes($bytes); $rng.Dispose()
   $env:Jwt__Key = [Convert]::ToBase64String($bytes); [Array]::Clear($bytes, 0, $bytes.Length)
   $env:Jwt__Issuer = 'LibraryApi.Local'
   $env:ConnectionStrings__Default = 'Server=(localdb)\MSSQLLocalDB;Database=LibraryApiLocal;Integrated Security=true;TrustServerCertificate=true'
   ```
   If you start the app from Visual Studio, use the untracked `appsettings.Development.json` instead.
3. Apply the database migrations: `Update-Database` (Package Manager Console) or `dotnet ef database update`.
4. Start the application with `dotnet run`.
5. Swagger UI is available in the Development environment.

---

## Learning Outcomes
This project demonstrates backend authentication design, secure API access and relational database modelling following real-world software engineering practices.
