---
name: docs-maintenance
description: "维护带 change-map、frontmatter 和版本锚的文档集，按代码变更同步页面或审计事实、链接、导航及 public/internal 构建。"
---

# 文档事实与契约维护

使用宿主已有页面结构和检查命令。内置 VitePress 站点采用 [页面字段](references/frontmatter-contract.md)，普通 Markdown 不强加这些字段。

- 更新产品、设计、API、数据库或运维事实时，读取 [同步方法](references/sync.md) 及受影响类型参考。
- 审查变更或发布一致性时，读取 [检查与版本规则](references/audit.md)。只读审计交付具体发现；授权修复包含修改和复查。

`change-map.yaml` 与 `related_code` 帮助定位影响面，内容结论仍核对实现与测试。同步正文、索引、导航和必要映射，保留不相关条目及扩展字段。

`last_verified_version` 表示实际核对过的版本；缺少锚点时使用 `unverified`。版本 metadata 的一致性检查不能代替内容核对。按实际影响运行宿主 checks，并查看 public/internal 页面的链接、图片和可见性。
