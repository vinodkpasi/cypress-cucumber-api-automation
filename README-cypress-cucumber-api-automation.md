# Cypress Cucumber API Automation

[![Cypress](https://img.shields.io/badge/Cypress-12.14.0-17202C?logo=cypress)](https://www.cypress.io/)
[![Cucumber](https://img.shields.io/badge/Cucumber-Gherkin-23D96C?logo=cucumber)](https://cucumber.io/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Node.js-F7DF1E?logo=javascript&logoColor=black)](https://nodejs.org/)
[![License](https://img.shields.io/badge/license-ISC-lightgrey)](#license)

A **Cypress + Cucumber BDD API automation framework** built with JavaScript and designed for validating REST APIs using readable Gherkin scenarios.

**Repository:** https://github.com/vinodkpasi/cypress-cucumber-api-automation

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Application Under Test](#-application-under-test)
- [Cypress Configuration](#-cypress-configuration)
- [Cucumber Configuration](#-cucumber-configuration)
- [BDD Workflow](#-bdd-workflow)
- [API Testing with Cypress](#-api-testing-with-cypress)
- [Feature Files](#-feature-files)
- [Step Definitions](#-step-definitions)
- [Request and Response Validation](#-request-and-response-validation)
- [JSON Schema Validation](#-json-schema-validation)
- [Test Data](#-test-data)
- [Reporting](#-reporting)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Run Tests](#-run-tests)
- [Run Tests in Headless Mode](#-run-tests-in-headless-mode)
- [Run Tests by Tag](#-run-tests-by-tag)
- [Debugging](#-debugging)
- [CI/CD](#-cicd)
- [Environment Management](#-environment-management)
- [Best Practices](#-best-practices)
- [Troubleshooting](#-troubleshooting)
- [Recommended Enhancements](#-recommended-enhancements)
- [Security](#-security)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 🎯 Overview

This repository provides a **Cypress/Cucumber integration for API automation**.

The framework uses:

```text
Cypress
   +
Cucumber / Gherkin
   +
JavaScript / Node.js
   +
REST API
   +
JSON validation
   +
HTML reporting
```

The configured Cypress `baseUrl` is:

```text
https://restful-booker.herokuapp.com
```

The repository is therefore set up around API testing against the **Restful Booker** service. citeturn2view1

The project is intentionally lightweight and demonstrates how API tests can be written as business-readable BDD scenarios while using Cypress for HTTP execution and assertions.

---

# ✨ Key Features

- ✅ Cypress API automation
- ✅ Cucumber / Gherkin BDD
- ✅ JavaScript-based test implementation
- ✅ REST API testing
- ✅ Cucumber step definitions
- ✅ Automatic Cucumber JSON generation
- ✅ JSON schema validation support through `ajv`
- ✅ Cucumber HTML reporting
- ✅ Headless test execution
- ✅ Cypress test runner support
- ✅ Configurable Cucumber preprocessor
- ✅ Reusable test architecture
- ✅ Node.js/npm-based dependency management

The current project defines Cypress `12.14.0`, `cypress-cucumber-preprocessor 4.3.1`, `ajv`, `multiple-cucumber-html-reporter`, and `cypress-slow-down`. citeturn1view0

---

# 🧰 Technology Stack

| Technology | Version / Purpose |
|---|---|
| **Node.js** | JavaScript runtime |
| **npm** | Package/dependency manager |
| **Cypress** | `12.14.0` |
| **Cucumber Preprocessor** | `4.3.1` |
| **Gherkin** | BDD syntax |
| **AJV** | JSON Schema validation |
| **multiple-cucumber-html-reporter** | HTML report generation |
| **cypress-slow-down** | Optional execution-speed control |
| **JavaScript** | Automation language |

Package versions are taken from the repository's `package.json`. citeturn1view0

---

# 🏗️ Architecture

The framework follows a BDD API automation flow:

```text
                 ┌─────────────────────┐
                 │ Business Requirement│
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Gherkin Feature     │
                 │ *.feature           │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Step Definitions    │
                 │ JavaScript          │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Cypress API Layer   │
                 │ cy.request()        │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ REST API            │
                 │ Restful Booker      │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Assertions / AJV    │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Cucumber JSON       │
                 │ + HTML Report       │
                 └─────────────────────┘
```

---

# 📁 Project Structure

The repository root currently contains:

```text
cypress-cucumber-api-automation/
│
├── .vscode/
│   └── VS Code configuration
│
├── cypress/
│   ├── e2e/
│   │   ├── features/
│   │   │   └── Gherkin feature files
│   │   │
│   │   └── step_definitions/
│   │       └── Cucumber step definitions
│   │
│   ├── cucumber-json/
│   │   └── Generated Cucumber JSON results
│   │
│   └── reports/
│       └── Generated report output
│
├── cucumber-html-report.js
│   └── HTML report generation script
│
├── cypress.config.js
│   └── Cypress + Cucumber configuration
│
├── jsconfig.json
│   └── JavaScript/IDE configuration
│
├── package.json
│   └── Dependencies and npm scripts
│
├── package-lock.json
│   └── Locked dependency tree
│
├── Task.txt
│   └── Project/task notes
│
└── README.md
```

The repository explicitly configures Cucumber step definitions under:

```text
cypress/e2e/step_definitions
```

and feature files under:

```text
cypress/e2e/features/**/*.feature
```

citeturn1view0turn2view1

---

# 🌐 Application Under Test

The configured API base URL is:

```text
https://restful-booker.herokuapp.com
```

This is configured directly in `cypress.config.js`. citeturn2view1

The framework can therefore be used to automate REST endpoints exposed by the Restful Booker sample application.

Typical API automation scenarios can cover:

```text
Create booking
Retrieve booking
Update booking
Delete booking
Authentication
Response validation
Negative scenarios
Schema validation
```

---

# ⚙️ Cypress Configuration

The project uses Cypress's `defineConfig()` API.

The current configuration enables the Cucumber preprocessor through:

```javascript
setupNodeEvents(on, config) {
    on(
        "file:preprocessor",
        require("cypress-cucumber-preprocessor").default()
    );
}
```

Feature discovery is configured as:

```text
cypress/e2e/features/**/*.feature
```

and the API base URL is:

```text
https://restful-booker.herokuapp.com
```

citeturn2view1

---

# 🥒 Cucumber Configuration

The `package.json` configures the Cucumber preprocessor with:

```json
{
  "cypress-cucumber-preprocessor": {
    "stepDefinitions": "cypress/e2e/step_definitions",
    "cucumberJson": {
      "generate": true
    }
  }
}
```

This means:

```text
Feature File
     ↓
Cucumber Preprocessor
     ↓
Step Definitions
     ↓
Cypress
```

and Cucumber JSON output is generated for reporting. citeturn1view0

---

# 🔄 BDD Workflow

A typical test execution follows:

```text
1. Feature file
        ↓
2. Cucumber parser
        ↓
3. Step definition
        ↓
4. Cypress API command
        ↓
5. REST API
        ↓
6. Response
        ↓
7. Assertion / Schema validation
        ↓
8. Cucumber JSON
        ↓
9. HTML report
```

This allows API behavior to be documented in readable Gherkin while the implementation remains in JavaScript.

---

# 📄 Feature Files

Feature files should describe API behavior rather than implementation details.

Example:

```gherkin
Feature: Booking API

  Scenario: Create a booking successfully
    Given I have valid booking data
    When I send a POST request to create a booking
    Then the response status should be 200
    And the booking should be created successfully
```

A feature can contain multiple scenarios:

```gherkin
Feature: Booking API

  Scenario: Create booking
    ...

  Scenario: Retrieve booking
    ...

  Scenario: Update booking
    ...

  Scenario: Delete booking
    ...
```

---

# 🧩 Step Definitions

Step definitions implement Gherkin steps.

Example:

```javascript
Given("I have valid booking data", () => {
    // Prepare request payload
});
```

API execution can then be implemented using Cypress:

```javascript
When("I send a POST request to create a booking", () => {
    cy.request({
        method: "POST",
        url: "/booking",
        body: bookingPayload
    }).as("createBooking");
});
```

The assertion step can consume the response:

```javascript
Then("the response status should be 200", () => {
    cy.get("@createBooking")
        .its("status")
        .should("eq", 200);
});
```

---

# 🔌 API Testing with Cypress

Cypress provides `cy.request()` for API calls.

Example GET:

```javascript
cy.request("GET", "/booking");
```

Example POST:

```javascript
cy.request({
    method: "POST",
    url: "/booking",
    body: payload
});
```

Example PUT:

```javascript
cy.request({
    method: "PUT",
    url: `/booking/${bookingId}`,
    body: payload
});
```

Example DELETE:

```javascript
cy.request({
    method: "DELETE",
    url: `/booking/${bookingId}`
});
```

Using a configured `baseUrl` keeps endpoint definitions concise:

```javascript
url: "/booking"
```

instead of:

```javascript
url: "https://restful-booker.herokuapp.com/booking"
```

---

# 📦 Request Validation

Validate the complete HTTP response where appropriate.

Example:

```javascript
cy.request({
    method: "GET",
    url: `/booking/${bookingId}`
}).then((response) => {

    expect(response.status).to.eq(200);

    expect(response.body).to.have.property("firstname");
    expect(response.body).to.have.property("lastname");
});
```

Useful validations include:

```text
HTTP status
Response headers
Response body
Required fields
Field values
Data types
Business rules
Response schema
```

---

# 🧪 Response Validation

Example:

```javascript
cy.request("GET", `/booking/${bookingId}`)
    .then((response) => {

        expect(response.status).to.eq(200);

        expect(response.body.firstname)
            .to.be.a("string");

        expect(response.body.lastname)
            .to.be.a("string");
    });
```

A robust API framework should validate more than only the HTTP status.

---

# 🧬 JSON Schema Validation

The project includes:

```text
ajv
```

which is a JSON Schema validator. citeturn1view0

A schema-based validation approach can be:

```javascript
const Ajv = require("ajv");

const ajv = new Ajv();

const validate = ajv.compile(schema);

const valid = validate(response.body);

expect(valid).to.equal(true);
```

This is useful when an API contract requires validation of:

- Required fields
- Data types
- Nested objects
- Arrays
- Enumerations
- String formats
- Numeric constraints

---

# 📊 Reporting

The project uses:

```text
multiple-cucumber-html-reporter
```

The npm script is:

```json
"cypress:execute": "npx cypress run && node cucumber-html-report.js"
```

So execution follows:

```text
Cypress Test Run
       ↓
Cucumber JSON
       ↓
cucumber-html-report.js
       ↓
multiple-cucumber-html-reporter
       ↓
HTML Report
```

citeturn1view0

The report generation script uses:

```javascript
report.generate({
    jsonDir: "cypress/cucumber-json",
    reportPath: "./reports"
});
```

citeturn2view2

The resulting report can be opened from:

```text
reports/
└── index.html
```

after execution, depending on the generated reporter output.

---

# ▶️ Run Tests

## Install dependencies

From the project root:

```bash
npm install
```

The repository README documents installing Node.js and then running `npm install`. citeturn0view0

## Run the configured test command

```bash
npm run cypress:execute
```

The configured script runs:

```bash
npx cypress run
```

followed by:

```bash
node cucumber-html-report.js
```

citeturn1view0

---

# 🖥️ Open Cypress UI

For interactive development:

```bash
npx cypress open
```

Then select the relevant feature/specification from the Cypress interface.

This mode is useful for:

- Developing feature files
- Debugging step definitions
- Inspecting API calls
- Viewing command logs
- Re-running individual scenarios

---

# 🏃 Run Tests in Headless Mode

Run Cypress directly:

```bash
npx cypress run
```

The repository's `cypress:execute` script uses this mode before generating the Cucumber HTML report. citeturn1view0

For CI:

```bash
npm run cypress:execute
```

---

# 🏷️ Run Tests by Tag

Cucumber tags are useful for organizing API suites.

Example:

```gherkin
@smoke
Scenario: Create booking
```

Or:

```gherkin
@regression
Scenario: Update booking
```

Common organization:

```text
@smoke
@regression
@negative
@contract
@authentication
@booking
```

Tag filtering depends on the configured Cucumber preprocessor/version. Keep tags focused on business/test-suite intent rather than implementation details.

---

# 🔐 Authentication Testing

For APIs requiring authentication, keep credentials outside feature files.

Preferred:

```text
Environment Variables
        ↓
Cypress configuration
        ↓
API request
```

Example concept:

```javascript
cy.request({
    method: "POST",
    url: "/auth",
    body: {
        username: Cypress.env("API_USERNAME"),
        password: Cypress.env("API_PASSWORD")
    }
});
```

Avoid:

```gherkin
Given username is "real-user"
And password is "real-password"
```

---

# 🌍 Environment Management

A production-ready API framework should support:

```text
dev
qa
stage
prod
```

Example:

```text
CYPRESS_baseUrl
CYPRESS_API_USERNAME
CYPRESS_API_PASSWORD
```

Then run:

```bash
npx cypress run
```

with environment-specific variables supplied by the shell or CI platform.

For example:

```bash
CYPRESS_baseUrl=https://qa.example.com npx cypress run
```

PowerShell:

```powershell
$env:CYPRESS_baseUrl="https://qa.example.com"
npx cypress run
```

---

# 🧪 Test Data Strategy

For API automation, separate test data from step implementation.

Recommended structure:

```text
cypress/
├── e2e/
│   ├── features/
│   └── step_definitions/
│
├── fixtures/
│   ├── booking.json
│   └── users.json
│
└── schemas/
    ├── booking.schema.json
    └── auth.schema.json
```

Use fixtures for stable data and generate dynamic data when tests need uniqueness.

A scalable data strategy can support:

```text
Static fixture data
        +
Dynamic test data
        +
API-created test entities
        +
Cleanup
```

---

# 🧹 Test Isolation and Cleanup

API tests should be independent whenever possible.

Recommended lifecycle:

```text
Before Scenario
      ↓
Create required test data
      ↓
Execute API
      ↓
Validate response
      ↓
Cleanup created data
```

Avoid depending on records created by another test.

This becomes especially important when the suite is parallelized.

---

# 🔁 API Test Pyramid

A practical API automation strategy is:

```text
              ┌───────────────┐
              │   E2E / UI    │
              └───────────────┘
             ┌─────────────────┐
             │ API Integration │
             └─────────────────┘
           ┌─────────────────────┐
           │ API Contract/Schema │
           └─────────────────────┘
        ┌───────────────────────────┐
        │ Unit / Component Testing  │
        └───────────────────────────┘
```

API tests should provide fast feedback and cover business rules that do not require browser interaction.

---

# 🐞 Debugging

When an API test fails, inspect:

```text
Feature
   ↓
Step Definition
   ↓
HTTP Method
   ↓
URL
   ↓
Headers
   ↓
Request Body
   ↓
Response Status
   ↓
Response Body
   ↓
Assertion
```

Useful debugging:

```javascript
cy.request({
    method: "GET",
    url: "/booking"
}).then((response) => {

    cy.log(JSON.stringify(response.body));

    expect(response.status).to.eq(200);
});
```

For failures, inspect the Cypress command log and generated Cucumber report.

---

# 🧪 Negative API Testing

A comprehensive API suite should include negative cases such as:

```text
Invalid endpoint
Invalid method
Missing required field
Invalid data type
Invalid authentication
Invalid ID
Malformed JSON
Unauthorized access
Forbidden access
Unsupported values
Duplicate resources
```

Example:

```gherkin
Scenario: Retrieve a non-existing booking
    When I request an invalid booking ID
    Then the API should return the expected error response
```

---

# 📈 Recommended API Coverage

For each endpoint, consider validating:

| Area | Examples |
|---|---|
| HTTP method | GET / POST / PUT / DELETE |
| Status | 2xx / 4xx / 5xx |
| Headers | Content-Type, Authorization |
| Body | Required and optional fields |
| Schema | Object structure and types |
| Business rules | Domain-specific validation |
| Negative cases | Invalid inputs |
| Security | Authentication/authorization |
| Idempotency | Repeated operations |
| Data lifecycle | Create/read/update/delete |

---

# 🔄 CI/CD

A CI pipeline can execute:

```text
Checkout
   ↓
Install Node.js
   ↓
npm ci
   ↓
Run Cypress + Cucumber
   ↓
Generate Cucumber JSON
   ↓
Generate HTML report
   ↓
Publish report artifact
```

Recommended command:

```bash
npm ci
npm run cypress:execute
```

`npm ci` is preferable to `npm install` in CI because it uses the lock file for deterministic dependency installation.

---

# 🧰 GitHub Actions Example

A basic workflow can be:

```yaml
name: Cypress API Tests

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  api-tests:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm

      - name: Install dependencies
        run: npm ci

      - name: Run Cypress API tests
        run: npm run cypress:execute

      - name: Upload reports
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: cypress-cucumber-report
          path: |
            reports/
            cypress/cucumber-json/
```

Adjust the Node.js version and artifact paths to match your CI environment.

---

# 🔐 Security

Never commit:

```text
API passwords
Access tokens
JWT secrets
Private keys
Client secrets
Production credentials
```

Use:

```text
GitHub Secrets
Azure DevOps Variables
Jenkins Credentials
GitLab CI Variables
```

and access them through Cypress environment variables.

Do not put secrets directly into:

```text
.feature
.js
cypress.config.js
README.md
```

---

# 🛠️ Troubleshooting

## `npm install` fails

Try:

```bash
node --version
npm --version
```

Then:

```bash
npm cache verify
npm install
```

If dependency resolution remains inconsistent, use the committed lock file with:

```bash
npm ci
```

---

## Cypress does not start

Verify installation:

```bash
npx cypress verify
```

Then:

```bash
npx cypress open
```

or:

```bash
npx cypress run
```

---

## No feature files found

Verify:

```text
cypress/e2e/features/**/*.feature
```

matches the feature-file location configured in `cypress.config.js`. citeturn2view1

---

## Step definition not found

Verify:

```text
cypress/e2e/step_definitions
```

matches the `stepDefinitions` configuration in `package.json`. citeturn1view0

Check spelling and capitalization of the Gherkin step.

---

## Cucumber JSON is not generated

Verify the package configuration:

```json
"cucumberJson": {
    "generate": true
}
```

The current repository enables this option. citeturn1view0

---

## HTML report is not generated

Run:

```bash
npx cypress run
```

then:

```bash
node cucumber-html-report.js
```

The report generator reads:

```text
cypress/cucumber-json
```

and writes the report under:

```text
./reports
```

citeturn2view2

---

## API returns unexpected status

Check:

1. HTTP method
2. Endpoint
3. Base URL
4. Headers
5. Authentication
6. Request payload
7. API data state
8. Expected status code

---

# 🧹 Best Practices

## Gherkin

Keep scenarios:

- Business-readable
- Short
- Focused on behavior
- Independent
- Free of JavaScript implementation details

Good:

```gherkin
When I create a booking
Then the booking should be created successfully
```

Avoid:

```gherkin
When I call cy.request with method POST
Then I use a JavaScript assertion
```

---

## Step Definitions

Keep step definitions thin:

```text
Gherkin
 ↓
Step
 ↓
Reusable API helper
 ↓
Cypress request
```

Avoid duplicating API request construction across many steps.

---

## API Helpers

For larger suites, create reusable helpers for:

```text
Authentication
Headers
GET
POST
PUT
PATCH
DELETE
Schema validation
Common assertions
```

---

## Assertions

Validate:

```text
Status
Headers
Body
Schema
Business rules
```

Do not validate only the HTTP status.

---

## Test Data

Use:

```text
Fixtures
Factories
API setup
Dynamic IDs
Environment variables
```

rather than hard-coded IDs that can become stale.

---

# 📈 Recommended Enhancements

The current project is a good foundation. For a production-grade API automation framework, consider adding:

### 1. API Client Layer

Create reusable clients:

```text
BookingClient
AuthClient
UserClient
```

### 2. Request Builder

Centralize:

```text
Headers
Authentication
Base URL
Common request options
```

### 3. Schema Repository

Organize:

```text
schemas/
├── booking/
├── auth/
└── common/
```

### 4. Test Data Factory

Generate unique:

```text
Names
Emails
Booking data
IDs
Dates
```

### 5. Environment Profiles

Support:

```text
dev
qa
stage
prod
```

### 6. Authentication Utility

Centralize token acquisition and reuse.

### 7. Better Reporting

Add:

- Request/response details
- Schema validation results
- Environment information
- Duration
- Failure diagnostics

### 8. CI Matrix

Run:

```text
Environment × API Suite
```

### 9. Parallel Execution

Parallelize independent API scenarios after test isolation is guaranteed.

### 10. Contract Testing

Consider Pact or JSON Schema contract validation for service-to-service API contracts.

### 11. Performance Smoke Tests

For selected APIs, add lightweight latency/response-time checks without turning functional tests into full load tests.

---

# 🧭 Recommended Framework Architecture

For future growth:

```text
cypress/
│
├── e2e/
│   ├── features/
│   │   ├── booking.feature
│   │   └── authentication.feature
│   │
│   └── step_definitions/
│       ├── booking.steps.js
│       └── authentication.steps.js
│
├── fixtures/
│   └── booking.json
│
├── schemas/
│   └── booking.schema.json
│
├── support/
│   ├── commands.js
│   └── api/
│       ├── bookingClient.js
│       └── authClient.js
│
└── cucumber-json/
```

Execution:

```text
Feature
   ↓
Step Definition
   ↓
API Client
   ↓
Cypress cy.request()
   ↓
REST Service
   ↓
Response
   ├── Status Assertion
   ├── Body Assertion
   └── JSON Schema Assertion
   ↓
Cucumber JSON
   ↓
HTML Report
```

---

# 🧪 Example End-to-End API Scenario

### Feature

```gherkin
Feature: Booking API

  @smoke
  Scenario: Create a booking
    Given I have valid booking information
    When I send a request to create the booking
    Then the response status should be successful
    And the booking response should match the expected schema
```

### Step Definition

```javascript
When("I send a request to create the booking", () => {
    cy.request({
        method: "POST",
        url: "/booking",
        body: bookingData
    }).as("createBooking");
});
```

### Validation

```javascript
Then("the response status should be successful", () => {
    cy.get("@createBooking")
        .its("status")
        .should("eq", 200);
});
```

### Architecture

```text
Gherkin
   ↓
Cucumber Step
   ↓
Cypress
   ↓
REST API
   ↓
Response
   ↓
Assertions
   ↓
Cucumber Report
```

---

# 📦 Useful npm Commands

Install:

```bash
npm install
```

Recommended CI installation:

```bash
npm ci
```

Open Cypress:

```bash
npx cypress open
```

Run Cypress:

```bash
npx cypress run
```

Run the repository's full command:

```bash
npm run cypress:execute
```

Generate report separately:

```bash
node cucumber-html-report.js
```

---

# 🤝 Contributing

Contributions are welcome.

Before submitting changes:

1. Install dependencies.
2. Run the relevant API tests.
3. Verify feature files remain readable.
4. Avoid duplicate step definitions.
5. Add schema validation for important contracts.
6. Do not commit credentials.
7. Update this README when framework behavior changes.

Git workflow:

```bash
git checkout -b feature/add-booking-tests

git add .

git commit -m "Add booking API BDD tests"

git push origin feature/add-booking-tests
```

Then create a Pull Request.

---

# 📄 License

The repository's `package.json` currently specifies:

```text
ISC
```

If this project is intended for broad public reuse, consider adding an explicit `LICENSE` file to the repository.

---

# 👤 Author

## Vinod Kumar

**Lead SDET / QA Automation Leader**

Technical areas represented by this project include:

- Cypress
- JavaScript
- Cucumber / Gherkin
- BDD
- REST API automation
- JSON Schema validation
- API test data management
- HTML reporting
- CI/CD
- Test automation framework design

GitHub:

https://github.com/vinodkpasi

Repository:

https://github.com/vinodkpasi/cypress-cucumber-api-automation

---

# ⭐ Support

If this project is useful for learning or demonstrating Cypress + Cucumber API automation, consider giving the repository a ⭐ on GitHub.

---

## 📚 References

- Cypress — https://www.cypress.io/
- Cypress Documentation — https://docs.cypress.io/
- Cucumber — https://cucumber.io/
- Gherkin — https://cucumber.io/docs/gherkin/
- AJV — https://ajv.js.org/
- Node.js — https://nodejs.org/
