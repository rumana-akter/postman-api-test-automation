# API test cases — Reqres.in

Detailed cases aligned with the Postman collection in `postman-collection/`. **Expected** values follow observed Reqres behavior; adjust if the service changes.

**Base URL:** `https://reqres.in/api`  
**Collection variables:** `baseUrl` = `https://reqres.in/api`; **`apiKey`** = your Reqres API key (header `x-api-key`). Obtain a free key at [app.reqres.in/api-keys](https://app.reqres.in/api-keys).

> If Reqres changes response shapes for your project/collection, adjust expected fields in the Postman **Tests** tab and update this document.

---

## 1. GET — List users

| Field | Value |
|-------|--------|
| **Endpoint** | `GET /users` |
| **Example** | `GET {{baseUrl}}/users?page=1` |
| **Purpose** | Return a page of users plus pagination metadata |

### Test cases

| TC-ID | Description | Expected |
|-------|-------------|----------|
| GET-LIST-01 | Valid page query | HTTP `200` |
| GET-LIST-02 | Response is JSON | `Content-Type` includes `application/json`; body parses as JSON |
| GET-LIST-03 | Pagination fields present | Body contains `page`, `per_page`, `total`, `total_pages`, `data` |
| GET-LIST-04 | User objects shape | Each item in `data` has at least `id`, `email`, `first_name`, `last_name`, `avatar` |
| GET-LIST-05 | Performance | Response time within agreed budget (e.g. &lt; 3000 ms) |

---

## 2. GET — Single user

| Field | Value |
|-------|--------|
| **Endpoint** | `GET /users/:id` |
| **Example** | `GET {{baseUrl}}/users/2` |
| **Purpose** | Return one user wrapped in `data` |

### Test cases

| TC-ID | Description | Expected |
|-------|-------------|----------|
| GET-ONE-01 | Existing user | HTTP `200` |
| GET-ONE-02 | Wrapper object | Root has `data` object |
| GET-ONE-03 | Identity fields | `data.id`, `data.email`, `data.first_name`, `data.last_name`, `data.avatar` present and typed correctly |
| GET-ONE-04 | Performance | Response time within budget |

---

## 3. POST — Create user

| Field | Value |
|-------|--------|
| **Endpoint** | `POST /users` |
| **Body (example)** | `{ "name": "morpheus", "job": "leader" }` |
| **Purpose** | Simulate user creation; Reqres returns dummy `id` and `createdAt` |

### Test cases

| TC-ID | Description | Expected |
|-------|-------------|----------|
| POST-01 | Success path | HTTP `201` |
| POST-02 | Echo / synthetic fields | Response includes `name`, `job`, `id`, `createdAt` (or `createdAt` as returned by API) |
| POST-03 | Types | `id` is string or number per API; timestamps are non-empty strings |
| POST-04 | Performance | Response time within budget |

---

## 4. PUT — Update user (full)

| Field | Value |
|-------|--------|
| **Endpoint** | `PUT /users/:id` |
| **Example** | `PUT {{baseUrl}}/users/2` |
| **Body (example)** | `{ "name": "morpheus", "job": "zion resident" }` |

### Test cases

| TC-ID | Description | Expected |
|-------|-------------|----------|
| PUT-01 | Success | HTTP `200` |
| PUT-02 | Updated payload echoed | `name`, `job`, `updatedAt` present |
| PUT-03 | Performance | Response time within budget |

---

## 5. PATCH — Partial update user

| Field | Value |
|-------|--------|
| **Endpoint** | `PATCH /users/:id` |
| **Example** | `PATCH {{baseUrl}}/users/2` |
| **Body (example)** | `{ "name": "morpheus", "job": "messiah" }` |

### Test cases

| TC-ID | Description | Expected |
|-------|-------------|----------|
| PATCH-01 | Success | HTTP `200` |
| PATCH-02 | Updated fields | `name`, `job`, `updatedAt` present |
| PATCH-03 | Performance | Response time within budget |

---

## 6. DELETE — User

| Field | Value |
|-------|--------|
| **Endpoint** | `DELETE /users/:id` |
| **Example** | `DELETE {{baseUrl}}/users/2` |
| **Purpose** | Simulate deletion |

### Test cases

| TC-ID | Description | Expected |
|-------|-------------|----------|
| DEL-01 | Success | HTTP `204` |
| DEL-02 | Empty body | No JSON body (or empty body) suitable for non-JSON assertions |
| DEL-03 | Performance | Response time within budget |

---

## Automation mapping

Automated checks in the Postman collection implement the **status**, **response time**, **JSON/body**, and **field** validations referenced above. See request **Tests** tabs after import.
