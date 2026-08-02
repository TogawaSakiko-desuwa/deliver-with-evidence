# Verification Matrix

Select evidence by deliverable and risk. Use more than one layer when failure can occur after an earlier layer succeeds.

## Contents

- General rules
- Code, libraries, APIs, and plugins
- User interfaces and websites
- Documents, PDFs, presentations, and spreadsheets
- Data, generated datasets, and migrations
- Configuration, runtime, and deployment
- External systems and communications

## General rules

- Map every success criterion to a material change and a current check, inspection, or read-back.
- Prefer behavior at a public or user-visible boundary.
- Verify negative requirements, including protected files and systems remaining unchanged.
- Record exact commands, counts, artifacts, URLs, IDs, or observed states without exposing secrets.
- Mark unavailable evidence as unavailable. Do not replace it with confidence language.
- Distinguish objective verification from subjective user acceptance.

## Code, libraries, APIs, and plugins

Minimum evidence:

- Focused tests for changed behavior
- Relevant type, lint, compile, or build checks
- Regression checks for adjacent contracts
- Final diff review for scope, compatibility, debug residue, and accidental files

Final-effect evidence:

- Exercise the public API, command, plugin host, or integration boundary users depend on.
- For a bug fix, reproduce the original failure and show it no longer occurs.

Reject these false proofs:

- A helper unit test passes while the real caller remains untested.
- Import success is treated as host compatibility.
- Historical CI or release output is treated as a current run.

## User interfaces and websites

Minimum evidence:

- Build and relevant automated component or end-to-end checks
- Runtime inspection of the changed path
- Console and network error inspection
- Representative viewport, DPI, theme, keyboard, and accessibility checks when relevant

Final-effect evidence:

- Drive the actual user flow and inspect the rendered result.
- Confirm persistence and reload behavior when settings or data change.

Reject these false proofs:

- A successful build is treated as visual or interaction acceptance.
- A source change is assumed to affect the deployed or packaged interface.

## Documents, PDFs, presentations, and spreadsheets

Use the applicable artifact workflow and its render-and-verify process.

Minimum evidence:

- The file opens successfully in the intended format.
- Required content and source coverage are present.
- Formulas, links, headings, tables, pagination, or notes work as applicable.
- Rendered pages, slides, or sheets receive visual inspection.

Final-effect evidence:

- Inspect the exact final artifact, not only its source or template.

Reject these false proofs:

- File creation is treated as readable layout.
- Extracted text is treated as proof that charts, page breaks, or fonts render correctly.

## Data, generated datasets, and migrations

Minimum evidence:

- Schema and constraint validation
- Row counts, uniqueness, null, range, and referential checks
- Deterministic seed or source provenance when reproducibility matters
- Before-and-after samples or hashes that do not expose private records
- Idempotency or safe rerun behavior when required

Final-effect evidence:

- Read data through the consuming application or query path.
- Test rollback or restore mechanics for material migrations.

Reject these false proofs:

- A migration command exits successfully without reading back schema or data.
- A sample passes while the full dataset violates integrity constraints.

## Configuration, runtime, and deployment

Minimum evidence:

- Parse and schema validation
- Effective configuration or route inspection, including fallbacks
- Process, port, dependency, and health checks
- Log inspection for the changed flow
- A resolved rollback target and procedure

Final-effect evidence:

- Exercise the end-to-end action at the actual runtime boundary.
- Read back the deployed version or saved state.

Reject these false proofs:

- A process exists, but the service is not listening or healthy.
- A provider call succeeds, but the downstream message or action is not delivered.
- A saved version is treated as deployed or a deployment as third-party acceptance.

## External systems and communications

Minimum evidence:

- Confirm the exact target, recipient, repository, branch, environment, and action before mutation.
- Use idempotency protection when available.
- Read back the resulting object, status, link, message, event, or identifier.

Final-effect evidence:

- Distinguish drafted, sent, submitted, published, merged, approved, deployed, and accepted states.

Reject these false proofs:

- A local commit is treated as pushed.
- A pushed branch is treated as a pull request.
- An open pull request or issue is treated as merged or approved.
- A draft is treated as sent.
