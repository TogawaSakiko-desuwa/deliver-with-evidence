---
name: deliver-with-evidence
description: Orchestrate explicitly requested end-to-end delivery of non-trivial work from grounded scope to current, user-visible evidence across code, documents, data, interfaces, runtime changes, and authorized external systems. Use when the user invokes $deliver-with-evidence or explicitly asks an agent to carry a concrete artifact or change through implementation and verification. Combine with specialist skills. Do not use implicitly for Q&A, brainstorming, planning, lookup, diagnosis-only, review-only, or one-step low-risk edits.
license: MIT
---

# Deliver with Evidence

Own the delivery lifecycle while specialist skills own domain technique. Keep scope, authority, implementation, verification, and handoff connected.

## Select the lightest safe lane

- **Fast**: Complete a small, reversible task with obvious scope. Keep a lightweight contract internal: identify the target, exclusions, authority boundary, and decisive check; then hand off briefly.
- **Standard**: Complete a non-trivial local artifact or multi-step change. Make the contract explicit in working notes and verify each success criterion.
- **High-risk**: Handle destructive or irreversible work, sensitive data, production/runtime promotion, or external writes. Resolve exact targets, establish recovery, and obtain explicit authority before crossing the consequential boundary.

Treat risk and lane as related but separate. A reversible local development migration may use Standard with medium-risk safeguards; a production, destructive, or irreversible migration requires High-risk. Read [risk-and-authority.md](references/risk-and-authority.md) before medium- or high-risk work, external writes, destructive actions, or sensitive-data handling. If the reference cannot be read, treat unresolved external, destructive, sensitive-data, production, and irreversible work as High-risk and do not cross its consequential boundary.

Fast example: for a request to correct one misspelling and verify displayed help, keep an internal contract of one help string, no CLI or documentation refactor, local-edit authority only, and the real `--help` output as the decisive check. Make the narrow edit, run that check, and hand off briefly.

## Run the delivery workflow

### 1. Ground

Establish the actual state before choosing a solution:

1. Classify the request as answer, plan, diagnosis, review, implementation, artifact production, or external operation. Honor the requested boundary and the host's current collaboration mode.
2. Read applicable system, host, and project instructions plus authoritative specifications, configuration, schemas, entry points, and release rules.
3. Inspect the workspace, repository boundary, existing user changes, target files, runtime state, and available verification commands. Preserve unrelated work.
4. Identify protected data, secrets, production state, external recipients, and transitions between local, staged, submitted, deployed, and accepted states.
5. Discover facts before asking about preferences. Ask only when a missing choice changes architecture, behavior, authority, cost, or acceptance.

Stop at diagnosis or review when that is all the user requested. Do not turn a report into an implementation.

Read [project-contract.md](references/project-contract.md) when project instructions exist, conflict, or need to be proposed.

### 2. Contract

Lock the smallest useful delivery contract before substantive implementation:

- Goal and intended user effect
- Concrete deliverables
- Observable success criteria
- In-scope and out-of-scope work
- Compatibility, environment, privacy, cost, and time constraints
- Authorized local and external actions
- Evidence required for every success criterion

Prefer the smallest vertical slice that produces the requested outcome and can be verified at a real boundary. Do not add speculative abstractions, dependencies, broad cleanup, or automation whose value is not required by the contract. Ask before expanding scope when the larger option materially changes behavior, architecture, cost, or maintenance burden.

Keep the contract internal for Fast work. Surface it for long-running, interrupted, multi-party, ambiguous, or High-risk work.

### 3. Route

Choose the smallest set of specialist workflows that covers the contract:

- Use diagnosis to establish cause and a red-capable signal before fixing a hard bug.
- Use TDD when test-first development or integration tests are requested.
- Use review workflows for specification and standards review.
- Use the relevant specialist workflow for documents, PDFs, presentations, spreadsheets, images, frontends, or browser-driven interfaces; when one is available, load and follow it before applying domain-specific changes.
- Use provider workflows for repositories, communications, deployments, and other external systems.

Follow each selected workflow instead of restating it here. If a preferred specialist is unavailable, use safe host-native capabilities and preserve its important guarantees. Report a blocker only when the outcome actually depends on a missing capability.

Parallelize bounded, independent work only when it improves speed or confidence. Keep one owner for integration and final evidence, and avoid overlapping edits.

