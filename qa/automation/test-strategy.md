# VAI-006 — API Automation Test Strategy

## 1. Automation Objectives
Prepare reusable automated API checks for future execution in an approved QA environment.
Reduce repetitive manual verification and support regression testing.

## 2. API Methods in Scope
- GET / — root endpoint
- GET /api/v1/health — health endpoint
- POST /api/v1/leads — lead submission

No additional endpoints are assumed.

## 3. Automation Candidates
- HTTP status verification
- Response time measurement
- Response Content-Type verification
- JSON syntax and structure validation
- Required response fields
- Missing required request fields
- Empty request values
- Incorrect field types
- Boundary value tests
- Invalid JSON handling
- Health endpoint responses
- Duplicate lead behavior after contract confirmation

Assertions that depend on unknown requirements must remain configurable or disabled until confirmed.

## 4. Manual Checks
- Reviewing ambiguous business requirements
- Confirming expected duplicate handling
- Investigating unexpected responses
- Reviewing unclear validation messages
- Exploratory testing
- Reviewing defects and evidence

## 5. Error Handling
- Compare actual responses with confirmed requirements.
- Record unexpected results in a Bug Report.
- Distinguish test-script failures from API defects.
- Mark blocked tests as BLOCKED.
- Do not invent expected status codes or error schemas.

## 6. Test Results
Future execution results will be documented using:
- Test Execution Report
- Bug Report Template
- QA Summary Template
- Postman test results

Current execution status: NOT RUN.

## 7. Dependencies
Before executing tests, confirm:
- Approved isolated QA environment
- Backend version
- API contract
- Allowed QA base URL
- Authorization requirements, if applicable
- Expected status codes and response schemas
- Response time thresholds
- Permission to execute tests

## 8. Safety
No production testing, real credentials, private Backend access, or actual API requests during preparation.

## 9. Related Work
Based on the VAI-005 API Test Matrix, JSON fixtures, Postman Collection, and regression checklist.
