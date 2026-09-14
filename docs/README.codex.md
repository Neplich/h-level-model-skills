# H-Level Model Skills for Codex

安装八个直接可用的 Skill：human-writing、spec-authoring、release-management、e2e-testing、security-review、docs-maintenance、docs-site-bootstrap 和 manual-gen。

[完整安装步骤](../.codex/INSTALL.md) · [架构](architecture.md) · [迁移说明](migration.md)

## 安装

```text
Fetch and follow instructions from https://raw.githubusercontent.com/Neplich/h-level-model-skills/refs/heads/main/.codex/INSTALL.md
```

手动安装时选择已有授权的个人或项目范围，将仓库放在 Skill 根目录以外：

```bash
git clone https://github.com/Neplich/h-level-model-skills.git "$HOME/.agents/h-level-model-skills"
python3 "$HOME/.agents/h-level-model-skills/scripts/install_codex_skills.py" --target "$HOME/.agents/skills"
```

项目级将 `--target` 指向项目的 `.agents/skills`。安装器复制资料到 `<target>/.h-level-model-skills/`，过滤插件 manifest 和测试目录，生成根部相对软链。

## 更新与共存

更新 checkout 后重新运行安装命令。安装器只管理其独立镜像标记证明归属的镜像和软链，已退役的本库镜像入口会清理。其他 checkout、旧库镜像、真实目录和同名外部 Skill 保留并报告 `skipped`。

`--force` 可重建本库镜像，但遇到外部同名入口会在修改前报错。它不会迁移或删除原库的安装。若要切换两套库，请根据冲突报告明确选择要替换的入口；不要用全目录删除处理冲突。

本次派生未发布独立 tag，固定版本安装只能选择远端实际存在的本库标签。历史 changelog 不表示本仓库拥有对应 Release。
