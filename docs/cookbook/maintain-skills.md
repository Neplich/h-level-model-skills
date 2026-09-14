# 维护 Skill

维护原则是保留影响决策的专业约定和可复用资产。通用研究、编码、调试与交付方法不再作为独立 Skill。human-writing 是明确保留的偏好，不因助手已加载它而判定重复。

变更时同步入口、参考、四个插件的目录、marketplace、Kimi manifest 和 lockfile。文档站页面字段修改后运行生成器，同步三个独立使用它的 Skill。

```bash
uv run scripts/generate_shared_contracts.py --check
uv run scripts/check_repository_contract.py
uv run scripts/check_doc_contract.py
uv run --with pytest pytest agents/test_doc_contract.py scripts/test_generate_shared_contracts.py scripts/test_install_codex_skills.py scripts/test_check_repository_contract.py
git diff --check
```

修改文档站资产时还需执行其测试与 public/internal 构建。安装验证使用临时目标目录，不改个人安装。

维护分支通过 PR 交付。上游的分支保护、审批和发布设置不会自动复制到本仓库；只有核实后的配置才能写成现状。合并与发布使用维护者明确授权，合并默认 squash。
