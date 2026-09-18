# 📡 FitFlow API Documentation

## Base URL

```
Development: http://localhost:3000/api/v1
Production:  https://api.fitflow.app/v1
```

## Authentication

All protected endpoints require a Bearer token in the Authorization header:

```
Authorization: Bearer <jwt_token>
```

---

## Endpoints

### Auth

| Method | Endpoint              | Description          | Auth Required |
|--------|----------------------|----------------------|---------------|
| POST   | `/auth/register`     | Register new user    | ❌            |
| POST   | `/auth/login`        | Login user           | ❌            |
| POST   | `/auth/logout`       | Logout user          | ✅            |
| POST   | `/auth/refresh-token`| Refresh JWT token    | ✅            |
| GET    | `/auth/oauth/:provider` | OAuth login       | ❌            |

### Users

| Method | Endpoint          | Description           | Auth Required |
|--------|------------------|-----------------------|---------------|
| GET    | `/users/me`      | Get current user      | ✅            |
| PUT    | `/users/me`      | Update current user   | ✅            |
| PUT    | `/users/me/avatar` | Update avatar       | ✅            |
| DELETE | `/users/me`      | Delete account        | ✅            |

### Workouts

| Method | Endpoint                 | Description          | Auth Required |
|--------|-------------------------|----------------------|---------------|
| GET    | `/workouts`             | List all workouts    | ✅            |
| POST   | `/workouts`             | Create workout       | ✅            |
| GET    | `/workouts/:id`         | Get workout by ID    | ✅            |
| PUT    | `/workouts/:id`         | Update workout       | ✅            |
| DELETE | `/workouts/:id`         | Delete workout       | ✅            |
| POST   | `/workouts/:id/complete`| Mark as completed    | ✅            |

### Progress

| Method | Endpoint                  | Description           | Auth Required |
|--------|---------------------------|-----------------------|---------------|
| GET    | `/progress`              | Get progress history  | ✅            |
| POST   | `/progress`              | Log new progress      | ✅            |
| GET    | `/progress/stats`        | Get aggregated stats  | ✅            |
| GET    | `/progress/chart/:metric`| Get chart data        | ✅            |

### AI Recommendations

| Method | Endpoint                | Description            | Auth Required |
|--------|------------------------|------------------------|---------------|
| GET    | `/ai/recommendations`  | Get workout recs       | ✅            |
| POST   | `/ai/analyze`          | Analyze user progress  | ✅            |
| GET    | `/ai/insights`         | Get AI insights        | ✅            |

---

## Error Response Format

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": [
      {
        "field": "email",
        "message": "Must be a valid email address"
      }
    ]
  }
}
```

## Status Codes

| Code | Description                |
|------|----------------------------|
| 200  | Success                    |
| 201  | Created                    |
| 400  | Bad Request                |
| 401  | Unauthorized               |
| 403  | Forbidden                  |
| 404  | Not Found                  |
| 429  | Too Many Requests          |
| 500  | Internal Server Error      |

---

*Last updated: September 2026*
