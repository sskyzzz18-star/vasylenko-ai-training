# VAI-006 — API Assertion Plan

## Purpose
Document planned automated checks without inventing API contract requirements.

## Confirmation Status
All contract-dependent assertions remain PENDING CONTRACT CONFIRMATION until approved.

| Test ID | Condition | Expected Result | Requirement Source | Confirmation Status | Automation |
|---|---|---|---|---|---|
| AP-001 | HTTP status for GET / | Matches approved expected status | API contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-002 | HTTP status for GET /api/v1/health | Matches approved expected status | API contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-003 | HTTP status for valid POST /api/v1/leads | Matches approved success status | API contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-004 | Response time | Within approved time threshold | Performance requirement, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-005 | Response Content-Type | Matches approved media type | API contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-006 | JSON response structure | Valid JSON when JSON is required | Response schema, pending | PENDING CONTRACT CONFIRMATION | Yes, conditional |
| AP-007 | Required response fields | All approved fields are present | Response schema, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-008 | Validation errors | Matches approved error status and structure | Validation contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-009 | Root health response | Matches approved root endpoint behavior | API contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |
| AP-010 | API health response | Matches approved health response behavior | API contract, pending | PENDING CONTRACT CONFIRMATION | Yes, configurable |

## Assertion Design Rules
- Expected HTTP status must be configurable.
- Response time threshold must be configurable.
- Expected Content-Type must come from confirmed requirements.
- Required fields must come from the confirmed response schema.
- JSON parsing checks apply only when JSON is expected.
- Validation error checks must not assume unknown error formats.
- Do not activate contract-dependent assertions before confirmation.

## Execution Status
NOT RUN — Backend unavailable.

## Next Step
Prepare standalone Postman JavaScript examples on Day 2.
