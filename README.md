Here’s a detailed API documentation template for your endpoints, including descriptions, request/response formats, and authentication requirements.

---

# API Documentation

## Overview

This API provides endpoints for creating and retrieving information about short links. It uses Bearer Token authentication for secure access.

### Base URL

```
http://clicktoallmylinks.com/api
```

## Authentication

All requests to the API must include a Bearer Token in the Authorization header.

### Example Header

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Endpoints

### 1. Create Short Link

- **Endpoint**: `/create`
- **Method**: `POST`
- **Description**: Create a new short link with associated pages.

#### Request

- **Headers**:
  - `Authorization`: Bearer token for authentication.
  - `Content-Type`: `application/json`

- **Body**:
```json
{
    "shortLinkURL": "boot",
    "firstPage": "https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.css",
    "secondPage": "https://www.npmjs.com/package/uuid"
}
```

- **Parameters**:
  - `shortLinkURL` (string): The identifier for the short link.
  - `firstPage` (string): The URL of the first page.
  - `secondPage` (string): The URL of the second page.

#### Response

- **Status Code**: `201 Created`
- **Body**:
```json
{
    "message": "Short link created successfully.",
    "data": {
        "shortLinkURL": "boot",
        "firstPage": "https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.css",
        "secondPage": "https://www.npmjs.com/package/uuid",
        "createdAt": "2024-09-14T12:00:00Z"
    }
}
```

- **Error Responses**:
  - **400 Bad Request**: If the request body is invalid.
  - **401 Unauthorized**: If the Bearer token is missing or invalid.

### 2. Get Short Link Info

- **Endpoint**: `/info`
- **Method**: `POST`
- **Description**: Retrieve information about a short link.

#### Request

- **Headers**:
  - `Authorization`: Bearer token for authentication.
  - `Content-Type`: `application/json`

- **Body**:
```json
{
    "shortLinkURL": "boot"
}
```

- **Parameters**:
  - `shortLinkURL` (string): The identifier for the short link whose information is to be retrieved.

#### Response

- **Status Code**: `200 OK`
- **Body**:
```json
{
    "message": "Short link information retrieved successfully.",
    "data": {
        "shortLinkURL": "boot",
        "firstPage": "https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.css",
        "secondPage": "https://www.npmjs.com/package/uuid",
        "createdAt": "2024-09-14T12:00:00Z"
    }
}
```

- **Error Responses**:
  - **400 Bad Request**: If the request body is invalid.
  - **404 Not Found**: If the short link does not exist.
  - **401 Unauthorized**: If the Bearer token is missing or invalid.

## Example Usage

### Create Short Link

```bash
curl -X POST http://clicktoallmylinks.com/api/create \
-H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
-H "Content-Type: application/json" \
-d '{
    "shortLinkURL": "boot",
    "firstPage": "https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.css",
    "secondPage": "https://www.npmjs.com/package/uuid"
}'
```

### Get Short Link Info

```bash
curl -X POST http://clicktoallmylinks.com/api/info \
-H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
-H "Content-Type: application/json" \
-d '{
    "shortLinkURL": "boot"
}'
```

## Notes

- Ensure that the Bearer token is valid and has the necessary permissions to access the endpoints.
- The `shortLinkURL` should be unique for each entry to avoid conflicts.
- All timestamps are returned in ISO 8601 format.

---

This documentation should provide your clients with a clear understanding of how to use your API, including the necessary authentication and request/response structures. Adjust any specific details as needed based on your implementation.
