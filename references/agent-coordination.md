# Agent coordination

Read this when drafting or interpreting an agent handoff, action request, or execution report. Fit the receiving system's existing protocol. These conventions describe meaning; they do not authorize sending a message or performing its requested action.

## Message types

Use only the types needed. Split a message when clauses perform different functions; do not duplicate the same content under every marker.

| Marker | Meaning | Preserve or include when relevant |
|---|---|---|
| `INFORMATION` | An observation or attributed report | Source, scope, time, and whether you observed it directly |
| `INFERENCE` | An interpretation of evidence | Supporting evidence and remaining uncertainty |
| `QUESTION` | A request for information | The specific unknown and why it affects the next action |
| `REQUEST` | A requested action | Recipient, target, scope, prerequisites, and source of authority |
| `RECOMMENDATION` | Advice the recipient may consider | Reason, trade-off, and any condition on the advice |
| `PLAN` | An intended future action | Owner and dependencies; no implication that execution has begun |
| `RESULT` | What actually happened | Action or outcome, evidence, status, and verification limits |
| `WARNING` | A relevant risk | The trigger and possible consequence; do not assert that it has occurred |

This is an adaptation of SMCP, with added distinctions for inference and results. `RECOMMENDATION`, `PLAN`, `INFERENCE`, and `RESULT` are not a claim about official SMCP markers. An answer can be `INFORMATION`, `INFERENCE`, or `RESULT`, as its content warrants.

`REQUEST` does not itself decide whether an action is mandatory or optional. If the user or another authorized source requires something, retain that requirement explicitly with its source and scope. If someone only suggests it, preserve that discretion. Do not relabel a suggestion into an obligation, or weaken an existing obligation into advice.

## Context fields

Include fields only when they resolve ambiguity. Use existing task identifiers; do not invent an ID that could be mistaken for a real tracker entry.

| Field | Purpose |
|---|---|
| `task` / `in_reply_to` | Associate the exchange with the right work or question |
| `owner` / `recipient` | Identify who will act or answer |
| `purpose` | Explain the intended outcome when local optimization could miss it |
| `target` / `scope` | Identify the exact object and boundaries of the action |
| `constraints` / `prerequisites` | Carry forward the applicable conditions |
| `completion_criteria` | Record established success criteria; distinguish proposals |
| `authority` | Attribute the instruction or authorization, without manufacturing it |
| `assumptions` | Mark unresolved working assumptions |
| `status` | State the actual stage of work |
| `evidence` / `limits` | Support the claim and identify material gaps in verification |

Unknown fields can be omitted when immaterial, or explicitly marked unknown when needed. Do not fill a template merely for visual completeness.

## Status is not a message type

Keep work state separate from intent. Use the recipient's established status vocabulary when available; otherwise these words express distinct states:

- `received`: The message arrived; understanding and acceptance are not established.
- `accepted`: The recipient committed to the scoped task; execution is not established.
- `in_progress`: Execution started; completion is not established.
- `blocked`: A specific dependency prevents the next required action; identify it.
- `completed`: The stated action finished; broader effectiveness may remain unverified.
- `verified`: Named criteria were checked with supporting evidence; limit the claim to those checks.
- `failed`: An attempt did not achieve its stated result; report known effects and remaining work.

These are descriptions, not a mandatory sequence of acknowledgment messages. An action can be completed while its outcome remains unverified; report both facts. Never set a tool or workflow's status contrary to that system's own definition.

## Scoped handoff

The following is a fictional example whose details are supplied by its task context:

```text
task: export-42
recipient: verifier
purpose: Establish whether the staging export is complete.
authority: User requested verification; no upload was requested.

INFORMATION: The export process returned exit code 0.
REQUEST: Compare staging/export.csv with staging/expected-records.json.
constraints: Read only. Keep both files unchanged.
completion_criteria: Report missing IDs, duplicate IDs, and the row count.
```

A proportionate reply after actually running those checks:

```text
task: export-42
RESULT: Checked staging/export.csv against staging/expected-records.json.
status: verified
evidence: 240 expected IDs; 240 rows; no missing or duplicate IDs.
limits: Field values were not compared. Nothing was uploaded.
```

The initial exit code does not establish completeness. The reply supports the named ID and count checks, not field accuracy or successful delivery. Do not copy the fictional numbers as evidence for a real task.

## Corrections and confirmation

For an error that could affect action, identify the earlier claim or task, state the correction, and describe its effect on the next step. Do not imply that a corrected message undid an action already taken.

If a wrong interpretation could cause a consequential action, ask for a focused read-back of the disputed target, boundary, or condition. Confirm or correct that interpretation. Do not require a repeated acknowledgment once the material ambiguity is resolved.

## Machine-readable exchanges

Use JSON only when the recipient expects or can consume it. Follow its schema. The same distinctions can be represented as `type`, `content`, and relevant context fields; a JSON object is not proof of truth, successful execution, or authorization. This skill supplies semantic conventions, not a transport protocol or enforced schema.
