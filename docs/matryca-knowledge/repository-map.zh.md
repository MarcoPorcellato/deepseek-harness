---
type: Document
---
# DeepSeek Harness 仓库地图

[English](repository-map.md) | 中文

本参考按职责映射仓库。它指向负责的权威文档，而不是维护每个文件的第二份清单。

## 顶层区域

| 区域 | 职责 | 权威入口 |
|---|---|---|
| `packages/` | 产品插件、能力接缝、消费者、提供者、SDK 和测试支持 | [包组](../../packages/README.md)及各组 README |
| `apps/` | 产品入口、CLI 和 Web 应用 | [CLI](../../apps/cli/README.md)和 [Web 测试参考](../../apps/web/tests/README.md) |
| `examples/` | 可运行的 Cordis 组合和协议示例 | [示例](../../examples/README.md) |
| `python/` | Python 客户端 SDK 和捆绑运行时发行版 | [Python SDK](../../python/README.md) |
| `native/` | 原生进程隔离源码和包 | [原生组件](../../native/README.md) |
| `vendor/` | 固定版本的 Cordis 源码和同步流程 | [Vendoring 策略](../../vendor/README.md) |
| `docs/` | 架构、子系统参考、食谱、用户指南、测试和生成参考 | [架构](../architecture.md)、[测试](../testing.md)和[食谱](../cookbook/extension-cookbook.md) |
| `.agents/` | Agent 工作流和活动决策记录 | [Agent Notes](../../.agents/notes/README.md) |
| `scripts/` | 仓库门禁、生成器、发布工具和快照基础设施 | 根目录[命令](../../AGENTS.md#commands)和脚本源文件 |
| `website/` | 选定双语文档的 VitePress 投影 | [网站配置](../../website/docs.ts) |
| `.github/` | CI、发布工作流、Issue 表单和仓库自动化 | [工作流目录](../../.github/workflows/) |
| `patches/` | 由包管理器应用的维护依赖补丁 | [补丁清单](../../package.json) |
| `assets/` | 文档或示例使用的小型仓库资源 | 使用它的文档或示例 |

## 运行时地图

运行时由 Cordis 插件树组成。修改包代码前阅读[架构](../architecture.md)；使用下列族定位下一份文档。

| 运行时关注点 | 包族 | 检查内容 |
|---|---|---|
| Agent 主干 | `packages/core/`、`packages/llm/`、`packages/context/`、`packages/compaction/` | 会话事件、提示组装、模型流和代理循环 |
| 能力 | `packages/fs/`、`packages/shell/`、`packages/subprocess/`、`packages/terminal/`、`packages/lsp/`、`packages/web/`、`packages/skill/` | Service Definition、提供者、面向模型的消费者和策略事件 |
| 持久状态 | `packages/session/`、`packages/session-query/`、`packages/storage/`、`packages/settings/`、`packages/credentials/`、`packages/attachment/`、`packages/spill/` | 只追加事件、投影、受限检索和持久化后端 |
| 协作 | `packages/interaction/`、`packages/goal/`、`packages/plan/`、`packages/todo/`、`packages/feedback/`、`packages/schedule/` | 人工决定、目标、计划、反馈和后续任务 |
| 委派与工作 | `packages/subagent/`、`packages/jobs/`、`packages/workflow/`、`packages/code-runtime/` | 子代理、后台工作、工作线程和代码执行 |
| 组合与安全 | `packages/bundle/`、`packages/preset/`、`packages/guard/`、`packages/sandbox/`、`packages/boot/`、`packages/identity/` | 配置档案、补丁层、生命周期保护、进程隔离和启动 wiring |
| 产品传输 | `packages/api/`、`packages/host/`、`packages/client/`、`packages/sdk/`、`packages/acp/`、`packages/hooks/` | HTTP、浏览器、JSON-RPC、ACP、Hook 桥接和进程外客户端 |

完整的包和 ctx-key 地图仍位于 [packages/README.md](../../packages/README.md)。生成的模块关系位于 [module-graph.md](../module-graph.md)；不要在此手工复制该图。

## 学习边界

源码地图只通过 README 和同步契约包含 vendored 目录。Vendored 实现是带有上游来源的导入源码副本，因此不属于 Matryca 投影。

生成目录、锁文件、构建产物、快照和本地索引仍是派生数据或运行数据。需要时研究其所属的生成器或测试；不要把生成文档当作底层契约的来源。
