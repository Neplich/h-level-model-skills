# Security and Privacy Review

This plugin provides `security-review`, loading application, authorization, dependency, or privacy references for the requested surface. It applies to explicit security and privacy review tasks.

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [中文](./README_zh.md)

## Quick Facts

| Item | Details |
| --- | --- |
| Plugin | `h-level-security` |
| Skills | 1 |
| Main inputs | Review scope, code, configuration, resolved dependencies, identities, permissions, and data flows |
| Main outputs | Code evidence, permission matrices, dependency applicability, and data lifecycle maps |

## Skills

| Skill | When to use | Main artifact or resource |
| --- | --- | --- |
| [security-review](./skills/security-review/SKILL.md) | Explicit security or privacy reviews | Surface-specific checklists and findings |

## Choosing a Capability

- Use AppSec references for input, execution, and output boundaries, tracing reachable paths and defenses.
- Use authorization references for identity, object permissions, and tenant isolation matrices.
- Dependency reviews check resolved versions, advisories, and applicability; privacy reviews trace collection, sharing, retention, and deletion.

## Installation and Use

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-security@h-level-model-skills
```

See the [Codex Guide](../../docs/README.codex.md) for personal and project installs. From the repository root, install all eight skills into the selected target:

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

Describe the goal or choose a skill through the host, for example:

```text
Use security-review to inspect object permissions and cross-tenant access in admin exports.
Use security-review to trace personal data, caches, and external processors after account deletion.
```

## Inputs and Artifacts

Each finding retains its location, preconditions, defenses, concrete impact, and repair direction. Organize the report around the reviewed surface; prefer an existing dedicated security workflow when the host provides one.

## Verification

Distinguish advisory severity from demonstrated application impact. Record evidence gaps for unverified paths; legal conclusions require current authoritative requirements for the applicable jurisdiction. Ordinary login or dependency changes do not automatically trigger repository-wide audits.

## Combining Capabilities

Findings can guide authorized implementation, regression, and documentation. Use e2e-testing for persistent runtime evidence and Docs for interface or data-handling documentation.

The assistant keeps the task’s scope and authorization while combining relevant references. See the [repository README](../../README.md) for other plugins.

## Local Maintenance

Skill sources live under `skills/`. Synchronize descriptions, registration, and the lockfile after changes; see the [maintenance guide](../../docs/cookbook/maintain-skills.md) for checks.
