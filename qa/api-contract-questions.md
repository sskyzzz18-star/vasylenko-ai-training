# VAI-005 — API Contract Questions

## Purpose
Document API behavior that requires confirmation before test execution.

## Open Questions

| ID | Endpoint | Question | Related Test Cases | Status |
|---|---|---|---|---|
| Q-001 | GET / | What HTTP status and response body should the root endpoint return? | TC-001 | Open |
| Q-002 | GET /api/v1/health | What HTTP status and response format should the health endpoint return? | TC-002 | Open |
| Q-003 | POST /api/v1/leads | What HTTP status and response body indicate successful lead creation? | TC-003 | Open |
| Q-004 | POST /api/v1/leads | What HTTP status and error format are expected for validation failures? | TC-004 to TC-020 | Open |
| Q-005 | POST /api/v1/leads | Are empty strings, whitespace-only values, and null values rejected? | TC-009, TC-010, TC-019, TC-020 | Open |
| Q-006 | POST /api/v1/leads | How should the API handle incorrect field types and malformed JSON? | TC-016, TC-017 | Open |

## Notes
- No backend requests have been executed.
- All questions are pending developer confirmation.
- Test execution statuses remain Not Run.
