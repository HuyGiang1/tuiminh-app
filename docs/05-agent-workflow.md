# 05 — How ChatGPT, human and coding agent collaborate

## Roles
- **You / product owner**: approve priorities, visual changes, accounts/costs, device tests, production actions.
- **ChatGPT / architect & reviewer**: break tasks into small acceptance criteria, assess agent results, issue next precise prompt, maintain architecture coherence.
- **Coding agent / implementer**: inspect repo first, plan scoped changes, code, run tests, show evidence, update handoff docs.

## Turn cycle
1. ChatGPT outputs a TASK-ID prompt (one milestone slice, exact scope, acceptance gates).
2. Human pastes prompt to coding agent and approves its plan before significant changes.
3. Agent executes within allowed environment and returns report with branch, SHA, files, commands, tests, screenshots and blockers.
4. Human pastes report to ChatGPT. ChatGPT reviews evidence, may request targeted fixes, then emits next TASK-ID.
5. Agent updates `docs/PROJECT_STATE.md` and commits after a completed task.

## Four mandatory gates
A. Architecture approval: no new major library/cloud service without written rationale and approval.
B. Design approval: screenshot/prototype before heavy animation implementation.
C. Security/privacy approval: before first external media storage and real-couple data.
D. Deployment approval: no production or billing operations without explicit one-off consent.

## Agent report template
```
TASK: Mx-Tyy
STATUS: PASS | PARTIAL | FAIL
BRANCH / COMMIT:
CHANGED FILES:
TEST COMMANDS + RESULTS:
UI PROOF (screenshots/video links):
SECURITY / COST IMPACT:
OPEN RISKS / UNVERIFIED:
UPDATED DOCS:
NEXT PROPOSED TASK:
```

## Ground truth ordering
Repository files & actual test output > committed decision log > latest agent report > conversation recollection. Never invent current commit hashes or test runs. Every new chat must read `docs/PROJECT_STATE.md` plus `docs/DECISIONS.md` before proposing edits.
