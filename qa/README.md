\# VASYLENKO AI — VAI-005 Postman QA Preparation



\## Objective

Prepare Postman requests and test data for the Vasylenko AI Backend.



\## API Endpoints

\- GET /

\- GET /api/v1/health

\- POST /api/v1/leads



Base URL is configured using {{base\_url}}.



\## Lead Fields

\- name: required, non-empty, maximum 100 characters

\- company: required, non-empty, maximum 150 characters

\- task: required, non-empty, maximum 2000 characters

\- contactMethod: required, non-empty, maximum 50 characters

\- contact: required, non-empty, maximum 255 characters



The API does not currently enforce a fixed list of contactMethod values.



\## Test Preparation

\- Health checks

\- Valid lead creation

\- Duplicate lead submission

\- Missing name

\- Empty contact

\- Missing task

\- Name exceeding 100 characters

\- Invalid JSON



Test data files are located in test-data/.

The exported Postman collection is located in postman/.



\## Telegram Onboarding

Endpoint: POST /api/v1/leads/{id}/telegram/onboarding?event\_id=...



Requires service authorization and a valid event belonging to the organization.

No real requests or fabricated credentials are used.



\## Execution Status

Actual: NOT EXECUTED

Status: READY FOR QA / REQUIRES CONTRACT



Backend is not available for testing. No actual HTTP responses have been verified.



\## Security

\- No production testing

\- No real credentials or API tokens

\- No fabricated test results



\## Limitations

Requests must be reviewed against the confirmed API contract before execution.

Business outcomes and HTTP status codes will be verified in an isolated QA environment.



\## Git Branch

feature/VAI-005-postman-qa





\## Expected HTTP Statuses



These are expected outcomes for QA preparation, not verified API responses.



\- GET / — expected 200 OK

\- GET /api/v1/health — expected 200 OK

\- POST /api/v1/leads (valid lead) — expected 2xx success; exact code requires API contract confirmation

\- POST /api/v1/leads (missing name) — expected validation error (400 or 422, pending confirmation)

\- POST /api/v1/leads (missing task) — expected validation error (400 or 422, pending confirmation)

\- POST /api/v1/leads (empty contact) — expected validation error (400 or 422, pending confirmation)

\- POST /api/v1/leads (name over 100 characters) — expected validation error (400 or 422, pending confirmation)

\- POST /api/v1/leads (invalid JSON) — expected client error (400 or 422, pending confirmation)

\- Duplicate lead — expected behavior requires API contract confirmation



\## Validation Results



\- JSON fixtures: 19 total (18 valid JSON files and 1 intentionally invalid JSON file).

\- Invalid JSON fixture: intentionally malformed.

\- Name length: 110 characters confirmed.

\- Postman collection: prepared for QA review.

\- Actual HTTP requests: NOT EXECUTED.

\- Actual response statuses and fields: NOT VERIFIED.

\- Backend access: NOT AVAILABLE.



Final execution and response assertions require an approved QA environment and confirmed API contract.




## Final QA Package

### Test Coverage
- 20 API test cases documented in test-cases/api-test-matrix.md.
- API contract questions documented in api-contract-questions.md.
- Positive and negative test scenarios prepared.
- Test execution status: NOT RUN.

### QA Documentation
- templates/bug-report-template.md
- templates/test-execution-report.md
- checklists/api-regression-checklist.md

### Verification
- Test fixture references checked.
- Postman collection prepared and reviewed.
- Actual API responses have NOT been verified.
- Backend execution requires an approved QA environment.



## Final QA Inventory

- API test cases: 20.
- JSON fixtures: 19 total (18 valid, 1 intentionally invalid).
- Postman requests: 21 total.
- Postman folders: Leads 2, Health Checks 2, Negative Tests 17, Telegram Onboarding 0.
- TC-014 and TC-015: separate JSON fixtures and Postman requests prepared.
- API execution: NOT RUN.
- Unconfirmed API responses: PENDING CONTRACT CONFIRMATION.

