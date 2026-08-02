# Changelog

All notable changes to `deliver-with-evidence` are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the project intends to follow [Semantic Versioning](https://semver.org/spec/v2.0.0.html) for its public behavior contract.

## [Unreleased]

Planned `v0.1.0` public-preview baseline. Move these entries into a dated release section only when the tag and GitHub release exist.

### Added

- Six-phase delivery workflow: Ground, Contract, Route, Execute, Verify, and Handoff.
- Fast, Standard, and High-risk execution lanes.
- Minimum-useful-vertical-slice constraint to resist speculative scope expansion.
- Explicit authority and promotion boundaries for destructive, sensitive, production, and external actions.
- Requirement-to-change-to-evidence mapping across code, UI, artifacts, data, runtime, and external systems.
- Two-axis handoff model separating Work status from Outcome evidence.
- Project-contract, risk-and-authority, and verification-matrix references.
- Explicit-only invocation on Codex for the initial public preview; other Agent Skills hosts retain their own activation semantics.
- Pinned Agent Skills specification validation in CI.
- English canonical documentation and corresponding Simplified Chinese documentation.

### Changed

- Reorganized both READMEs around the first-use path: outcome, installation, trial prompt, expected handoff, workflow, and deeper policy.
- Surfaced installation verification, project boundaries, and repository structure without relying on unpublished badges or adoption claims.
- Made Fast-lane contracts lightweight but explicit internally, and added fail-closed behavior when risk or verification references cannot be read.
- Closed the two-axis handoff model to eight valid status combinations with exact labels and clarified evidence scope for partial work.
- Clarified repeat-validation expectations for critical safety scenarios and documented per-host invocation syntax.
- Required explicitly authorized promotion targets to be reached exactly instead of silently substituting an earlier draft or staging state.
- Required an available domain specialist workflow to be loaded and followed before domain-specific changes.
- Clarified that work remains `partial + not-reached` when an unavailable verifier also prevents a requested final artifact from being generated.
- Limited the public repository to the runtime skill, project documentation, and structural CI; local verification assets remain unpublished.
- Removed unsupported release-qualification claims; `v0.1.0` remains a public preview.

[Unreleased]: https://github.com/TogawaSakiko-desuwa/deliver-with-evidence/commits/main
