# OpenHarmony 联系人 GroundTruth

- 平台：OpenHarmony
- 源码仓库：https://gitcode.com/openharmony/applications_contacts
- 固定源码版本：`b9ab40d260a52afbe1ce63e08c9d0d8fc9efd6e2`
- 交付格式：每个具体功能目录包含 `dataflows.json`、`statement.json`、`statement.txt`。
- 证据约束：所有 `filePath` 均从该源码工程根目录开始；行号与 `code` 已按上述固定版本自动复核；未使用 README、Markdown 或测试文件作为数据流节点。

## 已标注页面与功能

- `权限管理/联系人与通话记录授权`：数据流 ID 1
- `联系人列表/读取联系人`：数据流 ID 2
- `联系人搜索/搜索联系人`：数据流 ID 3–4
- `联系人编辑/新增联系人`：数据流 ID 5
- `联系人编辑/更新联系人`：数据流 ID 6
- `联系人管理/删除联系人`：数据流 ID 7
- `通话记录/读取通话记录`：数据流 ID 8
- `拨号盘/拨打电话`：数据流 ID 9
- `SIM联系人/导入SIM联系人`：数据流 ID 10
