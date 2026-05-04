# Postman API Testing — Reqres.in Portfolio

A structured API test portfolio demonstrating REST validation against **[Reqres](https://reqres.in)** — a hosted REST API for prototyping and learning. This repository is intended for **QA engineers** and **test automation** portfolios: clear scenarios, traceable test cases, and a runnable Postman collection with automated assertions.

---

## Project overview

| Item | Description |
|------|-------------|
| **Target API** | Reqres: `https://reqres.in` (free **API key** required — see below) |
| **Scope** | CRUD-style user endpoints (read, create, update, delete) |
| **Tooling** | Postman (collection import, Collection Runner, CLI `newman` optional) |
| **Assertions** | HTTP status, latency, JSON shape, and field-level checks |

### Authentication (required)

Reqres expects the header **`x-api-key`** on API calls. For a free key:

1. Open **[app.reqres.in/api-keys](https://app.reqres.in/api-keys)** (sign in if prompted).  
2. Create an API key.  
3. In Postman, select the collection **Reqres.in — API Portfolio** → **Variables** → set **`apiKey`** (Current Value) to your key.  

Do not commit real keys to git; keep them in Postman’s **Current Value** only.

### Repository layout

```
postman-collection/     Postman v2.1 collection (import this into Postman)
screenshots/            Portfolio evidence — see section below
docs/                   Scenarios, test cases, and import/run guide
README.md               This file
```

### What this project demonstrates

- Test design from scenarios → cases → automated scripts  
- Consistent validation patterns (status, performance budget, schema/fields)  
- Professional documentation suitable for hiring managers and peer review  

---

## Quick start

1. Install [Postman](https://www.postman.com/downloads/) (Desktop or web).  
2. Import the collection: **File → Import** → select `postman-collection/Reqres-API-Portfolio.postman_collection.json`.  
3. Open the **Reqres.in — API Portfolio** collection and run requests individually, or use **Collection Runner** for the full suite.  

Step-by-step instructions: **[docs/POSTMAN_IMPORT_AND_RUN.md](docs/POSTMAN_IMPORT_AND_RUN.md)**.

---

## Documentation index

| Document | Purpose |
|----------|---------|
| [docs/TEST_SCENARIOS.md](docs/TEST_SCENARIOS.md) | High-level test scenarios |
| [docs/API_TEST_CASES.md](docs/API_TEST_CASES.md) | Detailed API test cases per endpoint |
| [docs/POSTMAN_IMPORT_AND_RUN.md](docs/POSTMAN_IMPORT_AND_RUN.md) | Import collection, run tests, optional Newman |

---

## Screenshots (portfolio placeholder)

Add exported evidence under `screenshots/` to showcase execution and results in your portfolio or CV:

| Suggested filename | What to capture |
|--------------------|-----------------|
| `01-collection-overview.png` | Collection tree with all folders/requests visible |
| `02-runner-summary.png` | Collection Runner **Summary** with all tests passed |
| `03-request-tests-green.png` | Single request **Test Results** tab (all assertions green) |
| `04-environment-variables.png` | (Optional) Variables if you add an environment later |

**Tip:** Use consistent zoom and light/dark theme so screenshots look cohesive on a portfolio site or PDF.

> The `screenshots/` folder is intentionally empty in source control; add your own images locally or attach them in your portfolio host without committing secrets.

---

## API reference (sandbox)

Base URL used in the collection: `https://reqres.in/api`

Official docs and behavior: [https://reqres.in](https://reqres.in)

---

## License & attribution

- **Reqres** is a third-party public API; usage subject to their terms.  
- Collection and docs in this repo are provided as a portfolio/educational artifact.

---

## Author

Prepared as a **QA / API testing portfolio** sample. Replace this section with your name, links, and contact if you publish the repo publicly.
