# Kheyma Backend

**Kheyma Backend** is the Spring Boot-powered backend for the Kheyma camping reservation platform, built to provide secure and efficient APIs for campsite discovery, user authentication, reviews, booking, and administration.

---

## 🌟 Core Features

- **User Management/Auth**: JWT-based authentication with role-based access control (USER, ADMIN).
- **Campsites**: CRUD operations for campsite listings, including filters and reviews.
- **Booking System**: Transaction lifecycle management with optional cancellation flow.
- **Admin Console**: Secure endpoints for managing users and monitoring statistics.
- **MongoDB Integration**: Persistent, scalable database support for users, locations, reviews, and transactions.

---

## 🛠️ Technology Stack

<p align="center">
  <img src="https://img.shields.io/badge/Java-17%2B-007396?style=for-the-badge&logo=java&logoColor=white" alt="Java Badge">
  <img src="https://img.shields.io/badge/Spring%20Boot-3.2.0-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot Badge">
  <img src="https://img.shields.io/badge/MongoDB-NoSQL-47a248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB Badge">
  <img src="https://img.shields.io/badge/Spring%20Security-Authorization-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white" alt="Spring Security Badge">
  <img src="https://img.shields.io/badge/JWT-Secure%20Auth-black?style=for-the-badge&logo=jsonwebtokens&logoColor=white" alt="JWT Badge">
  <img src="https://img.shields.io/badge/Maven-Dependency_Management-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white" alt="Maven Badge">
</p>

---

## ⚙️ Getting Started

### Prerequisites

Ensure the following are installed:

- **Java 17+**
- **Maven 3.6+**
- **MongoDB** (default URI: `mongodb://localhost:27017`)

### Installation & Setup

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-repo/kheyma-backend.git
   cd kheyma-backend
   ```

2. **Configure database and JWT secret**:
   Update `src/main/resources/application.yml`:

   ```yaml
   spring:
     data:
       mongodb:
         uri: mongodb://localhost:27017/kheyma
   jwt:
     secret: your-secret-key
   ```

3. **Run the backend service** with Maven:

   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

4. Access your API at `http://localhost:8080/api`.

---

## 📌 API Highlights

### Key Endpoints

- **Authentication**: `/api/auth` for login/registration/refresh (JWT-based).
- **Locations**: CRUD at `/api/locations` with public access for searching.
- **Reviews**: `/api/reviews` for location reviews with owner/admin control.
- **Transactions (Bookings)**: Manage `/api/transactions` for booking flow.
- **Admin Tools**: `/api/admin` for user roles, stats, and content moderation.

> For a full list of endpoints, refer to [API_ENDPOINTS.md](API_ENDPOINTS.md).

---

## 🔐 Core Security Features

- **JWT Authentication**: Tokens secured with `HS256` algorithm.
- **BCrypt Password Encryption**: All user credentials securely hashed.
- **Role-Oriented Authorization**:
  - `ROLE_USER`: Access to general endpoints (listings, reviews, transactions).
  - `ROLE_ADMIN`: Full access to modify users, statistics, and content.
- **CORS Settings**: Preconfigured for frontend integration.

---

## 📂 Project Structure

```
src/main/
├── java/com/kheyma/
│   ├── aop/               # Logging, performance, security advice
│   ├── config/            # Configuration for AOP, MongoDB, etc.
│   ├── controller/        # REST endpoints for Auth, Locations, Reviews, etc.
│   ├── database/          # Initializers/Seeders for test data
│   ├── dto/               # Data Transfer Objects (DTOs)
│   ├── exception/         # Global error handlers
│   ├── model/             # Data models for MongoDB entities
│   ├── repository/        # Interfaces for persistence
│   ├── security/          # JWT filters and configurations
│   └── service/           # Business logic services
└── resources/
    ├── application.yml    # Main configuration
    └── static/            # (Optional) Static assets directory
```

---

## 📊 Database Overview

**Collections**:

- **`users`**: Stores user credentials and roles.
- **`locations`**: Camping site details (title, description, pricing, geo-coordinates, etc.).
- **`reviews`**: User-provided ratings and comments on locations.
- **`transactions`**: Booking flow with status and payment info.

> See the [`Entity Relationship Diagram Representation`](docs/ERD.svg) for relationships.
