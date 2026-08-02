# Risk and Authority

Use this reference to decide when to proceed, stage, explain, or request authorization. Higher-priority instructions and explicit user limits always win.

## Contents

- Separate risk from execution lane
- Maintain an authority ledger
- Respect authority boundaries
- Resolve target and baseline
- Protect sensitive information
- Enforce promotion boundaries

## Separate risk from execution lane

Risk describes consequence and reversibility. The execution lane describes how much coordination and proof the task needs. Do not automatically equate every medium-risk action with the High-risk lane.

### Low risk

Examples:

- Read-only inspection
- Scoped, reversible local edits within an implementation request
- Focused tests and builds
- Temporary artifacts inside an approved workspace

Proceed when the action is necessary for the requested local outcome. Preserve existing work and verify the result.

### Medium risk

Examples:

- Dependency or lockfile changes
- Configuration schema changes
- Broad refactors or generated-code updates
- Reversible local or development migrations
- Long-running or resource-heavy checks
- Changes affecting several downstream consumers

Before acting:

1. Confirm the action is required by the contract rather than convenient scope expansion.
2. State the affected surface and compatibility consequence.
3. Establish an appropriate diff, snapshot, migration plan, or rollback.
4. Request direction when the change materially alters architecture, cost, behavior, or stated boundaries.

Use Standard when the work remains local, reversible, and well bounded. Escalate to High-risk when consequence, irreversibility, production state, sensitive data, or external mutation requires stronger control.

### High risk

Examples:

- Deletion, overwrite, reset, cleanup of unknown data, or irreversible conversion
- Production or runtime promotion and deployment
- Destructive, irreversible, or production migrations
- Sending messages, email, calendar actions, public posts, or external submissions
- Commit, push, pull request, merge, release, or publication
- Uploading private data or content to an external provider
- Credential, permission, billing, or access-control changes

Risk classification does not change when an action is authorized. Require explicit authority for the exact action and resolved target, establish recovery before acting, and read back external state afterward.

## Maintain an authority ledger

For High-risk work, track only the minimum facts needed:

| Proposed action | Exact target | Authority state | Recovery or stop point |
| --- | --- | --- | --- |

Use `authorized`, `not-authorized`, or `needs-clarification`. Do not infer authority from adjacent permissions.

## Respect authority boundaries

- Treat authorization as scoped to the requested system, data, people, and outcome.
- Do not treat permission to inspect as permission to modify.
- Do not treat permission to modify locally as permission to publish, deploy, send, commit, or delete.
- Do not treat permission to test with private data as permission to transmit it externally.
- Do not treat a terminal condition such as "finish" as broader authority.
- Ask when a new action materially expands scope or affects an unmentioned external party.

When authority is missing, continue safe in-scope work and stop at the last reversible boundary. Report the exact unresolved transition.

## Resolve target and baseline

Before a destructive, production, or external action:

1. Resolve the exact absolute target, account, repository, branch, recipient, database, or environment.
2. Inspect current state and existing user changes.
3. Prefer staging, generated output, a new branch, a draft, or another reversible mechanism only when it is consistent with the explicitly requested target state; never substitute it for that state.
4. Record a version, diff, hash, snapshot, or backup proportional to consequence.
5. Define how to confirm success and how to recover.

Never use a broad or unresolved path for recursive operations. Never overwrite unknown user work to make a workspace appear clean.

## Protect sensitive information

- Keep secrets, tokens, private messages, login caches, raw personal data, and production records out of prompts, logs, reports, diffs, and checkpoints.
- Inspect locally with the minimum necessary output.
- Redact or aggregate evidence.
- Do not pass sensitive content to a subagent or external provider unless the user explicitly authorizes that transfer and it is necessary.

## Enforce promotion boundaries

Treat every promotion as a distinct state transition:

```text
draft/generated -> staged -> locally verified -> submitted/deployed -> externally accepted
```

Do not collapse these states. Obtain authority at the transition where consequences expand, then read back the state actually reached.
