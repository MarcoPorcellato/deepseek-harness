# Agent Note: Matryca Knowledge 仓库地图

Status: proposed

[English](2026-08-19-matryca-knowledge-repository-map.md) | 中文

## Problem

DeepSeek Harness 跨越插件、可运行组合、SDK、原生启动器、Vendored 源码、文档和仓库门禁。只列出文件而不说明所有权和证据路径，会扩大语料，却不会让系统更容易学习或验证。

## Proposal

为每个通过资格验证的上游 release 维护一个 Matryca 版本化集成分支。每个分支包含语义仓库地图、有序学习和测试路径、Matryca 投影约定、证据矩阵以及确切的上游源码固定点。让 DeepSeek Harness 中的源代码和包约定保持权威，通过明确允许列表接纳人工维护的 Markdown，并把每次审查解析到不可变 Git 提交。

版本化分支按职责组织导航，并链接到已有的包、子系统、实操手册、示例、SDK、原生、Vendoring 和 Agent Note 所属文档。默认投影排除生成目录、构建产物、本地索引、运行日志、凭据、Vendored 实现树和归档 Agent Notes。本地安装只保留最新资格验证分支的一份完整 checkout；较早分支和提交的来源信息保留在 Git 和 Matryca Knowledge 中，不保留重复 worktree。

## Alternatives considered

**只投影默认分支的文档。** 这会让源码 ref 保持简单，但会把上游镜像与 Matryca 所有的文档混在一起。版本化集成分支为源码 manifest 提供明确的审查目标，同时不更改 fork 镜像。

**把整个仓库导入 Matryca Knowledge。** 这会复制实现和生成数据，削弱源码所有权，并可能纳入运行数据或含密钥路径。允许列表保留人工维护的文档层。

**只在 Matryca Knowledge 中编写地图。** 这会把导航和来源规则从它们描述的源码中分离。将地图留在 DeepSeek Harness 中，可以让源码提交解释自己的投影，并让 Matryca registry 保持集成配置的角色。

**为每个上游 release 保留一份完整 checkout。** 这会简化离线比较，但会复制源码树和依赖。不可变 Git ref 和 Knowledge 来源信息能够以更低的本地存储成本保留所需历史。

## Acceptance criteria

- 分支在 `docs/matryca-knowledge/` 下包含双语导航层。
- 地图覆盖顶层仓库区域、包族、可运行路径、SDK/原生/Vendoring 层、文档所有权和证据层级，但不复制生成清单。
- 投影契约说明允许列表、排除项、不可变提交规则、分类和更新流程。
- 源码固定点命名不可变上游 release、Matryca 版本化分支、兼容性要求和回滚源码。
- 每个新的活动文档都有所需的中文对应文件和配对记录。
- 更改范围的文档和链接检查通过，最终 diff 不包含 `vendor/` 内容变化。
- 临时 worktree 通过干净状态和可达性检查后，本地安装只保留最新资格验证分支的一份完整 checkout。

## Risks

每个上游 release 都需要新的集成分支和经过审查的 Knowledge 提案。双语配对会增加维护工作，宽泛允许列表也可能随着包 README 变化而快速增长，因此生成目录和归档记录仍然排除。删除未经验证的 worktree 可能丢失本地工作；因此清理前必须确认状态干净，并且其确切 head 可通过保留的本地或远程 ref 到达。
