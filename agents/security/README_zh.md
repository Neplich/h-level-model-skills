# 安全与隐私审查

本插件提供一个 `security-review` 入口，按审查面加载应用安全、授权、依赖或隐私资料。适用于明确请求的安全和隐私审查。

> [!NOTE]
> [Architecture](../../docs/architecture.md) · [Documentation Guide](../../docs/AGENTS.md) · [English](./README.md)

## 快速信息

| 项目 | 详情 |
| --- | --- |
| 插件名称 | `h-level-security` |
| Skills | 1 |
| 主要输入 | 审查范围、代码、配置、解析依赖、身份权限与数据流 |
| 主要产物 | 代码证据、权限矩阵、依赖适用性与数据生命周期映射 |

## Skill 清单

| Skill | 适用场景 | 主要产物或资源 |
| --- | --- | --- |
| [security-review](./skills/security-review/SKILL.md) | 明确的安全或隐私审查 | 按审查面选择的检查表与发现 |

## 能力选择

- 应用输入、执行与输出边界使用 AppSec 参考，追踪可达路径和已有防护。
- 身份、对象权限和租户隔离使用授权参考，核对预期与实现矩阵。
- 依赖审查核对解析版本、公告和可达性；隐私审查追踪采集、共享、保留和删除。

## 安装与使用

```text
/plugin marketplace add Neplich/h-level-model-skills
/plugin install h-level-security@h-level-model-skills
```

Codex 的个人级和项目级安装见 [安装指南](../../docs/README.codex.md)。从仓库根目录安装全部 8 个 Skill 到已选目标：

```bash
python3 scripts/install_codex_skills.py --target /path/to/skills
```

直接描述目标或通过宿主的 Skill 选择器调用，例如：

```text
使用 security-review，核对管理后台导出的对象权限与跨租户访问。
使用 security-review，追踪账号删除后的个人数据、缓存和外部处理方。
```

## 输入与产物组织

每条发现保留位置、前提、已有防护、具体影响和修复方向。报告按实际审查面组织；宿主已有完整专用安全工作流时优先使用其验证能力。

## 结果核对

公告严重性与本系统实际影响分别说明。未验证路径记录证据缺口；法律合规结论另行核对适用地区的当前权威要求。普通功能修改不会因涉及登录或依赖而自动变成整库审计。

## 与其他能力组合

审查发现可以支持授权范围内的实现、回归和文档更新。需要持久运行证据时结合 e2e-testing，维护接口或数据处理说明时结合文档插件。

助手沿用当前任务范围和授权，按实际需要组合资料。其他插件的目录见 [仓库 README](../../README_zh.md)。

## 本地维护

能力源码位于本目录的 `skills/`。修改后同步说明、注册和 lockfile；检查方法见 [维护指南](../../docs/cookbook/maintain-skills.md)。
