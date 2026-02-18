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
