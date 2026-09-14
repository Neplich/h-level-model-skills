# Product, Specifications and Releases

This plugin provides three skills for specification templates, release conventions, and Chinese writing preferences. Use them independently or together in a design, documentation, or release task.

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [中文](./README_zh.md)

## Quick Facts

| Item | Details |
| --- | --- |
| Plugin | `h-level-product` |
| Skills | 3 |
| Main inputs | Requirements, existing specifications, code, tests, tags, commits, and PRs |
| Main outputs | PRD/TRD/API/ADR, test specifications, release content, and reader-facing prose |

## Skills

| Skill | When to use | Main artifact or resource |
| --- | --- | --- |
| [spec-authoring](./skills/spec-authoring/SKILL.md) | Maintained specifications or a requested format | Templates, state fields, and feature paths |
| [release-management](./skills/release-management/SKILL.md) | Version changes and release preparation | Changelogs, site notes, and GitHub Releases |
| [human-writing](./skills/human-writing/SKILL.md) | Chinese writing and revision | Clear prose and document organization |

## Choosing a Capability

- Choose `spec-authoring` for maintained specifications, loading only the PRD, TRD, API, ADR, or test template needed.
- Choose `release-management` for versioned changes or publication content based on one verified scope.
- Choose `human-writing` for Chinese prose while preserving terms, formats, practical detail, and writing preferences.

## Installation and Use

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-product@h-level-model-skills
```

See the [Codex Guide](../../docs/README.codex.md) for personal and project installs. From the repository root, install all eight skills into the selected target:

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

Describe the goal or choose a skill through the host, for example:

```text
Use spec-authoring to document the bulk export API contract and migration design.
Use release-management to prepare a changelog and a preview of the next release.
Use human-writing to restore the Chinese installation guide’s structure and practical steps.
```

## Inputs and Artifacts

Specifications follow the host format first; the defaults provide document states, relationship fields, and stable feature paths. Release artifacts share a commit or tag scope and use channel-specific presentation.

For durable artifacts, use existing project locations or adapt this layout, creating only the files needed for the task:

```text
docs/pm/{feature}/PRD.md
docs/engineer/{feature}/TRD.md
docs/engineer/{feature}/API.md
docs/changelog/changelog-v{version}.md
```

## Verification

Check GitHub tags, prerelease, and latest separately. Text previews, drafts, and published releases are distinct outcomes; version metadata records actual versions and verification.

## Combining Capabilities

Combine with E2E for runtime acceptance and Docs for site fact updates. `human-writing` can also revise Chinese artifacts produced using other plugins.

The assistant keeps the task’s scope and authorization while combining relevant references. See the [repository README](../../README.md) for other plugins.

## Local Maintenance

Skill sources live under `skills/`. Synchronize descriptions, registration, and the lockfile after changes; see the [maintenance guide](../../docs/cookbook/maintain-skills.md) for checks.
