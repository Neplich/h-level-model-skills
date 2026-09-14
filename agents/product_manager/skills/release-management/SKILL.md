---
name: release-management
description: "从同一版本范围维护 changelog、站内发布说明和 GitHub Release，处理标签、资产、预发布、latest 与版本元数据的一致性。"
---

# 版本交付

先确定目标仓库、标签或提交范围和本次交付渠道。共用一份已核实的变更证据，按渠道组织内容；只写用户需要的产物。

| 渠道 | 参考 |
| --- | --- |
| 开发者变更记录 | [提交范围与分类](references/changelog.md) |
| GitHub Release | [正文结构](references/release-outline.md)、[发布操作](references/github-release-workflow.md) |
| 内置 VitePress 站内说明 | [页面与版本元数据](references/site-release.md) |

发布操作沿用已有授权。草稿、正式发布和文案预览保持各自目标；需要额外权限时，先准备可审阅的正文、标签指向、资产及执行目标。

GitHub 的 tag、prerelease 和 latest 不是同一状态。按发布参考处理它们，每次实质写入前回读状态；遇到并发变化重新核对目标，出现新决策或权限缺口时停下相应写入。操作结果不确定时先回读再决定是否重试。

站内 `.meta/releases.json` 保留其他版本和扩展字段，`verifiedDocs` 只能声明实际核对过的页面版本。完成时给出所选渠道的产物、真实发布状态和验证结果。