### 4. Execute

Implement in small, verifiable slices:

1. Protect the baseline with version-control state, a diff, hash, backup, snapshot, or staging copy proportional to risk.
2. Change only what the contract requires. Separate unrelated cleanup and redesign.
3. Keep generated content, migrations, experiments, and risky configuration out of runtime or production until promotion is authorized.
4. Verify each slice before depending on it. Classify failures as implementation, environment, evidence, authority, or external-state failures instead of repeating commands blindly.
5. Give concise progress updates during long work and record a sanitized recovery point only when interruption or handoff is plausible.

Never infer authority to commit, push, open or merge a pull request, deploy, publish, send, delete, purchase, or make another external mutation. Treat each promotion as a separate state transition with a resolved target and authority boundary. An explicit request for an exact end state authorizes only the indispensable intermediate transitions to that same target unless the user excludes them; host approvals still apply. Honor the authorized target state exactly: do not silently substitute an earlier state such as a draft when a reviewable submission was requested, and do not cross into a later state. If the exact state is unsafe or unavailable, stop and report the gap.

### 5. Verify

Read [verification-matrix.md](references/verification-matrix.md) for every relevant deliverable category. If the reference cannot be read, do not claim `verified` for an affected category; report the missing verification guidance and evidence.

Maintain a current requirement-to-evidence map:

| Success criterion | Material change | Decisive check or observation | Result |
| --- | --- | --- | --- |

Apply these rules:

- Verify the final observable outcome, not only an upstream helper, generated file, successful build, process, or API call.
- Run the narrowest decisive checks first, then broader regression, build, render, runtime, or end-to-end checks proportional to risk.
- Inspect final artifacts and the final diff for scope drift, debug residue, placeholders, accidental files, and sensitive output.
- Use evidence from the final source state. Do not reuse historical success as current proof.
- Record checks that failed, were skipped, or were unavailable and explain the consequence.

Fix in-scope causes while safe progress remains. Stop when progress requires new authority, missing input, unavailable external state, or material scope expansion.

### 6. Handoff

Report two independent statuses.

**Work status**

- `complete`: All contracted deliverables are implemented within the authorized boundary.
- `partial`: A meaningful subset is delivered, but at least one contracted part remains.
- `blocked`: Missing input, access, environment, authority, or dependency prevents meaningful delivery.

**Outcome evidence**

- `verified`: Current evidence supports every applicable criterion for the reported completed work.
- `needs-user-validation`: Objective checks pass, but subjective acceptance or a user-only environment remains.
- `waiting-external`: The explicitly requested submission or deployment state is reached and read back, but a third-party state is pending. An earlier draft or staging state does not qualify unless that was the requested target.
- `not-reached`: The required acceptance stage could not be entered because work, authority, access, or evidence is missing.

Use only these combinations and exact labels:

| Work status | Allowed Outcome evidence |
| --- | --- |
| `complete` | `verified`, `needs-user-validation`, `waiting-external`, or `not-reached` |
| `partial` | `verified`, `needs-user-validation`, `waiting-external`, or `not-reached` |
| `blocked` | `not-reached` only |

Use `complete + verified` only when every criterion has current evidence. Use `complete + not-reached` only when every contracted deliverable is implemented within the authorized boundary but a required real verifier or target environment is unavailable and cannot be substituted. If that unavailable capability is also the only path to create a requested final artifact or complete another contracted deliverable, the work remains `partial + not-reached`; for example, an unavailable renderer that prevents the requested PDF from being generated is not `complete`. A failed check caused by an unresolved in-scope defect means the work is not complete. For every `partial` handoff, name both the completed and missing subsets and make the evidence scope explicit. Use `partial + verified` when a completed subset has reached its own required observable boundary with current evidence, then name each unfinished stage as not reached. Use `partial + not-reached` when a deliverable remains unfinished and missing verifier, authority, access, or environment also prevents outcome evidence at its required boundary. Do not invent status synonyms.

Keep the final handoff proportional to the task while preserving:

1. Both statuses and the outcome
2. Material deliverables or changes
3. Verification performed and exact results
4. Unverified, incomplete, or externally pending items
5. Current local, runtime, submission, deployment, and acceptance state
6. Remaining risk, recovery path, and required user action
