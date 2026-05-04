# Import the collection and run tests

This guide explains how to load **Reqres-API-Portfolio** into Postman and execute manual runs or the **Collection Runner**.

---

## Prerequisites

- [Postman](https://www.postman.com/downloads/) Desktop (recommended) or Postman on the web  
- File: `postman-collection/Reqres-API-Portfolio.postman_collection.json`  

---

## Import the collection

### Option A — File import

1. Open Postman.  
2. Click **Import** (top left).  
3. Drag the file `Reqres-API-Portfolio.postman_collection.json` into the dialog, or choose **Upload Files** and select it.  
4. Confirm **Import**. You should see **Reqres.in — API Portfolio** in the sidebar.

### Option B — Raw / link

If the repository is hosted (e.g. GitHub), you can use **Import → Link** and paste the raw URL to the JSON file in that repo.

---

## Collection variables

The collection defines:

| Variable   | Initial value              | Purpose |
|------------|----------------------------|---------|
| `baseUrl`  | `https://reqres.in/api`    | Base path for all requests |
| `apiKey`   | *(empty)*                  | Sent as **`x-api-key`** header (required by Reqres) |

**Set `apiKey` before running:** create a free key at [app.reqres.in/api-keys](https://app.reqres.in/api-keys), then paste it into the collection **Variables** tab as **Current Value**. Use **Current Value** only for secrets; avoid syncing secrets to the Postman cloud if your workspace policy requires it.

To override `baseUrl` (e.g. self-hosted Reqres), edit **Current Value** (do not commit secrets).

---

## Run a single request

1. Expand **Reqres.in — API Portfolio** → **Users** (or the relevant folder).  
2. Select a request (e.g. **GET List users**).  
3. Click **Send**.  
4. Open the **Test Results** tab in the response panel to see assertion results.  

Assertions cover:

- **Status code** — expected HTTP status per operation  
- **Response time** — below a defined threshold (ms)  
- **Response body** — JSON where applicable; empty body for `204`  
- **JSON fields** — required keys and basic types  

---

## Run the full collection (Collection Runner)

1. Click the collection **Reqres.in — API Portfolio** (three dots) → **Run collection**, or use **Runner** from the left sidebar.  
2. Select the collection and choose which requests/folders to include.  
3. Set **Iterations** to `1` (default).  
4. Click **Run Reqres.in — API Portfolio**.  
5. Review the **Summary**: passed/failed tests and response times.  

**Tip:** Use **Persist responses** only if you need to inspect bodies later; it increases storage use.

---

## Export results (portfolio evidence)

- From the Runner **Summary**, use **Export Results** if available in your Postman version.  
- Alternatively, capture screenshots for your `screenshots/` folder (see main [README](../README.md#screenshots-portfolio-placeholder)).  

---

## Optional: Newman (CLI)

If you use [Newman](https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/) for CI:

```bash
npm install -g newman
newman run postman-collection/Reqres-API-Portfolio.postman_collection.json --env-var "apiKey=YOUR_KEY_HERE"
```

Pass your Reqres API key via `--env-var` (or a Newman environment file). Never commit keys to the repository.

Adjust the path if you run the command from a different working directory. Newman prints the same logical tests to the console.

---

## Troubleshooting

| Symptom | What to check |
|---------|----------------|
| `401` / `missing_api_key` / invalid key | Set collection variable **`apiKey`** to a valid key from [app.reqres.in/api-keys](https://app.reqres.in/api-keys) |
| `ENOTFOUND` / DNS | Internet connectivity; corporate proxy blocking `reqres.in` |
| Timeouts | Increase Postman request timeout; Reqres is usually fast |
| SSL errors | System clock and corporate SSL inspection |
| Tests fail on status | Reqres may have changed; verify live response in **Body** tab |

---

## Related documents

- [TEST_SCENARIOS.md](TEST_SCENARIOS.md) — scenario list  
- [API_TEST_CASES.md](API_TEST_CASES.md) — case IDs and expectations  
