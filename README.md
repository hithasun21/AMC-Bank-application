# 🏦 AMC Bank

### Full-Stack Banking Management System

AMC Bank is a full-stack banking application developed as the final integrated project of a **10-day Java Full Stack Development training program**.

The application demonstrates the development of a secure banking system using **Java, Spring Boot, Spring Security, JWT authentication, React, and PostgreSQL**. It provides separate workflows for administrators and customers, including customer management, account operations, loan management, and customer self-service.

---

## 📌 Project Overview

AMC Bank follows a layered backend architecture and a client-server model.

The React frontend communicates with the Spring Boot backend through REST APIs. Spring Security handles authentication and authorization using JWT tokens, while Spring Data JPA and Hibernate provide persistence between the Java application and PostgreSQL database.

### High-Level Architecture

┌──────────────────────┐
│      User            │
│  Admin / Customer    │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    React + Vite      │
│      Frontend        │
└──────────┬───────────┘
           │ REST APIs
           ▼
┌──────────────────────┐
│   Spring Security    │
│   JWT Authentication │
│   Role Authorization  │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│   Controller Layer   │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│     Service Layer    │
│   Business Logic     │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│   Repository Layer   │
│   Spring Data JPA    │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│      PostgreSQL      │
│       Database       │
└──────────────────────┘

---

# ✨ Key Features

## 🔐 Authentication & Security

- Admin and customer login
- JWT-based authentication
- Role-based authorization
- `ROLE_ADMIN` and `ROLE_CUSTOMER`
- BCrypt password hashing
- Bearer-token authentication between React and Spring Boot
- Customer account ownership validation
- Protected API endpoints

---

## 👨‍💼 Admin Features

Administrators can manage the core banking operations of the application.

### Customer Management

- Create customers
- View customers
- Update customer information
- Delete customers
- Search customers

### Account Management

- Open customer accounts
- View account information
- Perform deposits
- Perform withdrawals

### Loan Management

- View loans
- Validate loan eligibility
- Sanction eligible loans
- Calculate EMI

---

## 👤 Customer Self-Service

Customers have access to their own banking information and operations.

- View personal profile
- View own accounts
- View own loans
- Deposit money
- Withdraw money
- Change password
- Access only their own active accounts

Customer operations are protected using authentication, authorization, and account ownership checks.

---

# 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| Programming Language | Java 17 |
| Backend Framework | Spring Boot 3.3.4 |
| Web Layer | Spring Web |
| Persistence | Spring Data JPA |
| ORM | Hibernate |
| Security | Spring Security |
| Authentication | JWT |
| Password Hashing | BCrypt |
| JWT Library | JJWT 0.12.6 |
| Database | PostgreSQL |
| Frontend | React |
| Frontend Tooling | Vite |
| API Communication | REST |

---

# 🏗️ Backend Architecture

The backend follows a layered architecture based on separation of responsibilities.

## 1. Controller Layer

The Controller layer handles incoming HTTP requests from the frontend.

Responsibilities:

- Define REST API endpoints
- Receive client requests
- Validate/request required input
- Communicate with the Service layer
- Return HTTP responses

Examples include authentication, customer, account, and loan endpoints.

---

## 2. Service Layer

The Service layer contains the application's business logic.

Responsibilities include:

- Processing banking operations
- Validating account transactions
- Checking account ownership
- Applying loan eligibility rules
- Performing loan calculations
- Coordinating repository operations

Keeping business logic in the Service layer prevents Controllers from becoming tightly coupled with application rules.

---

## 3. Repository Layer

The Repository layer handles persistence operations.

The application uses **Spring Data JPA** to communicate with the database.

Typical operations include:

- Save
- Find
- Update
- Delete
- Query records

Repositories provide an abstraction between the Service layer and the underlying database.

---

## 4. Database Layer

PostgreSQL is used as the relational database.

It stores persistent information required by the banking application, including customer, account, and loan data.

---

# 🔄 Application Workflow

The overall application workflow is:

User
  ↓
React Frontend
  ↓
REST API Request
  ↓
JWT Authentication
  ↓
Spring Security
  ↓
Role Authorization
  ↓
Controller
  ↓
Service
  ↓
Repository
  ↓
JPA / Hibernate
  ↓
PostgreSQL
  ↓
Response
  ↓
React Frontend

---

# 🔑 Authentication Workflow

AMC Bank uses JWT-based authentication.

1. User enters username and password
                ↓
2. React sends POST /api/login
                ↓
3. Backend authenticates credentials
                ↓
4. Password is verified securely
                ↓
5. JWT is generated
                ↓
6. React stores the token
                ↓
7. Token is sent with protected requests
                ↓
8. Spring Security validates the JWT
                ↓
9. User role is checked
                ↓
10. Authorized request reaches the Controller

Protected requests use the Bearer token format:

Authorization: Bearer <JWT>

---

# 💰 Banking Operations

## Account Operations

The application supports:

- Account creation
- Account listing
- Deposits
- Withdrawals

### Transaction Rules

- Deposit amount must be greater than `0`
- Withdrawal amount must be greater than `0`
- Withdrawal cannot exceed the available balance
- Customers can perform transactions only on their own active accounts

---

# 🏦 Loan Management

The loan module provides loan listing, eligibility validation, sanctioning, and EMI calculation.

### Loan Validation Rules

