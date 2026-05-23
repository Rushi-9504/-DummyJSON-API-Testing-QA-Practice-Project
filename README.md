# 🧪 DummyJSON API Testing — QA Practice Project

![API Testing](https://img.shields.io/badge/Type-API%20Testing-blue)
![Tool](https://img.shields.io/badge/Tool-Postman-orange)
![API](https://img.shields.io/badge/API-DummyJSON-green)
![Newman](https://img.shields.io/badge/Automation-Newman-purple)
![Sprint](https://img.shields.io/badge/Sprint-14-lightgrey)
![Test Cases](https://img.shields.io/badge/Test%20Cases-38-informational)
![Pass](https://img.shields.io/badge/Pass-34-brightgreen)
![Fail](https://img.shields.io/badge/Fail-4-red)
![Pass Rate](https://img.shields.io/badge/Pass%20Rate-89.47%25-green)

> A complete, industry-style API testing practice project executed by a Junior QA Engineer.
> Tests the real public [DummyJSON](https://dummyjson.com) REST API across 4 modules — Auth, Users, Products, and Carts.

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [API Under Test](#-api-under-test)
- [Tech Stack](#-tech-stack)
- [Folder Structure](#-folder-structure)
- [Modules Covered](#-modules-covered)
- [Test Execution Summary](#-test-execution-summary)
- [Module-wise Results](#-module-wise-results)
- [Test Cases](#-test-cases)
- [Bugs Found](#-bugs-found)
- [Newman Report Stats](#-newman-report-stats)
- [Test Credentials](#-test-credentials)
- [Environment Variables](#-environment-variables)
- [Postman Scripts Reference](#-postman-scripts-reference)
- [Author](#-author)

---

## 📌 About the Project

This project was assigned as a **Sprint 14 QA practice task** to simulate real industry-level API testing workflow.

**Assigned by:** Senior SDTE Engineer
**Executed by:** Junior QA Engineer
**Project:** DummyJSON API Testing
**Sprint:** 14

### What this project covers

- Reading and understanding API documentation
- Writing structured test cases with TC IDs, expected and actual results
- Executing REST API tests using Postman
- Validating status codes, response body, and response time
- Writing detailed bug reports with steps to reproduce
- Generating automated HTML test reports using Newman
- Version controlling QA work using Git and GitHub

---

## 🌐 API Under Test

| Property | Value |
|---|---|
| API Name | DummyJSON REST API |
| Base URL | `https://dummyjson.com` |
| Type | Public REST API — Free, no signup required |
| Auth Type | JWT Bearer Token |
| Login Endpoint | `POST /auth/login` |
| Documentation | https://dummyjson.com/docs |
| GET data | Real persistent data |
| POST / PUT / DELETE | Simulated — returns realistic response only |

> ⚠️ **Note:** POST, PUT, and DELETE operations on DummyJSON are **simulated**. They return realistic JSON responses but do not permanently modify data. This is expected behaviour for a practice API.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Postman | Manual API test execution and collection building |
| Newman | CLI-based automated test run |
| newman-reporter-htmlextra | HTML test report generation |
| Node.js v18+ | Required runtime for Newman |
| Git | Version control |
| Excel (.xlsx) | Test case documentation, bug reports, summary |

---

## 📁 Folder Structure

```
dummyjson-api-testing/
│
├── README.md
│
├── postman/
│   ├── DummyJSON_Collection.json          ← Postman collection export
│   └── DummyJSON_Environment.json         ← Postman environment export
│
├── test-cases/
│   └── DummyJSON_API_TestCases.xlsx       ← Test cases + Bug Report + Summary
│
└── reports/
    └── Newman_Report.html                 ← Newman HTML report
```

---

## 📦 Modules Covered

| Module | Endpoints Tested | Test Cases | TC IDs |
|---|---|---|---|
| Auth | 3 | 8 | TC-01 to TC-08 |
| Users | 6 | 11 | TC-09 to TC-19 |
| Products | 7 | 11 | TC-20 to TC-30 |
| Carts | 6 | 8 | TC-31 to TC-38 |
| **Total** | **22** | **38** | |

---

## ✅ Test Execution Summary

| Metric | Count |
|---|---|
| Total Test Cases | 38 |
| Executed | 38 |
| PASS | 35 |
| FAIL | 4 |
| BLOCKED | 0 |
| **Pass %** | **89.47%** |
| **Fail %** | **10.52%** |

> All test cases were executed. Zero blocked. 3 failures were identified and raised as bug reports.

---

## 📊 Module-wise Results

| Module | Total TCs | Pass | Fail |
|---|---|---|---|
| Auth | 8 | 7 | 1 |
| Users | 11 | 10 | 1 |
| Products | 11 | 10 | 1 |
| Carts | 8 | 8 | 0 |
| **TOTAL** | **38** | **34** | **3** |

> 🏆 **Carts module — 100% pass rate.** All 8 test cases passed with correct status codes and response bodies.

---

## 🧾 Test Cases

### Auth Module (TC-01 to TC-08)

| TC ID | Method | Endpoint | Scenario | Expected | Actual | Status |
|---|---|---|---|---|---|---|
| TC-01 | POST | /auth/login | Valid login — correct credentials | 200 | 200 | ✅ PASS |
| TC-02 | POST | /auth/refresh | Valid refresh token | 200 | 200 | ✅ PASS |
| TC-03 | POST | /auth/login | Wrong password | 400 | 400 | ✅ PASS |
| TC-04 | POST | /auth/login | Empty request body | 400 | 400 | ✅ PASS |
| TC-05 | POST | /auth/login | Missing username field | 400 | 400 | ✅ PASS |
| TC-06 | GET | /auth/me | Valid token — get logged in user | 200 | 200 | ✅ PASS |
| TC-07 | GET | /auth/me | No Authorization header | 401 | 200 | ❌ FAIL |
| TC-08 | GET | /auth/me | Invalid / expired token | 401 | 401 | ✅ PASS |

---

### Users Module (TC-09 to TC-19)

| TC ID | Method | Endpoint | Scenario | Expected | Actual | Status |
|---|---|---|---|---|---|---|
| TC-09 | GET | /users | Get all users — default | 200 | 200 | ✅ PASS |
| TC-10 | GET | /users?limit=5&skip=0 | Paginate — first 5 users | 200 | 200 | ✅ PASS |
| TC-11 | GET | /users?limit=5&skip=10 | Paginate — skip 10 get next 5 | 200 | 200 | ✅ PASS |
| TC-12 | GET | /users/1 | Get user by valid ID | 200 | 200 | ✅ PASS |
| TC-13 | GET | /users/9999 | Get user — non-existent ID | 404 | 404 | ✅ PASS |
| TC-14 | GET | /users/search?q=Emily | Search users by name | 200 | 200 | ✅ PASS |
| TC-15 | GET | /users/search?q=xyznotexist | Search — no matching user | 200 | 200 | ✅ PASS |
| TC-16 | POST | /users/add | Add new user — valid body | 200/201 | 200/201 | ✅ PASS |
| TC-17 | PUT | /users/1 | Update user by ID | 200 | 200 | ✅ PASS |
| TC-18 | DELETE | /users/1 | Delete user by ID | 200 | 200 | ✅ PASS |
| TC-19 | GET | /users/1 | Get deleted user by ID | 400 | 200 | ❌ FAIL |

---

### Products Module (TC-20 to TC-30)

| TC ID | Method | Endpoint | Scenario | Expected | Actual | Status |
|---|---|---|---|---|---|---|
| TC-20 | GET | /products | Get all products — default | 200 | 200 | ✅ PASS |
| TC-21 | GET | /products?limit=10&skip=0 | Paginate — 10 products | 200 | 200 | ✅ PASS |
| TC-22 | GET | /products?skip=9999 | Paginate — skip beyond total | 200 | 200 | ✅ PASS |
| TC-23 | GET | /products/1 | Get product by valid ID | 200 | 200 | ✅ PASS |
| TC-24 | GET | /products/9999 | Get product — non-existent ID | 404 | 404 | ✅ PASS |
| TC-25 | GET | /products/search?q=phone | Search product — existing keyword | 200 | 200 | ✅ PASS |
| TC-26 | GET | /products/search?q=xyzabc | Search product — no match | 200 | 200 | ✅ PASS |
| TC-27 | GET | /products/categories | Get all categories | 200 | 200 | ✅ PASS |
| TC-28 | POST | /products/add | Add new product — valid body | 200/201 | 200/201 | ✅ PASS |
| TC-29 | PUT | /products/1 | Update product price | 200 | 404 | ❌ FAIL |
| TC-30 | DELETE | /products/1 | Delete product by ID | 200 | 200 | ✅ PASS |

---

### Carts Module (TC-31 to TC-38)

| TC ID | Method | Endpoint | Scenario | Expected | Actual | Status |
|---|---|---|---|---|---|---|
| TC-31 | GET | /carts | Get all carts | 200 | 200 | ✅ PASS |
| TC-32 | GET | /carts/1 | Get cart by valid ID | 200 | 200 | ✅ PASS |
| TC-33 | GET | /carts/9999 | Get cart — non-existent ID | 404 | 404 | ✅ PASS |
| TC-34 | GET | /carts/user/5 | Get carts by user ID | 200 | 200 | ✅ PASS |
| TC-35 | POST | /carts/add | Add cart — valid body | 200 | 200 | ✅ PASS |
| TC-36 | POST | /carts/add | Add cart — missing userId | 400 | 400 | ✅ PASS |
| TC-37 | PUT | /carts/1 | Update cart — add new product | 200 | 200 | ✅ PASS |
| TC-38 | DELETE | /carts/1 | Delete cart by ID | 200 | 200 | ✅ PASS |

---

## 🐞 Bugs Found

### BUG-001 — High Priority

| Field | Details |
|---|---|
| **Bug ID** | BUG-001 |
| **Linked TC** | TC-07 |
| **Module** | Auth |
| **Severity** | High |
| **Priority** | P1 |
| **Title** | GET /auth/me returns 200 without Authorization header |
| **Endpoint** | `https://dummyjson.com/auth/me` |
| **Steps to Reproduce** | 1. Send GET /auth/me  2. Do NOT add Authorization header  3. Click Send |
| **Expected** | Status `401` — Authentication required |
| **Actual** | Status `200` — Returns user profile without any token |
| **Status** | Open |

---

### BUG-002 — Medium Priority

| Field | Details |
|---|---|
| **Bug ID** | BUG-002 |
| **Linked TC** | TC-19 |
| **Module** | Users |
| **Severity** | Medium |
| **Priority** | P2 |
| **Title** | GET /users/1 still returns data after user was deleted |
| **Endpoint** | `https://dummyjson.com/users/1` |
| **Steps to Reproduce** | 1. DELETE /users/1  2. Then GET /users/1  3. Click Send |
| **Expected** | Status `400` or `404` — User no longer exists |
| **Actual** | Status `200` — Returns full user details of deleted user |
| **Status** | Open |

---

### BUG-003 — High Priority

| Field | Details |
|---|---|
| **Bug ID** | BUG-003 |
| **Linked TC** | TC-29 |
| **Module** | Products |
| **Severity** | High |
| **Priority** | P1 |
| **Title** | PUT /products/1 returns 404 instead of updating product |
| **Endpoint** | `https://dummyjson.com/products/1` |
| **Steps to Reproduce** | 1. Send PUT /products/1  2. Body: `{"price": 1299}`  3. Click Send |
| **Expected** | Status `200` — Product updated with new price |
| **Actual** | Status `404` — Product with id '1' not found |
| **Status** | Open |

---

## 📈 Newman Report Stats

| Metric | Value |
|---|---|
| Total Requests | 38 |
| Failed Requests | 0 |
| Total Assertions | 49 |
| Failed Assertions | 5 |
| Total Run Duration | 20.2s |
| Data Received | 203.19 KB |
| Average Response Time | 449ms |

> Newman confirmed all 38 requests successfully reached the API. 5 assertion-level failures match the test cases documented as FAIL in the Excel sheet.

---

## 🔑 Test Credentials

Public dummy credentials provided by DummyJSON for practice only:

| Username | Password |
|---|---|
| `emilys` | `emilyspass` |
| `michaelw` | `michaelwpass` |
| `sophiab` | `sophiabpass` |

> 🚫 Never commit real passwords or API keys to any GitHub repository.

---

## 🌍 Environment Variables

| Variable | Value | Set By |
|---|---|---|
| `base_url` | `https://dummyjson.com` | Manual |
| `access_token` | JWT from login response | Auto — Postman test script |
| `user_id` | Logged-in user ID | Auto — Postman test script |

> ⚠️ Always fill the **Initial Value** column in Postman Web — Newman reads Initial Value, not Current Value.


## 👤 Author

**Junior QA Engineer**
Sprint 14 · DummyJSON API Testing Project
Assigned by: *** Engineer

---

## 🙏 Acknowledgements

- [DummyJSON](https://dummyjson.com) — free fake REST API for QA practice
- [Postman](https://www.postman.com) — API testing platform
- [Newman](https://github.com/postmanlabs/newman) — Postman CLI runner
- [newman-reporter-htmlextra](https://github.com/DannyDainton/newman-reporter-htmlextra) — HTML report generator

---

*This project is for educational and QA practice purposes only.*
