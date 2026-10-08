# VAI-003 — End-to-End QA Regression Pack v1

**Task date:** 2026-10-07  
**Author:** Siuzanna Yehorova  
**Execution environment:** Not provided  
**Execution status:** Not executed; planning artifact only

## 1. Business Flow Understanding

Website → Lead → Vasylenko AI Core / Database → Telegram onboarding / deep link → Telegram user binds to correct Lead → AI consultation → n8n performs needed action → result/history saved.

### Original Answer (user's own responses, minimally transcribed)

| Stage | What happens | What could go wrong |
|---|---|---|
| Website → Lead | «Человек заполняет запрос». | «Если не заполнено поле, не будет работать». |
| Lead → Core / Database | «Обрабатывает». | «Не принять, если будет не заполнено что-то». |
| Telegram onboarding / deep link | «Вот этот Telegram-пользователь — тот самый человек, который оставил конкретную заявку на сайте» (user repeated the explanation). | «Неправильная ссылка». |
| Telegram user binds to correct Lead | «Клиент перешёл по правильной ссылке и всё норм, наверно». | «Не свяжется с Lead». |
| AI consultation | The assistant explained that the client talks with AI; user did not give a separate original explanation. | «Неправильный ответ ИИ». |
| n8n performs needed action | The assistant explained the stage; user did not give a separate original explanation. | «Выполнит неправильное действие или не выполнит действие» (selected from assistant suggestions). |
| Result / history saved | The assistant explained the stage; user did not give a separate original explanation. | «Не сохранится, наверное». |

**Original choice of most dangerous stages:** «Лид, Телеграм, n8n».

### AI Feedback (separate from original responses)

- Website lead submission can fail, or submitted data may be transmitted incorrectly; a missing field is not the only risk.
- Core/Database must process and retain lead information correctly; a lead might be accepted without being saved correctly.
- Telegram onboarding should validate the link/token and initiate the correct lead association. A wrong link or token can prevent onboarding or introduce misbinding risk.
- Identity binding must associate the Telegram user with the correct Lead. Binding to someone else's Lead can expose data and compromise later actions.
- AI consultation should respond relevantly, interpret requests accurately, and preserve appropriate context.
- n8n should carry out the intended action, not a different action, and handle failures safely.
- Results and history must remain available and correctly associated for subsequent interactions.
- Particularly high-risk areas include Lead creation, Telegram identity binding, and critical n8n actions.

## 2. Regression Test Matrix

**Execution note:** No backend, live API, Telegram integration, or n8n execution environment was supplied for this task. All cases below have **ACTUAL RESULT: NOT EXECUTED**. No HTTP codes, endpoints, storage implementation, or system outcomes are asserted. Exact technical behaviors require product/API contract confirmation.

### A-01 — Correct Website Lead
- **TEST ID:** A-01
- **COMPONENT:** Lead Creation
- **SCENARIO:** Submit a correctly completed website lead form.
- **PRECONDITIONS:** Test website lead form is available; test environment is authorized.
- **TEST DATA:** Synthetic name `Disha`; synthetic contact placeholder `test-contact-001` (replace with an approved test value); task `5 doors`; any additional required fields to be supplied according to the contract.
- **STEPS:** 1. Open test lead form. 2. Fill required fields with approved synthetic data. 3. Submit once. 4. Inspect the business outcome using an approved test interface.
- **EXPECTED BUSINESS RESULT:** A valid Lead is accepted and can proceed through the customer journey.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** READY FOR TEST
- **PRIORITY:** P0

### A-02 — Lead Without Contact
- **TEST ID:** A-02
- **COMPONENT:** Lead Creation
- **SCENARIO:** Submit a lead with empty contact information.
- **PRECONDITIONS:** Test lead form is available; mandatory-field rules must be confirmed.
- **TEST DATA:** Synthetic name `Disha`; contact empty; task `5 doors`; other required fields valid.
- **STEPS:** 1. Open test form. 2. Fill valid fields but leave contact empty. 3. Submit. 4. Inspect response and lead outcome.
- **EXPECTED BUSINESS RESULT:** An unusable lead should not silently enter normal processing; user proposed rejecting it, subject to product validation rules.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P1

### A-03 — Lead Without Task
- **TEST ID:** A-03
- **COMPONENT:** Lead Creation
- **SCENARIO:** Submit a lead with an empty task description.
- **PRECONDITIONS:** Test form available; task validation rules must be confirmed.
- **TEST DATA:** Synthetic name `Disha`; approved synthetic contact; task empty.
- **STEPS:** 1. Open test form. 2. Fill other fields. 3. Leave task empty. 4. Submit and inspect outcome.
- **EXPECTED BUSINESS RESULT:** A lead without a usable request should not silently proceed as complete; user proposed rejecting it, subject to contract.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P1

