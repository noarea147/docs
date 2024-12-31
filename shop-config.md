# Save Shop Config API Documentation

## Overview
This documentation provides details for the API endpoints related to saving and retrieving shop configurations for businesses.

---

## Endpoints

### 1. Save Shop Config

**Endpoint:** `POST /saveShopConfig`

**Description:** Saves the shop configuration for a specific business. If a configuration already exists for the business, it updates the existing configuration.

**Request Body:**
```json
{
  "config": "object",
  "businessId": "string"
}
```

**Response:**
- 200: Shop config saved successfully.
```json
{
  "message": "Shop config saved successfully",
  "data": "updatedConfigObject"
}
```
- 400: Invalid business ID or missing config.
```json
{
  "message": "Invalid business ID"
}
```
```json
{
  "message": "Config is required"
}
```
- 500: Internal server error.
```json
{
  "message": "Something went wrong while saving shop config"
}
```

---

### 2. Get Shop Config By Business ID

**Endpoint:** `POST /getShopConfigByBusinessId`

**Description:** Fetches the shop configuration for a specific business by its ID.

**Request Body:**
```json
{
  "businessId": "string"
}
```

**Response:**
- 200: Shop config fetched successfully.
```json
{
  "message": "Shop config fetched successfully",
  "data": "shopConfigObject"
}
```
- 400: Invalid business ID.
```json
{
  "message": "Invalid business ID"
}
```
- 500: Internal server error.
```json
{
  "message": "Something went wrong while saving shop config"
}
```

