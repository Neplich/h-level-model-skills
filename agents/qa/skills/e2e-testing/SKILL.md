---
name: e2e-testing
description: "用持久 E2E 用例和可追溯执行记录开展界面探索、行为验收、缺陷复现与回归，维护用例 ID、账号引用和证据格式。"
---

# 可复用 E2E 测试

复用宿主 harness 和已有用例。需要长期维护测试资产时，采用 [用例格式](references/e2e-case-format.md)，保持用例 ID、分支覆盖、执行入口和历次结果之间的关联。

按任务选择模式：

- 未知缺陷和用户旅程探索：[探索维度](references/exploration.md)。
- 已知要求的执行核对：[验收与结果状态](references/acceptance.md)。
- 观察到失败后的复现与记录：[缺陷记录](references/defects.md)。
- 修复后的原始用例和相邻路径验证：[回归范围](references/regression.md)。

账号只通过稳定 ID 出现在用例和报告中；需要持久保存用户提供的凭据时，使用宿主机制或 [本地凭据约定](references/e2e-credential-store.md)。

[结果报告](references/e2e-test-report.md) 分别记录 `pass`、`fail`、`blocked`；无法执行的场景不算通过。记录实际构建、环境和脱敏证据。普通单元测试编写无需使用这套 E2E 资产结构。
