---
type: Document
---
# 学习与测试路径

[English](study-and-test-paths.md) | 中文

这些教程把仓库地图转化为可观察的学习会话。它们假设使用 macOS 或 Linux 开发 shell，使用根 `package.json` 支持的 Node，并已通过 `pnpm install` 完成依赖安装。

## 路径 1：理解组合

1. 阅读 [Cordis 入门](../cordis-primer.md)，然后阅读[架构](../architecture.md)。
2. 检查[配置档案和 bundle](../architecture.md#profiles-and-bundles)，并使用 `pnpm dsh --profile headless --dump-config` 输出真实组合。
3. 阅读贡献目标配置行的包所属组 README。
4. 通过确认提供运行时服务的配置档案、bundle、补丁行和提供者来验证结果。

可观察结果是配置树，而不是因为包存在于磁盘上就断言插件已加载。

## 路径 2：跟踪一次模型回合

1. 阅读[回合流程](../architecture.md#turn-flow)、[会话日志](../architecture.md#session-log)和[代理生命周期](../agent-lifecycle.md)。
2. 从 `packages/core/agent-loop/`、`packages/core/session/`、`packages/core/system-prompt/` 和 `packages/llm/llm/` 开始。
3. 使用 `pnpm run test:snapshot` 运行无密钥快照，并检查一个场景的回放 JSONL 和预期输出。
4. 跟踪一个持久事件从追加到消息派生，以及一个实时事件从生产者到消费者。

可观察结果是可复现的转录，其中面向模型的输入可以从会话日志中重建。

## 路径 3：跟踪一个能力接缝

1. 阅读[能力接缝参考](../capability-seams.md)和[扩展食谱](../cookbook/extension-cookbook.md)。
2. 从[仓库地图](repository-map.md)选择一个族，然后识别其 Service Definition、提供者和消费者。
3. 阅读包 README 和负责的子系统页面，再阅读实现文件。
4. 运行覆盖注册、生命周期清理、策略和面向模型结果的最小包测试。

可观察结果是与提供者无关的契约，其中包含真实消费者和覆盖注册路径的测试。

## 路径 4：运行组合示例

1. 阅读[示例](../../examples/README.md)，然后选择 `headless-agent`、`acp-agent` 或 `jsonrpc-agent`。
2. 遵循所选示例 README，第一次运行保持默认组合不变。
3. 运行示例指定的无密钥快照或构建入口路径测试。
4. 如果有真实模型密钥，运行示例的 with-key smoke，并验证外部世界，而不是相信代理的自我报告。

可观察结果是通过示例中实际发布的同一组合产生的应用级转录或外部副作用。

## 路径 5：检查传输和隔离

1. 当问题跨越发行或安全边界时，阅读 [Python SDK](../../python/README.md)、[原生 README](../../native/README.md)和[Vendoring 流程](../../vendor/README.md)。
2. 检查 `packages/sdk/`、`packages/acp/`、`packages/sandbox/`、`native/landlock-run/` 和相关构建脚本。
3. 运行所属 README 指定的最小协议、构建产物或原生检查。
4. 记录平台、确切提交、启动器模式和产物路径。

可观察结果是绑定到特定平台的线级响应、构建运行时调用或隔离收据。

## 证据阶梯

按距离单元测试的远近递增使用证据：

1. 类型检查和聚焦单元测试建立局部类型和生命周期行为。
2. 覆盖率、快照和构建入口测试建立组合和持久化行为。
3. With-key e2e 建立与真实提供者和外部世界的交互。
4. 平台特定 CI 或发布产物建立本地 macOS 运行无法证明的声明。

每个保留的结果记录确切 Git head、命令、平台、依赖和运行时版本、退出状态以及产物或转录路径。跳过的、历史的或仅本地的结果不能作为发布资格证明。
