# Matryca Knowledge 投影契约

[English](projection-contract.md) | 中文

本参考定义如何把 DeepSeek Harness fork 纳入 Matryca Knowledge。它把源码所有权留在 Git 中，并使按提交审查投影语料成为可能。

## 权威性和身份

位于 [MarcoPorcellato/deepseek-harness](https://github.com/MarcoPorcellato/deepseek-harness) 的 Git 仓库拥有文档及其历史。专用文档分支是这张地图的工作源码；Matryca 源清单选择一个 ref，并在检出和清点前将其解析为不可变提交。

源记录由仓库 URL 和 source id 标识，而不是由本地检出路径标识。审查记录解析后的提交、选定路径、排除项、分类和内容哈希。

## 接纳集合

源清单接纳以下人工维护的 Markdown 族：

| 包含项 | 用途 |
|---|---|
| `README.md`、`AGENTS.md` | 仓库级导航和常驻指令 |
| `docs/**/*.md` | 架构、参考、食谱、用户指南和本地图 |
| `packages/**/README.md` | 包组和包契约 |
| `examples/**/README.md`、`apps/**/README.md` | 可运行组合和产品入口文档 |
| `python/**/README.md`、`native/**/README.md`、`vendor/**/README.md` | 发行、安全和 Vendoring 契约 |
| `.agents/notes/README.md`、`.agents/notes/AGENTS.md` | 活动决策记录规则 |
| `.agents/notes/{proposed,implemented,rejected}/**/*.md` | 仍具有未来决策价值的活动决策记录 |

清单排除生成目录和图、事件清单、Vendored 实现树、归档 Agent Notes、构建产物、快照、缓存、凭据和运行日志。排除项在包含模式之后应用，因此宽泛的文档 glob 不能重新纳入禁止的族。

## 审查流程

1. 将选定 ref 解析为提交并记录结果。
2. 在 Matryca 源工作区中检出该提交，不使用作者的工作树。
3. 仅清点清单接纳的文件，并拒绝含有未提交内容的选定文件。
4. 规范化记录、保留源路径、分类文档并生成内容寻址的提案。
5. 在应用或发布投影前审查提案和关系证据。

投影并不会因为检出成功就完成。审查必须确认源码 head、允许列表、排除项、记录和关系证据一致。

## 分类

架构、开发、测试、子系统、食谱和包契约页面按文档类型归为活动参考或教程。根目录和子树指令文件是规范的操作指南。Agent Notes 保留其生命周期分类；归档记录仍在默认投影之外。

地图不会把实现状态文字转换成知识事实。当前行为属于负责的源文档；决策理由属于活动 Agent Note。

## 更新规则

当此文档分支发生变化时，从新的确切提交重新生成 Matryca 提案。不要通过手工编辑 `knowledge/` 投影来修复源文档。如果分支被合并或默认源发生变化，更新 source ref 并重新生成提案，使来源归属于新的提交。

## 本地验证收据

请求审查前保留：

```sh
git status --short --branch
git rev-parse HEAD
git diff --check
```

收据必须标识仓库、分支、确切 head、选定的源 ref、清点结果、提案 id 以及任何跳过的质量配置。不得把凭据或机器本地路径作为知识内容写入。
