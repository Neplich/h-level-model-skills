---
name: spec-authoring
description: "使用可复用 PRD、TRD、API、ADR 和测试规格模板编写或维护正式规格，统一文档状态、功能路径与关联字段。适用于需要持久规格或指定模板的任务。"
---

# 规格与设计模板

沿用宿主已有格式；需要本库默认格式时使用 [字段与路径约定](references/output-conventions.md)。模板按交付需要裁剪，文档状态表达成熟度，当前实现与目标方案分别表述。

| 交付物 | 参考 |
| --- | --- |
| 产品要求与验收 | [PRD](references/schemas/prd-schema.md) |
| 技术设计与迁移 | [TRD](references/schemas/trd-schema.md)、[设计提纲](references/technical-design.md) |
| 接口契约 | [API](references/schemas/api-schema.md) |
| 架构决策 | [ADR](references/schemas/adr-schema.md) |
| 测试规格 | [测试规格](references/schemas/test-spec-schema.md) |
| 长期功能索引 | [功能目录](references/feature-catalog.md) |

只读取本次交付涉及的模板。`feature_path` 与文档关联指向宿主的真实稳定位置；移动时同步引用。普通需求澄清、代码实现和小范围设计直接完成，无需为套用模板新增正式文档。
