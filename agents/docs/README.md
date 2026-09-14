# Documentation Sites and Illustrated Manuals

This plugin provides three skills for VitePress assets, document fact maintenance, and manuals based on actual interfaces. Use them with existing documentation or combine them for a new site.

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [中文](./README_zh.md)

## Quick Facts

| Item | Details |
| --- | --- |
| Plugin | `h-level-docs` |
| Skills | 3 |
| Main inputs | Code, APIs, database models, running interfaces, existing documentation, and version evidence |
| Main outputs | Documentation sites, current guides, illustrated task pages, mappings, and verification results |

## Skills

| Skill | When to use | Main artifact or resource |
| --- | --- | --- |
| [docs-site-bootstrap](./skills/docs-site-bootstrap/SKILL.md) | Initialize or update the packaged VitePress site | Site assets and bootstrap manifest |
| [docs-maintenance](./skills/docs-maintenance/SKILL.md) | Synchronize or audit docs against implementation | Pages, mappings, version anchors, and checks |
| [manual-gen](./skills/manual-gen/SKILL.md) | Document tasks from actual interfaces | Task pages, screenshots, outcomes, and recovery |

## Choosing a Capability

- Choose `docs-site-bootstrap` for site setup and asset updates, preserving host-authored content and checking repeat runs.
- Choose `docs-maintenance` for product, design, API, database, and operations facts, including read-only audits.
- Choose `manual-gen` for real steps and screenshots organized by user task.

## Installation and Use

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-docs@h-level-model-skills
```

See the [Codex Guide](../../docs/README.codex.md) for personal and project installs. From the repository root, install all eight skills into the selected target:

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

Describe the goal or choose a skill through the host, for example:

```text
Use docs-site-bootstrap to create a public/internal documentation site.
Use docs-maintenance to check API pages against current routes and schemas.
Use manual-gen to update account setup with real screenshots and recovery steps.
```

## Inputs and Artifacts

The packaged site supports public/internal builds, page fields, navigation, templates, and version data. Keep established host paths and update indexes, references, screenshots, and affected change-map entries when pages move.

For durable artifacts, use existing project locations or adapt this layout, creating only the files needed for the task:

```text
docs/site/
  product/
  design/
  api/
  database/
  manual/
  ops/
  release-notes/
  standards/
  .meta/
```

## Verification

`related_code` and change-map locate affected pages; factual conclusions still require implementation and test evidence. `last_verified_version` records an actual review, not merely a passing metadata check.

Inside a bootstrapped `docs/site/`, run the checks relevant to the change:

```bash
npm run test:docs
npm run build:public
npm run build:internal
npm run check:affected -- --base <base-ref>
```

## Combining Capabilities

Use the product plugin’s release-management for site release notes. manual-gen can reuse verified E2E journeys, and human-writing can support Chinese pages.

The assistant keeps the task’s scope and authorization while combining relevant references. See the [repository README](../../README.md) for other plugins.

## Local Maintenance

Skill sources live under `skills/`. Synchronize descriptions, registration, and the lockfile after changes; see the [maintenance guide](../../docs/cookbook/maintain-skills.md) for checks.
