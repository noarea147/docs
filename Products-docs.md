# API Documentation InkLink backend

This document outlines the endpoints available on the Node.js server and their respective usage for integrating with a Unity application. Each endpoint is described in detail, including the required request body, method, and example responses.

---

## Base URL

```
http://<your-server-domain>/
```

---

## Endpoints

### 1. Get Products by Filters

**Endpoint:**

```
POST /products/getProducts
```

**Description:**
Fetch products based on multiple filters using an OR condition.

**Request Body:**

```json
{
  "filters": {
    "key": "value"
  },
  "limit": 10
}
```

**Response:**

```json
{
  "message": "Products fetched successfully",
  "data": [ ... ],
  "status": 200
}
```

---

### 2. Get Product by Slug

**Endpoint:**

```
POST /products/getProductBySlug
```

**Description:**
Fetch a single product based on its slug.

**Request Body:**

```json
{
  "slug": "product-slug"
}
```

**Response:**

```json
{
  "message": "Data fetched successfully",
  "data": { ... },
  "status": 200
}
```

---

### 3. Get Product by Name

**Endpoint:**

```
POST /products/getProductByName
```

**Description:**
Fetch products based on a partial or full name match.

**Request Body:**

```json
{
  "name": "product-name"
}
```

**Response:**

```json
{
  "message": "Data fetched successfully",
  "data": [ ... ],
  "status": 200
}
```

---

### 4. Get Products by Product Category

**Endpoint:**

```
POST /products/getProductByProductCategory
```

**Description:**
Fetch products that belong to a specific product category.

**Request Body:**

```json
{
  "ProductCategoryId": "category-id",
  "limit": 10
}
```

**Response:**

```json
{
  "message": "Categories fetched successfully",
  "data": [ ... ],
  "status": 200
}
```

---

### 5. Get Products by Business ID

**Endpoint:**

```
POST /products/getProductByBusinessId
```

**Description:**
Fetch products that belong to a specific business.

**Request Body:**

```json
{
  "businessId": "business-id",
  "limit": 10
}
```

**Response:**

```json
{
  "message": "Data fetched successfully",
  "data": [ ... ],
  "status": 200
}
```

---

### 6. Delete My Product

**Endpoint:**

```
POST /products/deleteMyProduct
```

**Description:**
Delete a product belonging to a specific business.

**Request Body:**

```json
{
  "productId": "product-id",
  "businessId": "business-id"
}
```

**Response:**

- **Success:**
  ```json
  {
    "message": "Product deleted successfully!",
    "data": { ... },
    "status": 200
  }
  ```
- **Error:**
  ```json
  {
    "message": "Product not found",
    "status": 404
  }
  ```

---

### 7. Create a Product

**Endpoint:**

```
POST /products/createProduct
```

**Description:**
Create a new product for a specific business.

**Request Body:**

```json
{
  "title": "product-title",
  "subtitle": "product-subtitle",
  "description": "product-description",
  "specification": "product-specification",
  "variants": [
    {
      "attributes": [{ "attribute": "size", "value": "large" }],
      "price": 100,
      "status": "inStock"
    }
  ],
  "image": "image-url",
  "status": "PUBLISHED",
  "productCategory": "product-category-id",
  "businessId": "business-id"
}
```

**Response:**

- **Success:**
  ```json
  {
    "message": "Product created successfully!",
    "data": { ... },
    "status": 201
  }
  ```
- **Error:**
  ```json
  {
    "message": "Something went wrong",
    "status": 500
  }
  ```

---

## Additional Notes

- **Authentication:** Ensure requests are authenticated as per the server's security settings (e.g., API keys or JWT).
- **Error Handling:** Standardized responses for errors include a message and a status code.
- **Testing:** Use tools like Postman or Unity’s networking libraries to test the API endpoints.
- **Dependencies:** The server uses `dotenv`, `Mongoose` models for database interactions, and custom utility functions.

For further assistance, contact the backend team or refer to the server’s codebase.# docs

# docs
