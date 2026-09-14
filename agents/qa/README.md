# E2E Testing and Evidence

This plugin brings exploration, acceptance, defect reproduction, and regression together in `e2e-testing`. It provides persistent cases, account references, and traceable execution records.

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [中文](./README_zh.md)

## Quick Facts

| Item | Details |
| --- | --- |
| Plugin | `h-level-qa` |
| Skills | 1 |
| Main inputs | User journeys, acceptance expectations, a running environment, existing harness, and test accounts |
| Main outputs | Case indexes, stable IDs, defect records, execution results, and sanitized evidence |

## Skills

| Skill | When to use | Main artifact or resource |
| --- | --- | --- |
| [e2e-testing](./skills/e2e-testing/SKILL.md) | Maintain reproducible user journeys | Exploration, acceptance, defect, and regression references |

## Choosing a Capability

- Use exploration dimensions for unknown defects in actual journeys and interface states.
- For known requirements, map expected behavior to observed results.
- Save a minimal reproduction for a defect, then reuse it and adjacent paths after a repair.

## Installation and Use

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-qa@h-level-model-skills
```

See the [Codex Guide](../../docs/README.codex.md) for personal and project installs. From the repository root, install all eight skills into the selected target:

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

Describe the goal or choose a skill through the host, for example:

```text
Use e2e-testing to explore first-time signup and save reproducible defects.
Use e2e-testing to regress the checkout fix, reuse existing cases, and record scenarios that did not run.
```

## Inputs and Artifacts

Reuse the project’s harness and test assets. For durable records, stable IDs connect cases, execution entries, run history, and evidence. Committed materials refer to accounts by ID.

For durable artifacts, use existing project locations or adapt this layout, creating only the files needed for the task:

```text
docs/qa/e2e/{feature}/
  TEST_SUITE.md
  FLOW_INDEX.md
  cases/TC-NNN-<slug>.md
  results/{build}/TC-NNN/{test-time}/result.md
  _reports/{build}/test-reports-{test-time}.md
```

## Verification

Record `pass`, `fail`, and `blocked` separately. Reports identify the build, environment, and actual entry point; scenarios that did not run are not passes. Store credentials through the host’s protected mechanism or the local-store convention.

## Combining Capabilities

Expectations can come from spec-authoring, a user request, an issue, or existing tests. Verified interface facts can also support manual-gen.

The assistant keeps the task’s scope and authorization while combining relevant references. See the [repository README](../../README.md) for other plugins.

## Local Maintenance

Skill sources live under `skills/`. Synchronize descriptions, registration, and the lockfile after changes; see the [maintenance guide](../../docs/cookbook/maintain-skills.md) for checks.
