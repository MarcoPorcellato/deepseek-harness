# Agent Note: Matryca Knowledge 仓库地图

Status: proposed

## Problem

DeepSeek Harness 跨越插件、可运行组合、SDK、原生启动器、Vendored 源码、文档和仓库门禁。只列出文件而不说明所有权和证据路径，会扩大语料，却不会让系统更容易学习或验证。

## Proposal

维护一个专用文档分支，其中包含语义仓库地图、有序学习和测试路径、Matryca 投影契约以及证据矩阵。让 DeepSeek Harness 中的源代码和包契约保持权威，通过明确允许列表接纳人工维护的 Markdown，并把每次审查解析到不可变 Git 提交。

文档分支按职责组织导航，并链接到已有的包、子系统、食谱、示例、SDK、原生、Vendoring 和 Agent Note 所属文档。默认投影排除生成目录、构建产物、本地索引、运行日志、凭据、Vendored 实现树和归档 Agent Notes。

## Alternatives considered

**只投影默认分支的文档。** 这会让源码 ref 保持简单，但无法在地图开发和审查期间携带投影契约。专用分支为源清单提供了明确的审查目标。

**把整个仓库导入 Matryca Knowledge。** 这会复制实现和生成数据，削弱源码所有权，并可能纳入运行数据或含密钥路径。允许列表保留人工维护的文档层。

**只在 Matryca Knowledge 中编写地图。** 这会把导航和来源规则从它们描述的源码中分离。将地图留在 DeepSeek Harness 中，可以让源码提交解释自己的投影，并让 Matryca registry 保持集成配置的角色。

## Acceptance criteria

- 分支在 `docs/matryca-knowledge/` 下包含双语导航层。
- 地图覆盖顶层仓库区域、包族、可运行路径、SDK/原生/Vendoring 层、文档所有权和证据层级，但不复制生成清单。
- 投影契约说明允许列表、排除项、不可变提交规则、分类和更新流程。
- 每个新的活动文档都有所需的中文对应文件和配对记录。
- 更改范围的文档和链接检查通过，最终 diff 不包含 `vendor/` 内容变化。

## Risks

如果 Matryca 清单继续解析 `master`，源码分支可能会与 fork 默认分支分离；registry 必须命名经过审查的 ref，并在分支变化后重新生成提案。双语配对会增加维护工作，宽泛允许列表也可能随着包 README 变化而快速增长，因此生成目录和归档记录仍然排除。
