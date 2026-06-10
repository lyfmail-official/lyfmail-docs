# API Documentation

## Overview

LYF Mail API endpoints are planned for future releases. This document serves as a placeholder for upcoming API specifications.

## Authentication

All API requests will require:
- `Authorization: Bearer <token>` header
- API key from [app.example.com](https://app.example.com)

## Rate Limits

| Plan | Requests/Minute | Requests/Hour |
|------|----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |
| Enterprise | Unlimited | Unlimited |

## Planned Endpoints

### Newsletters
```
GET /api/v1/newsletters
GET /api/v1/newsletters/{id}
POST /api/v1/newsletters/subscribe
```

### Health Data (Ebb)
```
POST /api/v1/health/encrypted
GET /api/v1/health/summary
```

## Response Format

All responses will be JSON:
```json
{
  "status": "success",
  "data": {},
  "meta": {
    "timestamp": "2026-06-10T12:00:00Z",
    "request_id": "uuid"
  }
}
```

## Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK |
| 400 | Bad Request |
| 401 | Unauthorized |
| 429 | Rate Limited |
| 500 | Server Error |
