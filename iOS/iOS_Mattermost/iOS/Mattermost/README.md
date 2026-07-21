# Mattermost Mobile (iOS) GroundTruth

- 平台：iOS
- 源码仓库：https://github.com/mattermost/mattermost-mobile
- 固定源码版本：`9a40cad748965717fe089456c0c192006d0396eb`
- 交付格式：每个具体功能目录包含 `dataflows.json`、`statement.json`、`statement.txt`。
- 证据约束：所有 `filePath` 均从该源码工程根目录开始；行号与 `code` 已按上述固定版本自动复核；未使用 README、Markdown 或测试文件作为数据流节点。

## 已标注页面与功能

- `登录/账号密码登录`：数据流 ID 1
- `频道/发送消息`：数据流 ID 2
- `附件/选择文件上传`：数据流 ID 3
- `附件/拍照上传`：数据流 ID 4
- `附件/相册上传`：数据流 ID 5
- `通话/麦克风通话`：数据流 ID 6
- `通知/注册推送令牌`：数据流 ID 7
- `安全/生物识别解锁`：数据流 ID 8
- `分享/分享书签链接`：数据流 ID 9
- `文件/下载附件`：数据流 ID 10
