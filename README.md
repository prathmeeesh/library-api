# Library Management Secure API

A secure backend REST API built using ASP.NET Core and SQL Server.  
Implements authentication, authorization and protected resources using JWT tokens.

## Features
- User registration and login
- Password hashing (BCrypt)
- JWT authentication
- Protected endpoints
- Entity Framework Core database integration

## Tech Stack
- ASP.NET Core Web API
- SQL Server
- Entity Framework Core
- JWT Authentication

## Architecture
See /docs folder for diagrams.

## API Endpoints
POST /api/auth/register
POST /api/auth/login
GET /api/books (Protected)
POST /api/books (Protected)

## How to Run
1. Clone repository
2. Update connection string in appsettings.json
3. Run `Update-Database`
4. Start application

## Learning Outcome
Demonstrates backend authentication design, secure API access and database modelling.