### A-04 — Duplicate Same Lead
- **TEST ID:** A-04
- **COMPONENT:** Lead Creation
- **SCENARIO:** Submit the same lead twice.
- **PRECONDITIONS:** Test form available; duplicate-handling rules must be confirmed.
- **TEST DATA:** Identical approved synthetic lead details in two submissions.
- **STEPS:** 1. Submit a valid test lead. 2. Repeat the identical submission. 3. Inspect the outcome for both submissions.
- **EXPECTED BUSINESS RESULT:** Avoid harmful duplicate handling; user proposed rejecting the second submission, but exact behavior requires product confirmation.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P1

### B-01 — Valid Telegram Onboarding Token
- **TEST ID:** B-01
- **COMPONENT:** Telegram Onboarding
- **SCENARIO:** Open onboarding with a valid test token.
- **PRECONDITIONS:** Authorized test Lead and valid test onboarding link available; contract and environment required.
- **TEST DATA:** Valid test token generated by authorized environment (do not record token value).
- **STEPS:** 1. Obtain approved test onboarding link. 2. Open it with the intended test Telegram account. 3. Inspect onboarding outcome.
- **EXPECTED BUSINESS RESULT:** Intended customer can begin onboarding toward their own Lead.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### B-02 — Invalid Telegram Token
- **TEST ID:** B-02
- **COMPONENT:** Telegram Onboarding
- **SCENARIO:** Attempt onboarding using an invalid token.
- **PRECONDITIONS:** Authorized test Telegram environment; token-validation rules available.
- **TEST DATA:** Deliberately invalid synthetic token; do not use live credentials.
- **STEPS:** 1. Prepare invalid test link. 2. Attempt onboarding. 3. Check whether any Lead association occurred.
- **EXPECTED BUSINESS RESULT:** Invalid token does not authorize onboarding or Lead binding.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### B-03 — Empty Telegram Token
- **TEST ID:** B-03
- **COMPONENT:** Telegram Onboarding
- **SCENARIO:** Attempt onboarding with no token.
- **PRECONDITIONS:** Authorized test onboarding flow is available.
- **TEST DATA:** Missing/empty token; synthetic test Telegram account.
- **STEPS:** 1. Open onboarding entry without a token. 2. Attempt to continue. 3. Check whether any Lead binding occurred.
- **EXPECTED BUSINESS RESULT:** No Lead is bound without valid authorization.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### B-04 — Telegram Token Reuse
- **TEST ID:** B-04
- **COMPONENT:** Telegram Onboarding
- **SCENARIO:** Attempt to reuse a token for a different test account after first onboarding.
- **PRECONDITIONS:** Two authorized test Telegram accounts; controlled test Lead; token lifecycle rules required.
- **TEST DATA:** One valid test token (not recorded), two synthetic test accounts.
- **STEPS:** 1. Complete authorized first onboarding. 2. Attempt onboarding with same token from second test account. 3. Inspect associations.
- **EXPECTED BUSINESS RESULT:** Reuse must not permit unauthorized binding; precise reuse policy requires contract confirmation.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### C-01 — Wrong Telegram-to-Lead Binding
- **TEST ID:** C-01
- **COMPONENT:** Identity Binding
- **SCENARIO:** Attempt to bind a test Telegram account to another customer's test Lead.
- **PRECONDITIONS:** Two distinct synthetic Leads and test Telegram identities in an authorized environment.
- **TEST DATA:** Synthetic Lead A (`5 doors`), Lead B (`10 windows`); test identity A; no real IDs or tokens recorded.
- **STEPS:** 1. Set up separate test Leads and accounts. 2. Attempt cross-Lead binding through approved test flow. 3. Inspect resulting association and access.
- **EXPECTED BUSINESS RESULT:** Cross-customer binding and unauthorized data access are prevented.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### D-01 — Normal User Message to AI
- **TEST ID:** D-01
- **COMPONENT:** AI Consultation
- **SCENARIO:** Send a normal consultation message.
- **PRECONDITIONS:** Authorized test user is correctly onboarded; AI consultation test interface available.
- **TEST DATA:** `Hello, I need 5 doors. Can you help?`
- **STEPS:** 1. Start approved test conversation. 2. Send message. 3. Inspect reply for relevance and continuity.
- **EXPECTED BUSINESS RESULT:** AI provides a relevant response and continues consultation.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** READY FOR TEST
- **PRIORITY:** P0

### D-02 — Empty User Message
- **TEST ID:** D-02
- **COMPONENT:** AI Consultation
- **SCENARIO:** Submit an empty user message, if the channel permits it.
- **PRECONDITIONS:** Authorized test conversation; empty-message behavior/channel support requires confirmation.
- **TEST DATA:** Empty message.
- **STEPS:** 1. Open test conversation. 2. Attempt to send empty content. 3. Observe validation or response.
- **EXPECTED BUSINESS RESULT:** Empty input is handled safely without inventing a user request; exact response is product-dependent.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P1

