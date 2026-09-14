# H-Level Model Skills

[English](README.md) · [简体中文](README_zh.md)

面向高自主能力模型的精简 Skill 库：4 个插件、8 个可直接使用的 Skill。保留可复用资产、专业格式和写作偏好，通用研究、编码、调试与部署由助手直接完成。

本项目派生自 [dev-agent-skills](https://github.com/Neplich/dev-agent-skills)，基线提交为 [`67fd47d3ad2c`](https://github.com/Neplich/dev-agent-skills/commit/67fd47d3ad2c44b441e3b7c4c27cc87d4a595b5c)，保留提交历史与 MIT 许可。原库继续服务需要更详细流程引导的模型。新库是独立仓库，GitHub 不显示 fork 关系。

## 能力目录

| Skill | 用途 |
| --- | --- |
| [human-writing](agents/product_manager/skills/human-writing/SKILL.md) | 中文写作偏好与文稿组织 |
| [spec-authoring](agents/product_manager/skills/spec-authoring/SKILL.md) | PRD、TRD、API、ADR 与测试规格模板 |
| [release-management](agents/product_manager/skills/release-management/SKILL.md) | Changelog、站内说明与 GitHub Release |
| [e2e-testing](agents/qa/skills/e2e-testing/SKILL.md) | 持久用例、账号引用与执行证据 |
| [security-review](agents/security/skills/security-review/SKILL.md) | 应用、授权、依赖和隐私检查表 |
| [docs-maintenance](agents/docs/skills/docs-maintenance/SKILL.md) | 文档事实、字段、映射与版本锚 |
| [docs-site-bootstrap](agents/docs/skills/docs-site-bootstrap/SKILL.md) | VitePress 资产、脚本和构建 |
| [manual-gen](agents/docs/skills/manual-gen/SKILL.md) | 真实界面的图文操作手册 |

## 安装

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

按需选择插件。Codex 安装器使用独立的 `.h-level-model-skills/` 镜像；遇到原库或其他安装的同名入口会跳过并报告，`--force` 也不会覆盖外部入口。升级本库不会删除原库的 37 个 Skill。

直接描述目标或点名 Skill。`human-writing` 的写作偏好被明确保留；默认不要求使用正式规格、E2E 记录或安全审查。

## 维护与来源

[Architecture](docs/architecture.md) · [Migration](docs/migration.md) · [Codex installation](docs/README.codex.md) · [Contributing](CONTRIBUTING.md) · [Release procedure](docs/cookbook/release.md)

当前元数据版本 `0.6.7` 继承自上游基线，不代表本仓库已发布该版本。上游历史发布记录保留在 changelog；本库首次发布需另行确定版本。
