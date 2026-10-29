

\# VAI-006 — Postman Test Script Examples



\## Purpose



Six JavaScript examples for future automated API testing in Postman.



Status: NOT RUN.

API contract: PENDING CONTRACT CONFIRMATION.



These are documentation examples only. Do not add them to the active Postman Collection until requirements are confirmed.



\## 1. HTTP Status



Variable: expected\_status



```javascript

const rawStatus = pm.variables.get("expected\_status");



pm.test("HTTP status matches expected value", function () {

&#x20;   pm.expect(rawStatus, "Configure expected\_status").to.match(/^\\d{3}$/);

&#x20;   pm.response.to.have.status(Number(rawStatus));

});

```



\## 2. Response Time



Variable: max\_response\_time\_ms



```javascript

const rawLimit = pm.variables.get("max\_response\_time\_ms");



pm.test("Response time is within limit", function () {

&#x20;   pm.expect(rawLimit, "Configure max\_response\_time\_ms").to.match(/^\[1-9]\\d\*$/);

&#x20;   pm.expect(pm.response.responseTime).to.be.below(Number(rawLimit));

});

```



\## 3. JSON Structure



Use only when the confirmed API contract requires JSON.



```javascript

pm.test("Response contains valid JSON", function () {

&#x20;   pm.expect(function () {

&#x20;       JSON.parse(pm.response.text());

&#x20;   }).not.to.throw();

});

```



\## 4. Required Fields



Variable: required\_response\_fields



Configure as a JSON array of field names after contract confirmation.



```javascript

const rawFields = pm.variables.get("required\_response\_fields");



pm.test("Required response fields exist", function () {

&#x20;   pm.expect(rawFields, "Configure required\_response\_fields").to.be.a("string").and.not.empty;



&#x20;   const fields = JSON.parse(rawFields);

&#x20;   pm.expect(fields).to.be.an("array").that.is.not.empty;

&#x20;   pm.expect(fields.every(f => typeof f === "string" \&\& f.length > 0)).to.be.true;



&#x20;   const body = pm.response.json();

&#x20;   pm.expect(body).to.be.an("object");



&#x20;   fields.forEach(function (field) {

&#x20;       pm.expect(body).to.have.property(field);

&#x20;   });

});

```



\## 5. Validation Errors



Variables:

\- expected\_validation\_status

\- expected\_error\_fields



```javascript

const rawStatus = pm.variables.get("expected\_validation\_status");

const rawFields = pm.variables.get("expected\_error\_fields");



pm.test("Validation error matches contract", function () {

&#x20;   pm.expect(rawStatus, "Configure expected\_validation\_status").to.match(/^\\d{3}$/);

&#x20;   pm.expect(rawFields, "Configure expected\_error\_fields").to.be.a("string").and.not.empty;



&#x20;   const fields = JSON.parse(rawFields);

&#x20;   pm.expect(fields).to.be.an("array");



&#x20;   pm.response.to.have.status(Number(rawStatus));



&#x20;   if (fields.length > 0) {

&#x20;       const body = pm.response.json();

&#x20;       pm.expect(body).to.be.an("object");



&#x20;       fields.forEach(function (field) {

&#x20;           pm.expect(body).to.have.property(field);

&#x20;       });

&#x20;   }

});

```



\## 6. Health Check



Existing endpoint: GET /api/v1/health



Variable: expected\_health\_status



```javascript

const rawStatus = pm.variables.get("expected\_health\_status");



pm.test("Health endpoint returns expected status", function () {

&#x20;   pm.expect(rawStatus, "Configure expected\_health\_status").to.match(/^\\d{3}$/);

&#x20;   pm.response.to.have.status(Number(rawStatus));

});

```



\## Requirements and Safety



\- All examples use the Postman pm API.

\- Expected statuses, fields, and response-time limits require confirmation.

\- No real API keys or credentials are used.

\- No production access.

\- No actual API requests executed.

\- Examples are not enabled in the main collection.

\- Execution requires an approved QA environment and permission.



\## Execution Status



NOT RUN — QA environment unavailable.
