\# VAI-006 — Regression Test Plan



\## 1. Purpose



Define a repeatable regression testing process for Vasylenko AI Backend after changes to API code, validation rules, or configuration.



Status: PREPARED — NOT EXECUTED.



\## 2. Scope



\*\*In scope:\*\*

\- GET `/`

\- GET `/api/v1/health`

\- POST `/api/v1/leads`

\- Required-field validation

\- Input length validation

\- Invalid JSON and invalid data types

\- Response status and structure after API contract confirmation



\*\*Out of scope:\*\*

\- Production testing

\- Load and performance testing

\- Security penetration testing

\- Telegram integration execution without an approved environment



\## 3. Test Levels



\### Smoke Testing



Run first to determine whether the Backend is ready for further testing.



1\. Verify that the Backend starts successfully.

2\. Verify GET `/`.

3\. Verify GET `/api/v1/health`.

4\. Verify a valid lead submission after the API contract is confirmed.



\### Regression Testing



Run after a successful smoke test.



1\. Execute the API test matrix.

2\. Verify missing required fields.

3\. Verify empty and whitespace-only values.

4\. Verify maximum-length boundaries.

5\. Verify incorrect data types.

6\. Verify malformed JSON.

7\. Compare actual responses with the confirmed API contract.

8\. Record all observed failures.



\## 4. Test Data



Source: `qa/test-data/`



Use the prepared JSON fixtures, including:



\- `valid-lead.json`

\- `missing-name.json`

\- `missing-company.json`

\- `missing-task.json`

\- `missing-contact-method.json`

\- `missing-contact.json`

\- `empty-name.json`

\- `empty-company.json`

\- `name-too-long.json`

\- `company-too-long.json`

\- `task-too-long.json`

\- `contact-method-too-long.json`

\- `contact-too-long.json`

\- `wrong-field-type.json`

\- `empty-object.json`

\- `null-name.json`

\- `whitespace-name.json`

\- `empty-contact.json`

\- `invalid-json.json`



Note: `invalid-json.json` is intentionally malformed.



\## 5. Entry Criteria



Testing may begin only when:



\- An isolated QA environment is available.

\- Permission to execute API requests is granted.

\- The Backend version is identified.

\- The API contract is confirmed.

\- Required Postman environment variables are configured.

\- Test data and collection files are reviewed.



\## 6. Exit Criteria



Regression testing is complete when:



\- All planned applicable tests have been executed.

\- Actual results have been documented.

\- Failed tests have been investigated.

\- Defects have been recorded.

\- Blocked tests have explanations.

\- A test execution report has been prepared.



\## 7. Test Execution Order



| Priority | Test group | Purpose |

|---|---|---|

| P0 | Health Checks | Verify basic Backend availability |

| P0 | Valid Lead | Verify primary API workflow |

| P1 | Required Fields | Detect missing-field validation defects |

| P1 | Input Validation | Detect boundary and type validation defects |

| P1 | JSON Validation | Detect malformed payload handling defects |

| P2 | Response Structure | Confirm response fields and error format |



\## 8. Defect Management



For every confirmed defect:



1\. Record the Backend version and QA environment.

2\. Record the affected endpoint.

3\. Describe the reproduction steps.

4\. Include expected and actual results.

5\. Attach relevant evidence.

6\. Assign severity based on impact.

7\. Retest after a fix.

8\. Include the result in the execution report.



Use `qa/templates/bug-report-template.md`.



\## 9. Reporting



Use the following documents:



\- `qa/test-cases/api-test-matrix.md`

\- `qa/checklists/api-regression-checklist.md`

\- `qa/templates/test-execution-report.md`

\- `qa/api-contract-questions.md`



Test statuses: NOT RUN, PASS, FAIL, BLOCKED.



Do not mark a test PASS without actual execution evidence.



\## 10. Current Status



Regression plan: PREPARED.



Backend execution: NOT RUN.



API contract: PENDING CONTRACT CONFIRMATION.



No production requests have been made.



The plan is ready for review and future execution after the necessary approvals.

