# VAI-005 — API Test Matrix

## Scope
Endpoints:
- GET /
- GET /api/v1/health
- POST /api/v1/leads

## Test Cases

| ID | Endpoint | Scenario | Preconditions | Test Data | Expected Result | Priority | Execution Status | Contract Status |
|---|---|---|---|---|---|---|---|---|
| TC-001 | GET / | Root health check | Backend running | No body | Endpoint responds; exact status and response format require confirmation | High | Not Run | Needs Confirmation |
| TC-002 | GET /api/v1/health | API health check | Backend running | No body | Health endpoint responds; exact status and response format require confirmation | High | Not Run | Needs Confirmation |
| TC-003 | POST /api/v1/leads | Create a valid lead | Backend running | valid-lead.json | Valid request is accepted; exact HTTP status and response body require confirmation | Critical | Not Run | Needs Confirmation |
| TC-004 | POST /api/v1/leads | Missing name | Backend running | missing-name.json | Request should be rejected because name is required; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-005 | POST /api/v1/leads | Missing company | Backend running | missing-company.json | Request should be rejected because company is required; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-006 | POST /api/v1/leads | Missing task | Backend running | missing-task.json | Request should be rejected because task is required; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-007 | POST /api/v1/leads | Missing contactMethod | Backend running | missing-contact-method.json | Request should be rejected because contactMethod is required; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-008 | POST /api/v1/leads | Missing contact | Backend running | missing-contact.json | Request should be rejected because contact is required; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-009 | POST /api/v1/leads | Empty name | Backend running | empty-name.json | Verify whether empty name is rejected; exact response requires confirmation | High | Not Run | Needs Confirmation |
| TC-010 | POST /api/v1/leads | Empty company | Backend running | empty-company.json | Verify whether empty company is rejected; exact response requires confirmation | High | Not Run | Needs Confirmation |
| TC-011 | POST /api/v1/leads | Name exceeds 100 characters | Backend running | name-too-long.json | Request should be rejected because name exceeds maximum length; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-012 | POST /api/v1/leads | Company exceeds 150 characters | Backend running | company-too-long.json | Request should be rejected because company exceeds maximum length; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-013 | POST /api/v1/leads | Task exceeds 2000 characters | Backend running | task-too-long.json | Request should be rejected because task exceeds maximum length; exact status requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-014 | POST /api/v1/leads | contactMethod exceeds 50 characters | Backend running | Inline test data: contactMethod with 51 characters | Verify rejection of value exceeding maximum length; exact response requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-015 | POST /api/v1/leads | Contact exceeds 255 characters | Backend running | Inline test data: contact with 256 characters | Verify rejection of value exceeding maximum length; exact response requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-016 | POST /api/v1/leads | Wrong field type | Backend running | wrong-field-type.json | Verify handling of numeric name instead of string; exact response requires confirmation | High | Not Run | Needs Confirmation |
| TC-017 | POST /api/v1/leads | Invalid JSON syntax | Backend running | invalid-json.json | Verify that malformed JSON is rejected; exact HTTP status requires confirmation | High | Not Run | Needs Confirmation |
| TC-018 | POST /api/v1/leads | Empty JSON object | Backend running | empty-object.json | Request should be rejected because required fields are missing; exact response requires confirmation | High | Not Run | Contract Confirmed; Response TBD |
| TC-019 | POST /api/v1/leads | Null name | Backend running | null-name.json | Verify handling of null in required name field; exact response requires confirmation | High | Not Run | Needs Confirmation |
| TC-020 | POST /api/v1/leads | Whitespace-only name | Backend running | whitespace-name.json | Verify whether whitespace-only name is rejected; exact response requires confirmation | Medium | Not Run | Needs Confirmation |
