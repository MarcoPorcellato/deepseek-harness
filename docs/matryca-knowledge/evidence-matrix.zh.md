# 证据矩阵

[English](evidence-matrix.md) | 中文

本参考把 DeepSeek Harness 的声明映射到能够支持它的最小证据，以及发布或对外发表前需要的更强证据。

| 声明 | 首要证据 | 更强证据 | 负责来源 |
|---|---|---|---|
| 包可以通过类型检查且生命周期在本地安全 | 聚焦包测试和 `pnpm run typecheck` | 确切 head 的 CI 结果 | 包 README 和测试 |
| 插件存在于产品组合中 | Loader/config smoke 和 `--dump-config` 输出 | 通过发布产物的构建入口路径测试 | 配置档案、bundle 和示例 README |
| 回合对模型可见且可回放 | 无密钥快照加会话日志断言 | 针对真实提供者的 with-key smoke | [测试策略](../testing.md)和 session 包 |
| 工具正确改变外部世界 | 真实执行器、受控夹具和外部重新读取 | 验证文件、进程或协议状态的 with-key e2e | 工具包 README 和 e2e 套件 |
| Wire 或 SDK 契约成立 | JSON-RPC/ACP 回放或协议测试 | 构建运行时和 Python 包 smoke | SDK、ACP、Python 和示例 README |
| 隔离声明成立 | 目标平台上的聚焦原生或 sandbox 测试 | 平台 CI 和发布产物收据 | Native 和 sandbox README |
| 文档已同步 | `pnpm run doc-sync` 和 `git diff --check` | 从不可变源码提交生成的 Matryca 审查提案 | 本目录和 Matryca 源策略 |

## 收据字段

每个为学习或审查保留的证据项记录：

- 确切 Git head 以及分支或标签；
- 命令、测试选择器和退出状态；
- 平台、Node、pnpm、Python 以及相关工具版本；
- 运行是无密钥、有密钥、回放还是跳过；
- 产物、转录或外部世界观察路径；
- 失败、限制或覆盖缺口。

不要在投影语料中存储 API key、token、本地文件系统路径或未经审查的运行日志。成功的本地运行是该环境的证据，不是平台或发布声明。

## 解读结果

`PASS` 表示指定命令在确切 head 上产生了预期观察。`SKIP` 表示前置条件不可用，声明仍未被证明。`RUNNING`、历史输出、过时 head 或代理自报答案都不是资格结果。

Matryca 投影保留源文档和审查元数据。没有 head、范围和收据，测试结果不会被提升为永久事实。
