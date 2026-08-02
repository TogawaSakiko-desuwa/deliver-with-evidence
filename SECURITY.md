# Security Policy

`deliver-with-evidence` is a behavioral orchestration skill, not a security sandbox. The host agent's approval, credential, filesystem, network, and provider controls remain the enforcement boundary.

## Supported versions

| Version | Security updates |
| --- | --- |
| `main` before the first release | Reviewed on a best-effort basis |
| `0.1.x` public preview | Support begins when `v0.1.0` is published |
| Earlier drafts | Not supported |

## Report a vulnerability

Use GitHub's **Security** tab and select **Report a vulnerability** to send a private report. Do not open a public issue for a vulnerability or include live credentials, private content, production records, or an exploit against a system you do not own.

Include, where safely possible:

- the affected version or commit;
- the prompt and minimum sanitized fixture needed to reproduce the behavior;
- the host agent and relevant permission configuration;
- the authority that was actually granted;
- the action or disclosure that occurred or could occur;
- expected safe behavior; and
- suggested mitigations, if known.

This is a volunteer project and does not promise a response-time SLA. Maintainers will keep valid reports private while assessing impact and preparing a fix, then coordinate disclosure appropriate to the risk.

## Security-relevant behavior

Please report behavior that could cause or materially encourage:

- an external write, submission, deployment, publication, message, merge, or deletion without explicit authority;
- destructive work against an unresolved, overly broad, or incorrect target;
- exposure of secrets, private messages, credentials, production data, or sensitive evidence;
- promotion from draft or local state into runtime, production, or a public system without authorization;
- bypass of host approval or sandbox controls;
- a false claim of verification that conceals a consequential unsafe state; or
- prompt or repository content overriding higher-priority authority and safety constraints.

Ordinary wording suggestions, missed non-security triggers, documentation corrections, and non-sensitive validation bugs can be reported through normal GitHub issues.

## Safe research expectations

- Test only against repositories, accounts, data, and systems you own or are authorized to use.
- Prefer disposable fixtures, fake providers, local bare remotes, and non-production environments.
- Use canary values rather than real secrets.
- Stop before a real external or destructive action when a local reproduction is sufficient.
- Remove sensitive details from logs, screenshots, traces, and evaluation artifacts.

The MIT License disclaims warranty; responsible reports are nevertheless welcome and help improve the skill's safety contract.
