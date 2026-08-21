---
type: Document
---
# Matryca 上游源码固定点

[English](upstream-sync.md) | 中文

本参考文档标识当前 Matryca 文档集成所使用的不可变上游 release。它记录来源和兼容性要求，但不改变上游所有权，也不暗示官方认可。

## 当前源码

| 字段 | 值 |
|---|---|
| 官方仓库 | [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) |
| 官方 release | [`dsh-v0.1.0-rc.8`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.0-rc.8) |
| 官方提交 | `141eb6fef83422698aef7a981029e843e8161534` |
| fork 镜像 | `MarcoPorcellato/deepseek-harness` 的 `master` 分支 |
| Matryca 集成分支 | `matryca/dsh-v0.1.0-rc.8-r1` |
| Matryca Knowledge source id | `deepseek-harness` |
| 已审查源码 ref | `matryca/dsh-v0.1.0-rc.8-r1`，在清点前解析为确切提交 |

## 所有权

官方仓库拥有运行时行为、包约定、release 产物和上游历史。本 Matryca 版本化分支增加此目录下的导航、证据和投影文档，以及 Matryca Knowledge 要求的已审查 OKF 元数据。

fork 的 `master` 分支仍然是官方上游的 fast-forward 镜像。Matryca 集成分支不会建立新的上游 release 或兼容性承诺。

## 运行时兼容性

rc.8 release 声明其 SQLite 存储格式与 rc.7 不兼容。资格验证使用一次性 DSH home，绝不原地打开操作员拥有的 rc.7 数据。任何数据迁移都需要单独的备份、迁移计划和运行时收据。

“DeepSeek Harness”用于描述上游项目及本 fork 与它的关系。Matryca 的命名和宣传必须遵守上游[品牌使用指南](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.1.0-rc.8/BRAND_GUIDELINES.md)，不得暗示认可、合作或授权。

## 更新流程

1. 解析不可变的官方 release tag，并记录其确切提交。
2. 从该提交构建新的 Matryca 版本化集成分支，不重写较早的集成分支。
3. 重新应用 Matryca 文档和 OKF 适配，并通过所属生成器重新生成每个受影响的派生文档。
4. 针对确切集成提交运行源码文档、OKF 和一次性运行时检查。
5. 更新 Matryca Knowledge 源码 ref，并通过受管提案工作流重新生成其已审查投影。

## 回滚

保留的 rc.7 文档源码是 `docs/matryca-knowledge-map` 分支的 `6d2cc057338c412500c82729d746422615d2fe0f`。回滚会选择该确切源码并重新生成 Knowledge 提案；它不需要第二份完整本地 checkout，也不需要手工编辑 `knowledge/`。
