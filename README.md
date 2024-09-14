Here’s a detailed documentation of API Tokens to create links or get information externally

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
![image](https://github.com/user-attachments/assets/cf71f3f8-37c1-49b5-b25c-798198a3fffb)

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

- **Status Code**: `200 Created`
- **Body**:
```json
{
    "message": "Link created successfully."
}
```
![image](https://github.com/user-attachments/assets/c0e92fe2-53de-4735-aea9-0825a23680a2)

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
    "success": true,
    "data": {
        "shortLinkURL": "boot",
        "firstPage": "https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.css",
        "secondPage": "https://www.npmjs.com/package/uuid",
        "createdAt": "2024-09-14T14:41:30.000Z",
    }
}
```
![image](https://github.com/user-attachments/assets/fed4fcfa-bc4d-438a-b2f2-fcef8571845d)

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

---
