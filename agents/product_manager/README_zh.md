# 产品、规格与发布

本插件提供 3 个 Skill，保留规格模板、版本交付约定和中文写作偏好。它们可单独使用，也可组合到同一次设计、文档或发布任务中。

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [English](./README.md)

## 快速信息

| 项目 | 详情 |
| --- | --- |
| 插件名称 | `h-level-product` |
| Skills | 3 |
| 主要输入 | 需求、现有规格、代码、测试、版本标签、提交与 PR |
| 主要产物 | PRD/TRD/API/ADR、测试规格、发布内容与读者文稿 |

## Skill 清单

| Skill | 适用场景 | 主要产物或资源 |
| --- | --- | --- |
| [spec-authoring](./skills/spec-authoring/SKILL.md) | 长期维护或指定格式的规格 | 模板、状态字段与功能路径 |
| [release-management](./skills/release-management/SKILL.md) | 版本变更与发布准备 | Changelog、站内说明、GitHub Release |
| [human-writing](./skills/human-writing/SKILL.md) | 中文写作与文稿修订 | 清晰正文与文档组织 |

## 能力选择

- 需要维护正式规格时选择 `spec-authoring`，按产物读取 PRD、TRD、API、ADR 或测试规格模板。
- 准备某一版本的变更记录或发布内容时选择 `release-management`，共用一份可核实的版本范围。
- 编写或修订中文材料时选择 `human-writing`，保留术语、格式、实用细节和已有写作偏好。

## 安装与使用

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-product@h-level-model-skills
```

Codex 的个人级和项目级安装见 [安装指南](../../docs/README.codex.md)。从仓库根目录安装全部 8 个 Skill 到已选目标：

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

直接描述目标或通过宿主的 Skill 选择器调用，例如：

```text
使用 spec-authoring，为批量导出功能整理 API 契约与迁移方案。
使用 release-management，为下一个版本准备 changelog 和 Release 文案预览。
使用 human-writing，恢复安装指南的章节和操作细节。
```

## 输入与产物组织

正式规格优先采用宿主格式；本库默认格式提供文档状态、关联字段和稳定功能路径。发布资料从同一提交或标签范围派生，按渠道组织正文。

需要持久产物时沿用项目现有位置，或参考以下布局；只创建本次任务需要的文件：

```text
docs/pm/{feature}/PRD.md
docs/engineer/{feature}/TRD.md
docs/engineer/{feature}/API.md
docs/changelog/changelog-v{version}.md
```

## 结果核对

GitHub tag、prerelease 与 latest 分别核对。文案预览、草稿和正式发布是不同交付目标；版本 metadata 只记录实际版本与核对结果。

## 与其他能力组合

需要运行验收时可结合 E2E 插件；站内事实更新可结合文档插件。`human-writing` 可用于其他插件生成的中文材料。

助手沿用当前任务范围和授权，按实际需要组合资料。其他插件的目录见 [仓库 README](../../README_zh.md)。

## 本地维护

能力源码位于本目录的 `skills/`。修改后同步说明、注册和 lockfile；检查方法见 [维护指南](../../docs/cookbook/maintain-skills.md)。
