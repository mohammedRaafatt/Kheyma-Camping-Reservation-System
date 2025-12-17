# 📖 KHEYMA API Endpoints Reference

**Base URL:** `http://localhost:8080/api`

Welcome to the **KHEYMA API Reference**! This guide provides detailed information about the available endpoints, their expected request/response formats, and authentication requirements.

---

## 🔐 **Authentication Endpoints** (`/api/auth`)

| Method | Endpoint         | Auth?  | Description                          |
| ------ | ---------------- | ------ | ------------------------------------ |
| POST   | `/auth/register` | ❌ No  | Register a new user                  |
| POST   | `/auth/login`    | ❌ No  | Authenticate and get a JWT token     |
| POST   | `/auth/refresh`  | ✅ Yes | Refresh an existing JWT token        |
| GET    | `/auth/me`       | ✅ Yes | Get the current user's profile data  |
| PUT    | `/auth/me`       | ✅ Yes | Update the authenticated user's data |

**Example Request/Response**

- **Register: POST `/auth/register`**

  ```json
  Request Body:
  {
    "email": "user@example.com",
    "password": "password123",
    "name": "John Doe",
    "phoneNumber": "+201234567890"
  }

  Response (201 Created):
  {
    "token": "jwt-token-string",
    "expiresIn": 86400,
    "user": { ... }
  }
  ```

- **Get Profile: GET `/auth/me`**
  ```json
  Response (200 OK):
  {
    "id": "user-id",
    "email": "user@example.com",
    "name": "John Doe",
    "roles": ["ROLE_USER"],
    "phoneNumber": "+201234567890",
    "active": true
  }
  ```

---

## 📍 **Location Endpoints** (`/api/locations`)

| Method | Endpoint                 | Auth?                | Description                           |
| ------ | ------------------------ | -------------------- | ------------------------------------- |
| GET    | `/locations/public/all`  | ❌ No                | View all public locations (paginated) |
| GET    | `/locations/{id}`        | ❌ No                | Fetch location details using its ID   |
| GET    | `/locations/search`      | ❌ No                | Advanced search with filters          |
| POST   | `/locations`             | ✅ Yes (USER)        | Create a new campsite location        |
| PUT    | `/locations/{id}`        | ✅ Yes (Owner/Admin) | Update location details               |
| DELETE | `/locations/{id}`        | ✅ Yes (Owner/Admin) | Remove the location                   |
| POST   | `/locations/{id}/images` | ✅ Yes (Owner/Admin) | Upload location image URLs            |

### Filters & Query Parameters

- **Search Locations: GET `/locations/search`**
  - **Filters**: `q`, `lat`, `lng`, `radius`, `tags`, `minPrice`, `maxPrice`
  - **Paginate**: `page`, `size`
  - **Sort By**: `sortBy` and `sortDir`

**Example Requests**

- **POST Create Location**

  ```json
  Request Body:
  {
    "title": "Beachfront Oasis",
    "description": "Luxury campsite near the Red Sea.",
    "pricePerNight": 150,
    "tags": ["beach", "oasis"],
    "latitude": 27.2578,
    "longitude": 33.8129,
    "locationType": "BEACH"
  }

  Response (201 Created):
  {
    "id": "location-id",
    "title": "Beachfront Oasis",
    ...
  }
  ```

**Location Types**: `DESERT`, `OASIS`, `PROTECTORATE`, `MOUNTAIN`, `BEACH`, `FOREST`

---

## ⭐ **Review Endpoints** (`/api/reviews`)

| Method | Endpoint                         | Auth?          | Description                          |
| ------ | -------------------------------- | -------------- | ------------------------------------ |
| POST   | `/reviews`                       | ✅ Yes (USER)  | Submit a review for a location       |
| GET    | `/reviews/location/{locationId}` | ❌ No          | List reviews for a specific location |
| PUT    | `/reviews/{id}`                  | ✅ Yes (Owner) | Edit a submitted review              |
| DELETE | `/reviews/{id}`                  | ✅ Yes (Owner) | Delete an existing review            |

**Note**: Users can only post one review per location.

---

## 💳 **Transactions (Booking)** (`/api/transactions`)

| Method | Endpoint                    | Auth?         | Description                       |
| ------ | --------------------------- | ------------- | --------------------------------- |
| POST   | `/transactions`             | ✅ Yes (USER) | Create and confirm a booking      |
| GET    | `/transactions/user`        | ✅ Yes (USER) | View transactions by current user |
| PUT    | `/transactions/{id}/cancel` | ✅ Yes        | Cancel a transaction              |

**Example: Create a Booking**

```json
Request Body:
{
    "locationId": "location-id",
    "amount": 300.00,
    "startDate": "2025-07-01",
    "endDate": "2025-07-05",
    "paymentMethod": "CARD"
}

Response (201 Created):
{
    "id": "transaction-id",
    "status": "CONFIRMED",
    "userId": "user-id",
    "amount": 300.00,
    ...
}
```

**Payment Methods**: `CARD`, `PAYPAL`, `CASH`  
**Status Updates**: `PENDING`, `CONFIRMED`, `CANCELLED`

---

## 👑 **Admin Endpoints** (`/api/admin`)

**Admin-only endpoints require authentication with `ROLE_ADMIN`.**

| Method | Endpoint            | Description                    |
| ------ | ------------------- | ------------------------------ |
| GET    | `/admin/users`      | Retrieve all registered users  |
| DELETE | `/admin/users/{id}` | Soft delete or deactivate user |
| GET    | `/admin/stats`      | View aggregated statistics     |

---

## 🚀 **Key Notes**

- **Authentication**:
  - Include in all secured endpoints:
    ```
    Authorization: Bearer <jwt_token>
    ```
- **Base Path**: All endpoints use the base path `/api`.
- **Paginated Responses**:
  ```json
  {
    "content": [...],
    "page": 0,
    "size": 20,
    "totalElements": 100,
    "totalPages": 5,
    "last": false
  }
  ```
- **Roles & Permissions**:
  - `ROLE_USER`: Basic user-level rights
  - `ROLE_ADMIN`: Full system access

🎉 Thank you for exploring the KHEYMA APIs!
