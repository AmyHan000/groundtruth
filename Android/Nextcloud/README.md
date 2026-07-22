# Nextcloud (Android) GroundTruth

- 源码仓库：https://github.com/nextcloud/android
- 分析对象：用户上传的源码压缩包固定快照
- 快照文件索引哈希：`cc549ae5011f223bff66b2270e2808618fc78ca750cae1647e2bdc2d5fea7b29`
- 源码索引文件数：1699
- 功能目录数：26
- 数据流数：26

## 证据规则

- `dataflows.json` 仅包含 `id` 与 `dataflow`；节点仅包含真实 `filePath`、`line`、`code`。
- 已排除 Markdown/README、测试、构建产物、生成目录，以及不属于该平台的原生实现。
- 权限清单仅用于辅助声明，不单独作为数据流执行节点。
- 同一应用内 ID 连续且唯一，并与 `statement.json` 一一对应。
- 自然语言声明位于 `statement.txt`，固定包含“1 我们如何收集和使用您的个人信息”和“2 设备权限调用”两节。