### E-01 — Same Event Resent to n8n
- **TEST ID:** E-01
- **COMPONENT:** n8n / Action
- **SCENARIO:** Deliver the same event twice through an approved test harness.
- **PRECONDITIONS:** Authorized isolated n8n test workflow and event-retry rules available.
- **TEST DATA:** One synthetic event delivered twice; no real customer data.
- **STEPS:** 1. Trigger an approved synthetic event. 2. Resend the same event. 3. Inspect action outcomes for unintended duplication.
- **EXPECTED BUSINESS RESULT:** Repeated delivery does not cause harmful unintended duplicate actions; exact idempotency policy requires contract.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### E-02 — External Action / Integration Failure
- **TEST ID:** E-02
- **COMPONENT:** n8n / Action
- **SCENARIO:** External service required for an action fails.
- **PRECONDITIONS:** Authorized isolated integration test with safe failure simulation; expected recovery rules available.
- **TEST DATA:** Synthetic action request and controlled simulated integration failure.
- **STEPS:** 1. Prepare approved test action. 2. Simulate external service failure. 3. Inspect reported outcome and any recovery behavior.
- **EXPECTED BUSINESS RESULT:** Failure is handled without falsely claiming action success.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** BLOCKED — REQUIRES CONTRACT
- **PRIORITY:** P0

### F-01 — Processing Result Saved
- **TEST ID:** F-01
- **COMPONENT:** Data / History
- **SCENARIO:** Verify successful action result remains available.
- **PRECONDITIONS:** Authorized test action can complete; approved result/history inspection interface available.
- **TEST DATA:** Synthetic test Lead and test action with a distinguishable result.
- **STEPS:** 1. Complete an authorized synthetic action. 2. Access the approved history/result view. 3. Verify the correct result is associated with the test Lead.
- **EXPECTED BUSINESS RESULT:** Processing result is saved and can be retrieved later.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** READY FOR TEST
- **PRIORITY:** P0

### F-02 — Conversation History Persists
- **TEST ID:** F-02
- **COMPONENT:** Data / History
- **SCENARIO:** Continue a conversation and verify earlier context is retained.
- **PRECONDITIONS:** Authorized test AI conversation; context retention policy and interface available.
- **TEST DATA:** Message 1: `I need 5 doors.` Message 2: `How much would that cost?`
- **STEPS:** 1. Send first message. 2. Continue with second message. 3. Inspect whether AI uses relevant prior context.
- **EXPECTED BUSINESS RESULT:** AI retains relevant previous conversation context in the continuing dialog.
- **TECHNICAL EXPECTATION:** TBD — REQUIRES PRODUCT/API CONTRACT
- **ACTUAL RESULT:** NOT EXECUTED
- **STATUS:** READY FOR TEST
- **PRIORITY:** P0

## 3. TOP 5 P0 Tests

1. **C-01 — Wrong Telegram-to-Lead Binding:** Incorrect identity binding can expose another client's data and compromise the entire business flow.
2. **A-01 — Correct Website Lead:** If a valid Lead cannot be created, the customer journey is blocked at the start.
3. **B-01 — Valid Telegram Onboarding Token:** If valid onboarding fails, the customer cannot proceed to AI consultation.
4. **B-02 — Invalid Telegram Token:** Accepting invalid tokens can permit unauthorized association with a customer's Lead.
5. **E-02 — External Action / Integration Failure:** Failure of a critical integration can prevent completion of the customer's requested action.

**Priority note:** P0/P1/P2 are planning judgments, not measured incident severities. Review against the product's real critical path and failure impact.

## 4. Bug Report Template — Blank (No Bugs Claimed)

```text
BUG ID:
TITLE:
COMPONENT:
SEVERITY:
ENVIRONMENT:
PRECONDITIONS:
STEPS TO REPRODUCE:
1.
2.
3.
TEST DATA:
EXPECTED RESULT:
ACTUAL RESULT:
STATUS CODE: (if applicable)
EVIDENCE:
REPRODUCIBILITY:
MY HYPOTHESIS:
BLOCKER: YES / NO
```

## 5. Knowledge Check — User's Original Answers

**Not completed yet.** Answer independently before requesting AI feedback:

1. What is the difference between a Test Case and a Bug Report?
2. Why can't a test be marked PASS if it was not executed?
3. What is Regression Testing?
4. Which stage of the full business flow is most dangerous, and why?
5. Why is wrong Telegram user-to-Lead binding more serious than a UI error?
6. Why assign P0/P1/P2 priorities?

## 6. Execution and Security Notes

- No real API requests or backend/n8n/Telegram tests were run for VAI-003.
- No test case is marked PASS or FAIL.
- No production credentials, real onboarding tokens, API keys, or customer data are included.
- All implementation-specific behavior remains subject to product/API contract confirmation.
- This document must be committed on `feature/VAI-003-regression-suite` and submitted via Pull Request for review; do not merge it.
