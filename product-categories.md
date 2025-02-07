# Get All Product Categories

**Endpoint**:  
`POST /product-categories/getProductCategories`

**Description**:  
Retrieves a list of product categories with an optional limit on the number of categories returned.

---

## Request

**Headers**:

- `Content-Type: application/json`

**Body Parameters**:  
| Field | Type | Required | Description |
|-------|--------|----------|-------------------------------------------|
| limit | number | No | Maximum number of product categories to retrieve. Default is 10. |

**Example Request**:

```json
{
  "limit": 5
}
```

---

## Response

**Success (200)**:  
A JSON response containing the retrieved product categories.

```json
{
  "message": "Categories fetched successfully",
  "statusCode": 200,
  "data": [
    {
      "_id": "62c9f9bf2b24f4f56e3e8c10",
      "name": "Electronics",
      "description": "All electronic gadgets and accessories"
    },
    {
      "_id": "62c9f9bf2b24f4f56e3e8c11",
      "name": "Home Appliances",
      "description": "Appliances for everyday home use"
    }
  ]
}
```

**Error (400)**:  
If the `limit` parameter is invalid.

```json
{
  "message": "Invalid limit parameter",
  "statusCode": 400
}
```

**Error (500)**:  
If an unexpected error occurs.

```json
{
  "message": "Something went wrong",
  "statusCode": 500
}
```

---

## Notes

1. **Limit Parameter**:

   - The `limit` parameter should be a positive integer.
   - If not provided, the API defaults to a limit of 10.

2. **Error Handling**:

   - Validation errors return a `400` status code.
   - Server errors return a `500` status code with a generic error message.

3. **Default Limit**:
   - To prevent fetching an excessive number of records, the system defaults to a `limit` of 10.

---

## Sample cURL Request

```bash
curl -X POST http://<server-domain>/categories/getAllProductCategories \
-H "Content-Type: application/json" \
-d '{
  "limit": 5
}'
```