| Rule | Requirement |
|---|---|
| Minimum Principal | ₹10,000 |
| Interest Rate | > 0% and ≤ 50% |
| Loan Tenure | 1–480 months |
| Maximum Active Loans | 3 |
| Minimum Account Balance | ≥ 10% of loan principal |

### Loan Workflow

Loan Request
     ↓
Input Validation
     ↓
Eligibility Checks
     ↓
EMI Calculation
     ↓
Loan Sanction / Rejection

---

# 🌐 API Overview

## Public Endpoints

POST /api/login

Used for user authentication.

---

## Authenticated Endpoints

GET /api/auth/me

Used to retrieve information about the authenticated user.

---

## Admin APIs

/api/dashboard
/api/customers/**
/api/accounts/**
/api/loans/**

These endpoints provide administrative banking functionality.

---

## Customer APIs

/api/customer/**

These endpoints provide customer self-service functionality.

---

# 🗄️ Database Configuration

The application uses PostgreSQL.

Create the database using:

CREATE DATABASE amc_bank_customer_login;

Default classroom configuration:

Database: amc_bank_customer_login
Username: postgres
Port: 5432

Update the database credentials in:

backend/src/main/resources/application.properties

Example configuration structure:

spring.datasource.url=jdbc:postgresql://localhost:5432/amc_bank_customer_login
spring.datasource.username=postgres
spring.datasource.password=YOUR_PASSWORD

> **Note:** Do not commit real database passwords or production credentials to a public repository.

---

# 🚀 Getting Started

## Prerequisites

Make sure the following are installed:

- Java 17
- PostgreSQL
- Node.js and npm
- Eclipse IDE or another Java IDE
- VS Code or another frontend IDE

---

## 1. Clone the Repository

git clone <repository-url>
cd <project-directory>

---

## 2. Configure PostgreSQL

Start PostgreSQL and create the database:

CREATE DATABASE amc_bank_customer_login;

Update:

backend/src/main/resources/application.properties

with your local PostgreSQL credentials.

---

## 3. Run the Spring Boot Backend

Open the `backend` folder in Eclipse.

Import it as:

File
→ Import
→ Maven
→ Existing Maven Projects

Select the `backend` directory.

If required, update Maven dependencies:

Right Click Project
→ Maven
→ Update Project

Run:

AmcBankApplication.java

as a Spring Boot application.

The backend runs by default at:

http://localhost:8080

---

## 4. Run the React Frontend

Open the `frontend` folder in VS Code.

Install dependencies:

npm install

Start the development server:

npm run dev

Vite will provide a local URL, normally:

http://localhost:5173

Open the displayed URL in your browser.

---

# 🔑 Demo Credentials

### Admin

Username: admin
Password: admin123
Role: ROLE_ADMIN

### Customer

Customer credentials are generated when an administrator creates the customer.

The customer's email is used as the login username, while the initial password supplied during customer creation is used for the first login.

Customers can change their password after logging in.

> Demo credentials are intended for classroom/testing purposes only.

---

# 📁 Project Structure

The project is organized into separate frontend and backend applications.

AMC-Bank/
│
├── backend/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── ...
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   │
│   └── pom.xml
│
├── frontend/
│   ├── src/
│   │   └── ...
│   ├── package.json
│   └── vite.config.*
│
└── README.md


The backend follows the logical structure:

Controller
    ↓
Service
    ↓
Repository
    ↓
Database

---

# 🔒 Security Considerations

The project includes classroom-oriented authentication and security configuration.

For a production banking system, additional security measures would be required, including:

- Secure secret management
- Strong credential/bootstrap procedures
- HTTPS
- Token lifecycle and expiration controls
- Secure environment-based configuration
- Audit logging
- Database migration tooling
- Production-grade monitoring
- Stronger operational security controls

The demo credentials and development configuration included with the training project should **not** be used in a production environment.

---

# 🎓 Learning Outcomes

This project provided practical experience with:

- Java 17
- Object-Oriented Programming
- Spring Boot
- REST API development
- Spring Web
- Dependency Injection
- Layered architecture
- Spring Data JPA
- Hibernate
- PostgreSQL
- Spring Security
- JWT authentication
- Role-based authorization
- BCrypt password hashing
- React
- Vite
- Frontend-backend integration
- Full-stack application workflow
- Business rule implementation

---

# 📈 Future Enhancements

Potential improvements for a production-oriented version include:

- Secure external secret management
- Refresh-token based authentication
- Enhanced audit logging
- Transaction history
- Advanced account management
- Automated testing and integration testing
- Database migration management
- Cloud deployment
- CI/CD integration
- Monitoring and application logging
- Improved exception handling and API documentation

---

# 👨‍💻 Project Summary

AMC Bank demonstrates the integration of modern Java backend technologies with a React frontend to create a structured full-stack banking application.

The project combines:

Java
  +
Spring Boot
  +
Spring Security
  +
JWT
  +
Spring Data JPA
  +
Hibernate
  +
PostgreSQL
  +
React

The final application demonstrates how authentication, authorization, business logic, persistence, and frontend interaction work together in a complete full-stack application.

---

## 📄 Project Type

**Academic / Training Project**

**Domain:** Banking / FinTech

**Development Model:** Full-Stack Web Application

**Backend:** Java + Spring Boot

**Frontend:** React + Vite

**Database:** PostgreSQL

**Authentication:** JWT + Spring Security

---

## ⭐ Acknowledgement

Developed as the final integrated project during a **10-day Java Full Stack Development training program**.
