# DeepSeek Harness 与 Matryca Knowledge

[English](README.md) | 中文

本目录是通过 Matryca Knowledge 学习 DeepSeek Harness 的导航层。

DeepSeek Harness 仓库仍然是源代码、包契约、测试、示例、运行时产物和决策记录的事实来源。Matryca Knowledge 接收经过审查且保留来源信息的 Markdown 文档投影；它不替代本仓库。

## 文档

| 文档 | 范围 |
|---|---|
| [仓库地图](repository-map.md) | 仓库的语义区域、所有权和权威文档位置 |
| [学习与测试路径](study-and-test-paths.md) | 从架构到可运行行为和证据的有序路线 |
| [投影契约](projection-contract.md) | Matryca Knowledge 的允许列表、排除项、来源规则和审查流程 |
| [证据矩阵](evidence-matrix.md) | 测试层级、入口路径、可观察输出和应保留的收据 |

## 使用这张地图

1. 先阅读[架构](../architecture.md)，了解插件组合、配置档案、代理循环、会话事件和能力接缝。
2. 使用[仓库地图](repository-map.md)选择负责的包组或运行时区域。
3. 沿着[学习与测试路径](study-and-test-paths.md)前进，直到真实入口路径产生可观察结果。
4. 按照[投影契约](projection-contract.md)和[证据矩阵](evidence-matrix.md)记录确切的源码提交和证据。

## 范围边界

这张地图记录关系和导航，不复制由下级文档负责的生成目录、包 API 声明、测试清单或实现细节。

Matryca 投影包含源清单选定的人工维护 Markdown。它排除生成报告、构建产物、凭据、运行日志、Vendored Cordis 源码副本以及归档 Agent Notes；除非经过审查的源文档明确链接到历史记录。

源清单会在清点和审查前把分支解析为不可变提交。因此投影可以归属于 Git 对象，而不是未经验证的工作树或可变本地路径。

## 相关源文档

- [架构](../architecture.md)
- [测试策略](../testing.md)
- [开发流程](../development.md)
- [包组](../../packages/README.md)
- [可运行示例](../../examples/README.md)
- [Agent Notes](../../.agents/notes/README.md)
