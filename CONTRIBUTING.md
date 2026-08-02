# Contributing

Thanks for helping make `deliver-with-evidence` safer, clearer, and easier to verify.

## Before opening a change

1. Search existing issues and pull requests for overlapping work.
2. Keep the proposal aligned with the skill's purpose: orchestration from grounded scope to evidence-backed delivery.
3. Open an issue first when a change would alter the authority model, status semantics, trigger boundary, or compatibility promise.
4. Report security-sensitive behavior privately as described in [SECURITY.md](SECURITY.md).

## Make a focused contribution

- Keep `SKILL.md` concise, imperative, and limited to essential workflow instructions.
- Keep its YAML frontmatter limited to `name` and `description`; the description owns trigger guidance.
- Put detailed reusable guidance in a directly linked file under `references/` rather than duplicating it in `SKILL.md`.
- Keep repository documentation and release notes outside the skill directory.
- Do not add local test suites, evaluation fixtures, raw traces, runner output, or machine-specific workspaces to the public tree.
- Preserve explicit authority boundaries. A convenience improvement must never imply permission for external writes, destructive actions, sensitive-data transfer, or promotion.
- Exercise a representative clean-context scenario whenever behavior, triggering, lane selection, status reporting, or safety constraints change.
- Exercise a dedicated safety scenario for every change to an authorization or destructive-action rule.
- Summarize sanitized observations in the pull request, including prohibited actions that did not occur and any boundary that was not tested.
- Do not include credentials, private prompts, production data, machine-specific absolute paths, or proprietary artifacts in validation evidence.

## Validate locally

Run the publication check:

```console
gh skill publish --dry-run
```

CI runs a pinned Agent Skills reference validator against the public skill directory. Behavioral changes still need clean, independent agent contexts: do not give the evaluating agent the expected answer, diagnosis, intended fix, lane, or handoff states.

## Pull request requirements

A pull request should:

- explain the user-visible behavior change and why it belongs in this skill;
- identify any changes to triggering, risk classification, authority, state semantics, or compatibility;
- include concise, sanitized evidence for relevant behavior checks;
- list exact verification commands and current results;
- disclose checks that were not run and why; and
- remain focused on one coherent change.

Use the repository pull request template. Maintainers may request a smaller change when unrelated edits make safety or behavioral review difficult.

## Versioning

The project follows semantic versioning for its public behavior contract:

- **Patch**: wording or validation corrections that preserve intended behavior.
- **Minor**: backward-compatible capabilities.
- **Major**: changes to the skill name, trigger contract, authority model, status meanings, or invocation policy after a stable release.

During the v0.1.0 public preview, behavior may still change based on real use and clean-context validation. Such changes must remain documented in [CHANGELOG.md](CHANGELOG.md).

By contributing, you agree that your contribution is licensed under the repository's [MIT License](LICENSE).
