# 文档站与图文手册

本插件提供 3 个 Skill，分别处理 VitePress 站点资产、文档事实维护和基于真实界面的操作手册。它们可以服务已有文档集，也可以组合交付新站点。

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [English](./README.md)

## 快速信息

| 项目 | 详情 |
| --- | --- |
| 插件名称 | `h-level-docs` |
| Skills | 3 |
| 主要输入 | 代码、接口、数据库模型、运行界面、现有文档与版本证据 |
| 主要产物 | 文档站、当前事实页面、图文任务页、映射与验证结果 |

## Skill 清单

| Skill | 适用场景 | 主要产物或资源 |
| --- | --- | --- |
| [docs-site-bootstrap](./skills/docs-site-bootstrap/SKILL.md) | 初始化或更新内置 VitePress 站点 | 站点资产与 bootstrap manifest |
| [docs-maintenance](./skills/docs-maintenance/SKILL.md) | 同步或审计文档与实现 | 页面、映射、版本锚与检查结果 |
| [manual-gen](./skills/manual-gen/SKILL.md) | 依据真实界面编写操作手册 | 任务页、截图、结果与恢复方式 |

## 能力选择

- 站点初始化和资产升级选择 `docs-site-bootstrap`，保留宿主独立内容并核对重复运行结果。
- 产品、设计、API、数据库和运维事实更新选择 `docs-maintenance`；只读审计同样通过此入口。
- 需要真实步骤与截图的用户手册选择 `manual-gen`，按独立用户任务组织页面。

## 安装与使用

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-docs@h-level-model-skills
```

Codex 的个人级和项目级安装见 [安装指南](../../docs/README.codex.md)。从仓库根目录安装全部 8 个 Skill 到已选目标：

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

直接描述目标或通过宿主的 Skill 选择器调用，例如：

```text
使用 docs-site-bootstrap，为项目建立 public/internal 文档站。
使用 docs-maintenance，核对接口页面与当前路由和 schema 的一致性。
使用 manual-gen，更新账号设置手册，保留真实截图和异常恢复步骤。
```

## 输入与产物组织

内置站点支持 public/internal 构建、页面字段、导航、模板和版本数据。已有文档沿用宿主路径；页面移动时同步索引、引用、截图和相关 change-map。

需要持久产物时沿用项目现有位置，或参考以下布局；只创建本次任务需要的文件：

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

## 结果核对

`related_code` 与 change-map 帮助定位影响范围，内容结论仍需核对实现与测试。`last_verified_version` 表示实际核对过的版本，不能只因 metadata 检查通过就更新。

内置站点在 `docs/site/` 下提供以下验证命令，按修改范围运行：

```bash
npm run test:docs
npm run build:public
npm run build:internal
npm run check:affected -- --base <base-ref>
```

## 与其他能力组合

站内发布说明由产品插件的 release-management 处理。manual-gen 可以结合 E2E 的已验证旅程，中文页面可结合 human-writing。

助手沿用当前任务范围和授权，按实际需要组合资料。其他插件的目录见 [仓库 README](../../README_zh.md)。

## 本地维护

能力源码位于本目录的 `skills/`。修改后同步说明、注册和 lockfile；检查方法见 [维护指南](../../docs/cookbook/maintain-skills.md)。
