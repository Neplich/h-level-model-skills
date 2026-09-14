# 从 dev-agent-skills 派生

本库以 dev-agent-skills 的 `67fd47d3ad2c44b441e3b7c4c27cc87d4a595b5c` 为基线，保留提交历史和许可。GitHub 同账号 fork 请求返回原仓库，因此采用独立派生仓库，原仓库不作精简修改。

## 入口变化

37 个入口减少到 8 个：删除 19 个独立入口，15 个合并为 5 个，3 个保留。

| 处理 | 原入口 | 当前入口或去向 |
| --- | --- | --- |
| 保留 | human-writing | 原样保留写作偏好和参考 |
| 保留 | docs-site-bootstrap、manual-gen | 资产和方法保留，迁移页面契约引用 |
| 合并 | idea-to-spec、trd-gen | spec-authoring；保留 schema、字段和功能路径约定 |
| 合并 | changelog-gen、github-release-gen、release-notes-gen | release-management；按渠道加载参考 |
| 合并 | exploratory-tester、spec-based-tester、bug-analyzer、regression-suite | e2e-testing |
| 合并 | appsec-checklist、authz-reviewer、dependency-risk-auditor、privacy-surface-mapper | security-review |
| 合并 | formal-docs-sync、docs-audit | docs-maintenance |
| 删除入口 | pm-agent、engineer-agent、qa-agent、devops-agent、security-agent、docs-agent | README 负责目录；QA 用例资料迁入 e2e-testing，页面契约迁入 docs-maintenance |
| 删除入口 | competitive-brief、codebase-analyzer、debugger、feature-implementor、test-writer、delivery | 由助手现有能力和宿主约定承担 |
| 删除入口 | feature-catalog、github-reader、roadmap-gen | 功能目录约定进入 spec-authoring；查询与路线图直接完成 |
| 删除入口 | cicd-bootstrap、deployment-planner、env-config-auditor、incident-playbook-writer | 由助手结合实际环境完成 |

spec-authoring 将旧的生成、修订和校验小文件收敛为按交付物选择的模板，不保留通用流程路由。文档站的脚本、模板、测试和构建资产保持原样。

## 安装边界

新仓库、marketplace、插件名称和 Codex 镜像身份均独立。原库安装不被接管，同名 human-writing、docs-site-bootstrap 或 manual-gen 入口由安装器保留并报告。希望同时保留两套库时可选择不同项目安装范围；替换旧库入口需明确选择后单独处理。

本次改动不安装到个人环境，不创建发布标签，不发布 Release。`0.6.7` 和历史 changelog 是上游基线信息，后续按本库发布流程确定首个版本。
