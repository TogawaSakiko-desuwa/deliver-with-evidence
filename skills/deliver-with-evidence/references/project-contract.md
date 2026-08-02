# Project Contract

Use project instructions to preserve stable repository knowledge across tasks. Keep cross-project delivery behavior in this skill; keep repository-specific truth in the nearest applicable project-instruction file, such as `AGENTS.md`.

## Read existing instructions

Before editing:

1. Locate every applicable project-instruction file from the workspace root to the target path.
2. Apply the most specific relevant instruction while respecting higher-priority system, host, and user instructions.
3. Confirm supported environments, authoritative specifications, protected areas, standard commands, and the repository's definition of done against current files.
4. Treat stale or contradictory instructions as a finding. Do not silently select the convenient version.

## Handle a missing contract

Do not create a project-instruction file automatically.

- Discover enough repository truth to complete the current task safely.
- Keep task-specific decisions in the task contract or a temporary recovery point.
- At handoff, suggest a project contract only when the repository is likely to receive continued work and missing knowledge caused repeated discovery or risk.
- Create or update it only when the user explicitly requests that durable change.

## Store only stable project truth

A useful project contract may include:

- Project purpose and component boundaries
- Authoritative specifications and architecture decisions
- Supported operating systems, runtimes, package managers, and locked versions
- Standard setup, build, test, lint, render, and verification commands
- Protected files, generated directories, private data, and upstream-owned code
- Compatibility, migration, release, deployment, and rollback rules
- Repository-specific definition of done
- Durable communication or explanation preferences

Omit claims that cannot be verified.

## Keep transient material elsewhere

Do not store these as project instructions:

- Current task progress or personal to-do lists
- One-off debugging hypotheses
- Secrets, tokens, private content, or production records
- Volatile process IDs, ports, temporary paths, or external status
- Long release histories, postmortems, or copied documentation
- Rules that merely repeat higher-priority platform instructions

Use a sanitized recovery point for temporary continuation state and normal project documentation for durable domain knowledge.

## Suggested minimal shape

When the user requests a new contract, adapt this outline to verified facts:

```markdown
# Project instructions

## Purpose and boundaries
## Authoritative sources
## Supported environment
## Standard commands
## Protected data and files
## Verification and definition of done
## Release and rollback
## Communication preferences
```

Keep the contract short enough to remain trustworthy. Update it when stable project truth changes, not after every task.
