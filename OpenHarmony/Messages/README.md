# Messages (OpenHarmony) GroundTruth

- 源码仓库：https://gitcode.com/openharmony/applications_mms
- 分析对象：用户上传的源码压缩包固定快照
- 快照文件索引哈希：`de071f5d260f9beb1512bd6b71bbf08f00460d78cf48679d0e3c4c319da517dc`
- 源码索引文件数：388
- 功能目录数：30
- 数据流数：30

## 证据规则

- `dataflows.json` 仅包含 `id` 与 `dataflow`；节点仅包含真实 `filePath`、`line`、`code`。
- 已排除 Markdown/README、测试、构建产物、生成目录，以及不属于该平台的原生实现。
- 权限清单仅用于辅助声明，不单独作为数据流执行节点。
- 同一应用内 ID 连续且唯一，并与 `statement.json` 一一对应。
- 自然语言声明位于 `statement.txt`，固定包含“1 我们如何收集和使用您的个人信息”和“2 设备权限调用”两节。
