# Save Shop Config API Documentation

## Overview

The `saveShopConfig` endpoint allows users to save or update the configuration for a specific business. If the configuration does not exist for the given business ID, a new record will be created.

## Endpoint

**URL:** `/saveShopConfig`

**Method:** `POST`

**Description:** Saves or updates shop configuration for a business.

## Request Body

```json
{
  "config": "object", // Configuration details for the shop
  "businessId": "string" // Valid MongoDB ObjectId of the business
}
```

### Fields

- **config** (required): The configuration object containing details about the shop.
- **businessId** (required): A valid MongoDB ObjectId representing the business.

## Responses

### Success Response

**Status Code:** `200`

```json
{
  "message": "Shop config saved successfully",
  "data": {
    "_id": "string",
    "businessId": "string",
    "config": "object",
    "__v": "number"
  }
}
```

- **message:** A success message.
- **data:** The saved or updated shop configuration document.

### Error Responses

**Status Code:** `400`

- **Invalid business ID:**
  ```json
  {
    "message": "Invalid business ID"
  }
  ```
- **Config is required:**
  ```json
  {
    "message": "Config is required"
  }
  ```

**Status Code:** `500`

- **Internal Server Error:**
  ```json
  {
    "message": "Something went wrong while saving shop config"
  }
  ```

## Implementation Details

The `saveShopConfig` function performs the following steps:

1. Validates the `businessId` field to ensure it is a valid MongoDB ObjectId.
2. Checks if the `config` field is provided.
3. Uses `findOneAndUpdate` with the `upsert` option to save or update the configuration:
   - If a record for the `businessId` exists, it is updated.
   - If no record exists, a new record is created.
4. Returns the updated configuration or an error message.

## Error Handling

- Validates input data to prevent invalid or missing fields.
- Catches and logs any unexpected errors.

## Example Request

### Request

```bash
POST /saveShopConfig
Content-Type: application/json

{
  "config": {
    "theme": "dark",
    "currency": "USD"
  },
  "businessId": "64e20c3a88a1d8e74110a8b2"
}
```

### Response

```json
{
  "message": "Shop config saved successfully",
  "data": {
    "_id": "64e20c3a88a1d8e74110a8b2",
    "businessId": "64e20c3a88a1d8e74110a8b2",
    "config": {
      "theme": "dark",
      "currency": "USD"
    },
    "__v": 0
  }
}
```
