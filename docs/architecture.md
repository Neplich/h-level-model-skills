# 仓库架构

H-Level Model Skills 面向能够自主研究、实现和验证的模型，包含四个插件、八个 Skill。插件用于分发相关资料，不再提供角色导航 Skill。

| 插件 | Skill |
| --- | --- |
| h-level-product | human-writing、spec-authoring、release-management |
| h-level-qa | e2e-testing |
| h-level-security | security-review |
| h-level-docs | docs-maintenance、docs-site-bootstrap、manual-gen |

源码沿用 `agents/{category}/skills/{skill}/`，保留目录历史。`SKILL.md` 仅定义用途、必要约束和资料入口；模板、检查表及模式细节按需加载。`human-writing` 保留原有内容与偏好。

文档站页面契约的唯一源位于 `agents/docs/skills/docs-maintenance/references/frontmatter-contract.md`。`scripts/generate_shared_contracts.py` 将其复制到 release-management、docs-site-bootstrap 和 manual-gen，保证独立安装后仍能读取同一契约。旧的角色交接与完成记录生成副本已移除。

Claude Code 从 marketplace 安装四个插件。Codex 安装器复制 Agent 树到 `.h-level-model-skills/` 隐藏镜像，并通过相对软链暴露八个 Skill。Kimi manifest 注册四个现存目录。安装身份与原库隔离，同名外部入口保留并报告。

[迁移清单](migration.md) · [安装](README.codex.md) · [维护](cookbook/maintain-skills.md)
