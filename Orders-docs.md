# API Documentation for Orders

This document outlines the endpoints available on the Node.js server for managing orders. Each endpoint is described in detail, including the required request body, method, and example responses.

---

## Base URL

```
http://<your-server-domain>/
```

---

## Endpoints

### 1. Place Order

**Endpoint:**

```
POST /orders/order-client-or-guest
```

**Description:**
Place an order for one or more products grouped by business.

**Request Body:**

```json
{
  "orderSummary": {
    "fullName":"user",
    "phoneNumber":"25445558",
    "email":"email@gmail.com",
    "products": [
      {
        "id":"67405b1b2fb6ea7db0417308",
        "variant":[{"attribut" : "value"}],
        "price":45,
        "quantity":4,
        "businessId": "67405b0b2fb6ea7db0417306"

      }
    ],
    "shippingAddress": "123 Test Street",
    "shippingDate": "2024-07-21T00:00:00.000Z",  
    "notes": "This is a test order note",
    "delivery":"STORE_PICKUP"
  }
}
```

**Response:**

- **Success:**
  ```json
  {
    "message": "Order placed successfully",
    "data": [ ... ],
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

### 2. Get Orders by User

**Endpoint:**

```
POST /orders/getOrdersByUser
```

**Description:**
Retrieve orders for the authenticated user.

**Request Body:**

```json
{
  "limit": 10
}
```

**Response:**

```json
{
  "message": "Orders fetched successfully!",
  "data": [ ... ],
  "status": 200
}
```

---

### 3. Confirm Order

**Endpoint:**

```
POST /orders/confirmOrder
```

**Description:**
Update the status of an order to "CONFIRMED."

**Request Body:**

```json
{
  "id": "order-id"
}
```

**Response:**

```json
{
  "message": "Order confirmed successfully!",
  "data": { ... },
  "status": 200
}
```

---

### 4. Dispatch Order

**Endpoint:**

```
POST /orders/dispatchOrder
```

**Description:**
Update the status of an order to "DISPATCHED."

**Request Body:**

```json
{
  "id": "order-id"
}
```

**Response:**

```json
{
  "message": "Order dispatched successfully!",
  "data": { ... },
  "status": 200
}
```

---

### 5. Deliver Order

**Endpoint:**

```
POST /orders/deliverOrder
```

**Description:**
Update the status of an order to "DELIVERED."

**Request Body:**

```json
{
  "id": "order-id"
}
```

**Response:**

```json
{
  "message": "Order delivered successfully!",
  "data": { ... },
  "status": 200
}
```

---

### 6. Cancel Order

**Endpoint:**

```
POST /orders/cancelOrder
```

**Description:**
Update the status of an order to "CANCELED."

**Request Body:**

```json
{
  "id": "order-id"
}
```

**Response:**

```json
{
  "message": "Order cancelled successfully!",
  "data": { ... },
  "status": 200
}
```

---