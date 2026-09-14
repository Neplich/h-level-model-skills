# H-Level Model Skills

[English](README.md) · [简体中文](README_zh.md)

A focused library for highly autonomous models: four plugins and eight directly usable skills. It retains reusable assets, specialized formats and writing preferences; research, coding, debugging and deployment use the assistant’s existing capabilities.

Derived from [dev-agent-skills](https://github.com/Neplich/dev-agent-skills) at [`67fd47d3ad2c`](https://github.com/Neplich/dev-agent-skills/commit/67fd47d3ad2c44b441e3b7c4c27cc87d4a595b5c), preserving Git history and the MIT license. The original library continues to support models that benefit from more detailed procedural guidance. This is an independent repository, without GitHub fork metadata.

## Skills

| Skill | Purpose |
| --- | --- |
| [human-writing](agents/product_manager/skills/human-writing/SKILL.md) | Chinese writing conventions |
| [spec-authoring](agents/product_manager/skills/spec-authoring/SKILL.md) | Specification and design templates |
| [release-management](agents/product_manager/skills/release-management/SKILL.md) | Changelog, site notes and GitHub releases |
| [e2e-testing](agents/qa/skills/e2e-testing/SKILL.md) | Persistent E2E cases and execution evidence |
| [security-review](agents/security/skills/security-review/SKILL.md) | Application, authorization, dependency and privacy references |
| [docs-maintenance](agents/docs/skills/docs-maintenance/SKILL.md) | Documentation facts, contracts and version anchors |
| [docs-site-bootstrap](agents/docs/skills/docs-site-bootstrap/SKILL.md) | VitePress assets, scripts and builds |
| [manual-gen](agents/docs/skills/manual-gen/SKILL.md) | Illustrated manuals from real interfaces |

## Install

### Codex

```text
Fetch and follow instructions from https://raw.githubusercontent.com/Neplich/h-level-model-skills/refs/heads/main/.codex/INSTALL.md
```

### Claude Code

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-product@h-level-model-skills
/plugin install h-level-qa@h-level-model-skills
/plugin install h-level-security@h-level-model-skills
/plugin install h-level-docs@h-level-model-skills
```

### Kimi Code

```text
/plugins install https://github.com/Neplich/h-level-model-skills
```

Choose the plugins you need. The Codex installer uses an independent `.h-level-model-skills/` mirror. Existing entries owned by the original library or another installation are skipped and reported; `--force` does not overwrite them. Updating this library does not remove the original library’s 37 skills.

Describe the task or name a skill. The `human-writing` preferences are intentionally retained. Formal specifications, persistent E2E records and security reviews are used only when relevant.

## Maintenance and provenance

[Architecture](docs/architecture.md) · [Migration](docs/migration.md) · [Codex installation](docs/README.codex.md) · [Contributing](CONTRIBUTING.md) · [Release procedure](docs/cookbook/release.md)

Metadata version `0.6.7` is inherited from the upstream baseline, not a release published by this repository. Historical changelogs describe upstream releases; the first independent release requires its own version decision.
