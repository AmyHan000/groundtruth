# Nextcloud iOS GroundTruth

- 平台：iOS
- 源码仓库：https://github.com/nextcloud/ios
- 固定源码版本：`5013aa0587cb3413c49b058e677ac572b5344fff`
- 交付格式：每个具体功能目录包含 `dataflows.json`、`statement.json`、`statement.txt`。
- 证据约束：所有 `filePath` 均从该源码工程根目录开始；行号与 `code` 已按上述固定版本自动复核；未使用 README、Markdown 或测试文件作为数据流节点。

## 已标注页面与功能

- `登录/Nextcloud账号登录`：数据流 ID 1
- `文件/浏览文件列表`：数据流 ID 2
- `文件/下载文件`：数据流 ID 3
- `文件/上传文件`：数据流 ID 4
- `媒体/自动上传照片视频`：数据流 ID 5
- `扫描文档/扫描并暂存文档`：数据流 ID 6
- `通知/注册推送令牌`：数据流 ID 7
- `安全/Face ID或Touch ID解锁`：数据流 ID 8
- `系统分享/分享扩展上传`：数据流 ID 9
- `文件提供器/系统文件访问`：数据流 ID 10
