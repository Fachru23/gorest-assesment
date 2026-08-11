# gorest-assesment

A step-by-step API testing guide and collection for the [GoRest API](https://gorest.co.in/) using Postman and Bruno API client.

---

## 📌 Repository Overview

This repository contains API requests and environment configurations for testing user management endpoints provided by GoRest v2 API.

### Included Files
- **`gorest-1.json`**: Environment configuration file exported from Bruno (`bruno-environment`).
- **`gorest-collection-2.json`**: Postman v2.1 collection containing API endpoints (`create-new-users` and `edit-new-users`).

---

## 🔑 Prerequisites & Account Setup

1. Go to [https://gorest.co.in/](https://gorest.co.in/) and sign in with your account (via Google, GitHub, Microsoft, etc.).
2. Navigate to your profile/dashboard to generate your personal **Bearer Access Token**.
3. Copy your token for use in the setup steps below.

---

## 🚀 Step-by-Step Setup Guide

Follow the steps below depending on the API Client you prefer (Postman or Bruno).

---

### Option A: Setup via Postman

#### Step 1: Import the Environment
1. Open **Postman**.
2. Click on the **Environments** tab on the left sidebar.
3. Click the **Import** button at the top left.
4. Select the file **`gorest-1.json`** from this repository to import it.
5. Set your environment variables:
   - Variable Name: `Authorization`
   - Value: `Bearer YOUR_ACCESS_TOKEN` (replace with your real token from GoRest)
   - Variable Name: `Access-Token`
   - Value: `YOUR_ACCESS_TOKEN`
6. Save the environment and set it as active in the top-right environment dropdown selector.

#### Step 2: Import the Collection
1. Click on the **Collections** tab on the left sidebar.
2. Click the **Import** button.
3. Select and import **`gorest-collection-2.json`**.
4. The collection named `gorest-collection-1` will now appear in your list.

#### Step 3: Run the API Endpoints

##### 1. Create New User (`POST /public/v2/users`)
1. Open `create-new-users` from the imported collection.
2. Ensure the Headers/Auth are using the imported `{{Authorization}}` variable.
3. Review or modify the JSON request body:
   ```json
   {
     "name": "Fachru Rozi 1",
     "gender": "male",
     "email": "fachrurozi1@example.com",
     "status": "active"
   }
   ```
4. Click **Send**.
5. Copy the returned user `id` from the response body.

##### 2. Edit User Details (`PUT /public/v2/users/{user_id}`)
1. Open `edit-new-users` from the imported collection.
2. Append the copied `id` to the end of the URL path:
   `https://gorest.co.in/public/v2/users/{user_id}`
3. Check the JSON request body:
   ```json
   {
     "name": "Updated Name",
     "status": "inactive"
   }
   ```
4. Click **Send** to update user details.

---

### Option B: Setup via Bruno API Client

#### Step 1: Import the Environment
1. Open **Bruno**.
2. Create or open a Collection/Workspace.
3. Navigate to **Environment Manager** (click the environment dropdown at the top right -> **Configure**).
4. Click **Import Environment** and select **`gorest-1.json`**.
5. Set the `Authorization` secret variable with your Bearer Token:
   - Key: `Authorization`
   - Value: `Bearer YOUR_ACCESS_TOKEN`
6. Click **Save** and select `gorest-1` as your active environment.

#### Step 2: Import the Collection
1. In Bruno, click **Import Collection** from the main screen or menu.
2. Select **Postman Collection** format and upload **`gorest-collection-2.json`**.
3. Confirm the import into your Bruno workspace.

#### Step 3: Run the API Requests
1. Execute `create-new-users` (`POST`) first to register a new user.
2. Take note of the `id` generated in the response.
3. Open `edit-new-users` (`PUT`), append the `id` to the endpoint URL, and send the request.

---

## 📝 Important Notes
- **Unique Email Constraint**: GoRest requires unique email addresses. If you receive a `422 Unprocessable Entity` error during `create-new-users`, update the `email` field in the body to a new value.
- **Bearer Token Format**: Ensure the `Authorization` variable is formatted correctly (`Bearer <token>`).
