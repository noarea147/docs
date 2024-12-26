# Business API Documentation

This document describes the endpoints and methods available for managing businesses in the application.

## Table of Contents

- [Create Business](#create-business)
- [Get My Businesses](#get-my-businesses)
- [Get Business By ID](#get-business-by-id)
- [Delete Business](#delete-business)
- [Update My Business](#update-my-business)

## Endpoints

### 1. Create Business

**Endpoint:** `POST /createBusiness`

**Description:** Creates a new business and associates it with the requesting user.

**Request Body:**

```json
{
  "name": "string",
  "address": {
    "streetAddress": "string",
    "zipCode": "string",
    "state": "string"
  },
  "publicPhone": "string",
  "publicEmail": "string",
  "description": "string",
  "image": "string",
  "businessCategory": "string"
}
```

**Response:**

- 201: Point of sale created successfully.
- 400: Request under review.
- 500: Failed to create point of sale.

---

### 2. Get My Businesses

**Endpoint:** `POST /getMyBusinesses`

**Description:** Fetches businesses created by the requesting user.

**Request Body:**

```json
{
  "limit": "number"
}
```

**Response:**

- 200: Businesses fetched successfully.
- 404: User not found.
- 500: Something went wrong.

---

### 3. Get Business By ID

**Endpoint:** `POST /getBusinessById`

**Description:** Fetches details of a specific business by ID.

**Request Body:**

```json
{
  "businessId": "string"
}
```

**Response:**

- 200: Business fetched successfully.
- 404: User or Business not found.
- 500: Something went wrong.

---

### 4. Delete Business

**Endpoint:** `POST /deleteBusiness`

**Description:** Deletes a specific business owned by the user.

**Request Body:**

```json
{
  "businessId": "string"
}
```

**Response:**

- 200: Business deleted successfully.
- 401: No permission to delete business.
- 404: User or Business not found.
- 500: Something went wrong.

---

### 5. Update My Business

**Endpoint:** `POST /UpdateMyBusiness`

**Description:** Updates business details.

**Request Body:**

```json
{
  "id": "string",
  "name": "string",
  "publicPhone": "string",
  "publicEmail": "string",
  "description": "string",
  "address": {
    "streetAddress": "string",
    "zipCode": "string",
    "state": "string"
  }
}
```

**Response:**

- 200: Profile updated successfully.
- 400: Invalid or missing `id` field.
- 404: Business not found.
- 500: Error occurred while updating.

## Logging

Errors and events are logged using the `LOG` module for debugging and monitoring.
