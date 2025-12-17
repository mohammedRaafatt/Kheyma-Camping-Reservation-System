# KHEYMA — Campsite Reservation Platform

Full-stack web app for discovering, reviewing, and booking campsites across Egypt. Backend is a Spring Boot + MongoDB service with JWT security and AOP logging; frontend is a React + Vite SPA styled with Tailwind. Project assets include SRS, UML, sequence, and ERD diagrams for quick onboarding.

## Contents
- `kheyma_backend/` — Spring Boot 3 service (JWT auth, MongoDB, AOP logging, admin console)
- `kheyma_frontend/` — React 19 + Vite client (routing, auth context, booking flows)
- Diagrams: `Activity_diagram.png`, `Class Diagram with OCL.svg`, `Use Case Diagram with OCL.svg`, `Sequence Diagram.svg`, `ERD.svg`
- Docs: `SRS.docx`, `kheyma_backend/API_ENDPOINTS.md`

## Core Features
- Secure auth with JWT (login/register/refresh, role-based access: USER, ADMIN)
- Campsite CRUD with search, filters, image URLs, and pagination
- Reviews and ratings per campsite
- Booking/transaction lifecycle with cancel flow
- Admin tools for user management and stats
- CORS ready for local dev; request/exception/performance logging via AOP

## Prerequisites
- Java 17+, Maven 3.6+
- Node.js 18+ (Vite requires modern Node), npm
- MongoDB (default `mongodb://localhost:27017/kheyma`)

## Quick Start
1) Backend  
```bash
cd kheyma_backend
# optional: export JWT_SECRET=your-secret MONGODB_URI=...
mvn spring-boot:run
```
- Runs at `http://localhost:8080/api` (context-path `/api`).
- Config file: `kheyma_backend/src/main/resources/application.yml`.

2) Frontend  
```bash
cd kheyma_frontend
npm install
npm run dev -- --host --port 5173
```
- App served at `http://localhost:5173` and points to the backend via `VITE_API_BASE_URL` (default `http://localhost:8080/api`).
- Create `.env` in `kheyma_frontend/` if you need a custom API URL:
  ```
  VITE_API_BASE_URL=http://localhost:8080/api
  ```

## Backend Configuration Highlights
- `spring.data.mongodb.uri`: override with `MONGODB_URI` or edit `application.yml`.
- `jwt.secret`: uses `JWT_SECRET` env var when set (default in `application.yml`).
- CORS: `app.cors.allowed-origins` already includes common Vite ports (5173/5174, 3000/3001).
- Multipart uploads enabled (10 MB).

## API
- Full endpoint list: `kheyma_backend/API_ENDPOINTS.md`.
- Base path: `/api`.
- Key groups: `/auth`, `/locations`, `/reviews`, `/transactions`, `/admin`.

## Database
- Mongo collections: `users`, `locations`, `reviews`, `transactions`.
- ERD: `ERD.svg` (see root). Data initializer seeds sample content when enabled.

## Frontend Notes
- Routing and pages in `kheyma_frontend/src/pages/` (home, listing, detail, booking, auth, profile, admin dashboard).
- API client with JWT header injection: `kheyma_frontend/src/services/api.js`.
- Global auth state: `kheyma_frontend/src/contexts/AuthContext.jsx`.

## Run Books
- Build backend: `mvn clean package` (artifact in `kheyma_backend/target/`).
- Build frontend: `npm run build` (output in `kheyma_frontend/dist/`).
- Lint frontend: `npm run lint`.

## References
- System docs: `SRS.docx`, UML & sequence diagrams in root for architecture/context.
- Logging/AOP: see `kheyma_backend/src/main/java/com/kheyma/aop`.
- Security: see `kheyma_backend/src/main/java/com/kheyma/security`.

## Contributing
Use conventional PRs, keep environment-specific secrets out of source, and prefer configuration via environment variables over editing committed YAML. Run lint/build before submitting changes.