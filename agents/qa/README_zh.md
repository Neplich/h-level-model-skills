# E2E 测试与证据

本插件通过一个 `e2e-testing` 入口整合探索、行为验收、缺陷复现和回归。价值集中在持久用例、账号引用和可追溯执行记录。

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [English](./README.md)

## 快速信息

| 项目 | 详情 |
| --- | --- |
| 插件名称 | `h-level-qa` |
| Skills | 1 |
| 主要输入 | 用户旅程、验收要求、运行环境、现有 harness 与测试账号 |
| 主要产物 | 用例索引、稳定用例 ID、缺陷记录、执行结果与脱敏证据 |

## Skill 清单

| Skill | 适用场景 | 主要产物或资源 |
| --- | --- | --- |
| [e2e-testing](./skills/e2e-testing/SKILL.md) | 需要积累可复现用户旅程 | 探索、验收、缺陷与回归资料 |

## 能力选择

- 探索未知问题时选择探索维度，围绕实际用户旅程和界面状态采集证据。
- 已有要求时执行行为验收，把预期结果与实际结果对应起来。
- 发现缺陷后保存最小复现；修复后复用原始用例并覆盖相邻路径。

## 安装与使用

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-qa@h-level-model-skills
```

Codex 的个人级和项目级安装见 [安装指南](../../docs/README.codex.md)。从仓库根目录安装全部 8 个 Skill 到已选目标：

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

直接描述目标或通过宿主的 Skill 选择器调用，例如：

```text
使用 e2e-testing，探索首次注册流程，保存可复现缺陷。
使用 e2e-testing，回归结算修复，复用现有用例并记录未执行场景。
```

## 输入与产物组织

沿用项目已有 harness 和测试资产。需要长期维护时，稳定 ID 关联用例、执行入口、历次结果和证据，账号只以引用 ID 出现在提交材料中。

需要持久产物时沿用项目现有位置，或参考以下布局；只创建本次任务需要的文件：

```text
docs/qa/e2e/{feature}/
  TEST_SUITE.md
  FLOW_INDEX.md
  cases/TC-NNN-<slug>.md
  results/{build}/TC-NNN/{test-time}/result.md
  _reports/{build}/test-reports-{test-time}.md
```

## 结果核对

结果分别记录 `pass`、`fail` 和 `blocked`。报告注明构建、环境和实际执行入口，未运行的场景不计为通过。凭据使用宿主保护机制或本库的本地存储约定。

## 与其他能力组合

验收要求可来自 spec-authoring 生成的规格，也可直接来自用户、issue 或已有测试。需要用户手册时，可与 manual-gen 共享已核实的界面事实。

助手沿用当前任务范围和授权，按实际需要组合资料。其他插件的目录见 [仓库 README](../../README_zh.md)。

## 本地维护

能力源码位于本目录的 `skills/`。修改后同步说明、注册和 lockfile；检查方法见 [维护指南](../../docs/cookbook/maintain-skills.md)。
