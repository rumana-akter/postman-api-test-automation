# Test scenarios — Reqres.in user API

High-level scenarios traceable to detailed cases in [API_TEST_CASES.md](API_TEST_CASES.md). Each scenario assumes the public Reqres service is available (`https://reqres.in`).

---

## Scenario catalog

| ID | Scenario | Business / QA intent |
|----|----------|----------------------|
| **TS-01** | List users with pagination | Verify paginated list returns consistent metadata and user records |
| **TS-02** | Retrieve a single user by ID | Verify known user ID returns expected profile fields |
| **TS-03** | Create a user | Verify create accepts payload and returns identifiers + timestamp |
| **TS-04** | Full update (PUT) | Verify replace semantics return merged representation |
| **TS-05** | Partial update (PATCH) | Verify partial update returns updated fields |
| **TS-06** | Delete user | Verify delete succeeds with no-content response |

---

## Preconditions (global)

| Precondition | Notes |
|--------------|--------|
| Network | Client can reach `https://reqres.in` over HTTPS |
| Data | Reqres uses fixed demo data; IDs such as `2` are stable for read/update/delete examples |
| Tool | Postman collection imported; variables `baseUrl` and **`apiKey`** (Reqres `x-api-key`) configured |

---

## Traceability

| Scenario | Postman folder | Primary requests |
|----------|----------------|------------------|
| TS-01 | Users — List | `GET List users` |
| TS-02 | Users — Single | `GET Single user` |
| TS-03 | Users — Create | `POST Create user` |
| TS-04 | Users — Update | `PUT Update user` |
| TS-05 | Users — Update | `PATCH Partial update user` |
| TS-06 | Users — Delete | `DELETE User` |

---

## Out of scope (for this portfolio)

- Authentication / authorization (Reqres list/create flows used here do not require tokens)  
- Rate-limit and abuse testing  
- Contract testing against a private OpenAPI file (could be a follow-up)  
