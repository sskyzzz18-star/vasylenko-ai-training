# VAI-005 — API Regression Checklist

## General Information
- Project: Vasylenko AI
- Environment: Not available
- Execution Status: Not Run
- Backend: Not started

## 1. Health Checks
- [ ] GET / — verify root endpoint
- [ ] GET /api/v1/health — verify API health endpoint

## 2. Lead Creation
- [ ] POST /api/v1/leads — valid lead
- [ ] Verify all five required fields
- [ ] Verify successful response against confirmed API contract

## 3. Required Fields
- [ ] Missing name
- [ ] Missing company
- [ ] Missing task
- [ ] Missing contactMethod
- [ ] Missing contact

## 4. Input Validation
- [ ] Empty name and company
- [ ] Name longer than 100 characters
- [ ] Company longer than 150 characters
- [ ] Task longer than 2000 characters
- [ ] contactMethod longer than 50 characters
- [ ] Contact longer than 255 characters
- [ ] Wrong field type
- [ ] Null name
- [ ] Whitespace-only name

## 5. JSON Validation
- [ ] Invalid JSON syntax
- [ ] Empty JSON object
- [ ] Content-Type: application/json

## 6. QA Documentation
- [ ] Verify JSON fixtures
- [ ] Verify Postman request URLs and methods
- [ ] Verify Postman collection structure
- [ ] Record actual results after execution
- [ ] Document confirmed defects

## Notes
- All checkboxes are intentionally unchecked.
- No real API requests have been executed.
- Exact response statuses require contract confirmation.
- Do not mark checks complete without evidence.
