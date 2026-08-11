# gorest-assesment

# gorest-assesment

A API testing suite for the [GoRest API](https://gorest.co.in/) containing API collection endpoints and environment configurations for Postman and Bruno.

---

## 📌 Repository Overview

This repository contains the setup for testing user management endpoints provided by GoRest v2 API.

### Files Included
- **`gorest-1`**: Environment configuration file exported from Bruno (`bruno-environment`), containing variable definitions like `Authorization`.
- **`gorest-collection`**: Postman v2.1 collection containing API request definitions for user creation and modification.

---

## 🚀 Environment Variables

To execute requests against the GoRest API, set up the following environment variable with your personal API token obtained from [GoRest](https://gorest.co.in/)[cite: 1, 2]:

| Variable Name | Description | Type |
| :--- | :--- | :--- |
| `Authorization` | Bearer token for GoRest API authentication (`Bearer <YOUR_TOKEN>`) | Secret / Text |
| `Access-Token` | Alternative access token variable used in specific requests | Text |

---

## 📡 API Endpoints Summary

### 1. Create New User
* **Method:** `POST`
* **URL:** `https://gorest.co.in/public/v2/users`
* **Authentication:** `Bearer {{Authorization}}`
* **Headers:**
  * `Accept: application/json`
  * `Content-Type: application/json`
* **Request Body (JSON):**[cite: 1]
  ```json
  {
    "name": "Fachru Rozi 1",
    "gender": "male",
    "email": "fachrurozi1@example.com",
    "status": "active"
  }