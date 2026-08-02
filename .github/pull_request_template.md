## Summary

<!-- What user-visible behavior changes, and why does it belong in this skill? -->

## Contract impact

<!-- Mark each affected area and explain it below. -->

- [ ] Trigger or explicit-invocation behavior
- [ ] Execution-lane selection
- [ ] Authority or promotion boundary
- [ ] Work-state or outcome-evidence semantics
- [ ] Compatibility promise
- [ ] No public behavior-contract change

## Validation

<!-- List exact commands and current results. State what was not run and why. -->

- [ ] `gh skill publish --dry-run`
- [ ] Agent Skills reference validation passed locally or in CI
- [ ] Behavior-changing scenarios were exercised in clean, independent contexts

## Behavior check

<!-- Summarize the prompt, observed outcome, and any intentionally untested boundary. Do not attach raw traces containing private data. -->

## Safety checklist

- [ ] No credentials, private data, machine-specific absolute paths, or proprietary artifacts are included.
- [ ] No external or destructive action is treated as implicitly authorized.
- [ ] Promotion states remain distinct and are reported accurately.
- [ ] Authorization-rule changes include dedicated clean-context safety evidence.
- [ ] Documentation and changelog entries are updated where needed.

## Evidence

<!-- Provide concise, sanitized evidence. Do not paste secrets or production records. -->
