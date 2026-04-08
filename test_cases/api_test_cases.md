# 🧪 API Test Cases – E-Commerce Project

## 📌 Base URL

https://fakestoreapi.com

---

# 🔐 1. LOGIN API TEST CASES

## ✅ TC-01: Valid Login

* **Method:** POST
* **Endpoint:** /auth/login
* **Input:**

```json
{
  "username": "mor_2314",
  "password": "83r5^_"
}
```

* **Expected Result:**

  * Status Code: 200
  * Token is returned
  * Response time < 500ms

---

## ❌ TC-02: Invalid Password

* **Input:**

```json
{
  "username": "mor_2314",
  "password": "wrong_pass"
}
```

* **Expected Result:**

  * Status Code: 401
  * Error message displayed

---

## ❌ TC-03: Missing Password

* **Input:**

```json
{
  "username": "mor_2314"
}
```

* **Expected Result:**

  * Status Code: 400

---

## ⚠ TC-04: Empty Fields

* **Input:**

```json
{
  "username": "",
  "password": ""
}
```

* **Expected Result:**

  * Status Code: 400 or validation error

---

## ⚠ TC-05: SQL Injection Attempt

* **Input:**

```json
{
  "username": "' OR 1=1 --",
  "password": "test"
}
```

* **Expected Result:**

  * Login should fail
  * Status Code: 401

---

# 📦 2. GET PRODUCTS API TEST CASES

## ✅ TC-06: Get All Products

* **Method:** GET
* **Endpoint:** /products
* **Expected Result:**

  * Status Code: 200
  * Response is array
  * Products count > 0

---

## ❌ TC-07: Invalid Endpoint

* **Endpoint:** /productssss
* **Expected Result:**

  * Status Code: 404

---

## ⚠ TC-08: Slow Response Check

* **Expected Result:**

  * Response time < 500ms

---

## ⚠ TC-09: Validate Product Fields

* **Expected Result:**

  * Each product contains:

    * id
    * title
    * price
    * category

---

# 🛒 3. CREATE CART API TEST CASES

## ✅ TC-10: Create Cart Successfully

* **Method:** POST
* **Endpoint:** /carts
* **Input:**

```json
{
  "userId": 1,
  "date": "2026-04-08",
  "products": [
    { "productId": 1, "quantity": 2 }
  ]
}
```

* **Expected Result:**

  * Status Code: 200 or 201
  * Cart created successfully

---

## ❌ TC-11: Missing userId

* **Input:**

```json
{
  "date": "2026-04-08"
}
```

* **Expected Result:**

  * Status Code: 400

---

## ⚠ TC-12: Invalid productId

* **Input:**

```json
{
  "userId": 1,
  "products": [
    { "productId": 9999, "quantity": 1 }
  ]
}
```

* **Expected Result:**

  * Error or rejection

---

## ⚠ TC-13: Negative Quantity

* **Input:**

```json
{
  "userId": 1,
  "products": [
    { "productId": 1, "quantity": -5 }
  ]
}
```

* **Expected Result:**

  * Validation error

---

# ✏️ 4. UPDATE CART API TEST CASES

## ✅ TC-14: Update Cart Successfully

* **Method:** PUT
* **Endpoint:** /carts/7
* **Expected Result:**

  * Status Code: 200
  * Cart updated

---

## ❌ TC-15: Invalid Cart ID

* **Endpoint:** /carts/9999
* **Expected Result:**

  * Status Code: 404

---

## ⚠ TC-16: Empty Body

* **Expected Result:**

  * Status Code: 400

---

# ❌ 5. DELETE CART API TEST CASES

## ✅ TC-17: Delete Cart Successfully

* **Method:** DELETE
* **Endpoint:** /carts/7
* **Expected Result:**

  * Status Code: 200
  * Cart deleted

---

## ❌ TC-18: Delete Non-Existing Cart

* **Endpoint:** /carts/9999
* **Expected Result:**

  * Status Code: 404

---

# 🔐 6. AUTHORIZATION TEST CASES

## ❌ TC-19: Access Without Token

* **Action:** Call protected API without token
* **Expected Result:**

  * Status Code: 401 Unauthorized

---

## ❌ TC-20: Invalid Token

* **Expected Result:**

  * Status Code: 401

---

# ⚠ EDGE CASES SUMMARY

* Empty fields
* Null values
* Long strings (1000+ chars)
* SQL Injection
* Invalid IDs
* Negative numbers

---

# ✅ COVERAGE SUMMARY

✔ Positive Testing
✔ Negative Testing
✔ Edge Cases
✔ CRUD Operations
✔ Authentication
✔ Response Validation
✔ Error Handling

---
