# Library API — Original Source Prototype

> **Live Folio demo:** [Folio — Library Management System](https://prathmesh-library.runasp.net/) is a non-commercial **read-only portfolio demonstration** with 15 synthetic books. Visitors can browse and search; registration, login, borrowing, returns, and administration are disabled on the hosted site.

> **Source status:** This branch currently contains the original API-era prototype, **not** the full ASP.NET Core 10 Folio implementation behind the live demonstration. The completed local implementation has been tested separately and awaits a reviewed GitHub source publication. Do not treat the runtime or endpoints below as documentation for the deployed demo.

> **Security note:** Earlier commits contained an exposed JWT signing value. Newer source must use independently generated secrets supplied via protected configuration; historical credential retirement remains a separate operational review.

---

# Secure Library Management API

Production-style REST API built using ASP.NET Core and SQL Server demonstrating authentication, authorization and protected resources using JWT tokens.

---

## Key Features
- User Registration & Login
- Password hashing using BCrypt
- JWT Token authentication
- Protected endpoints
- Entity Framework Core database integration
- Role-based authorization ready

---

## Tech Stack
- ASP.NET Core Web API
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

## Running the Project

1. Clone repository
2. Update connection string in `appsettings.json`
3. Run database migration:
   ```
   Update-Database
   ```
4. Start application
5. Use Swagger UI for testing

---

## Learning Outcomes
This project demonstrates backend authentication design, secure API access and relational database modelling following real-world software engineering practices.
