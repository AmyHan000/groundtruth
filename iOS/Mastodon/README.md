# Mastodon for iOS 隐私数据流分析

## 项目信息
- **应用名称**: Mastodon for iOS
- **源码仓库**: https://github.com/mastodon/mastodon-ios
- **Commit Hash**: 5ed53676eb2da88c6f1a505ed376fc45b3af9701

## 应用简介
Mastodon是一个去中心化的社交网络客户端，允许用户在多个Mastodon服务器之间切换，浏览和发布帖子（Toots），关注其他用户，以及参与社交互动。

## 目录结构

```
Mastodon/
├── README.md
├── 首页/
│   └── 时间线浏览/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 发帖页/
│   ├── 发布帖子/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 上传媒体/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 个人主页/
│   └── 查看资料/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 设置页/
│   └── 账户设置/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 搜索页/
│   └── 搜索功能/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 通知页/
│   └── 查看通知/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 分享页/
│   └── 分享内容/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 小组件/
│   └── 关注者计数/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 通知服务/
│   └── 推送通知处理/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 打开扩展/
│   └── 网页链接处理/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 登录页/
│   └── 用户认证/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
└── 社交互动/
    └── 关注用户/
        ├── dataflows.json
        ├── statement.json
        └── statement.txt
```

## 主要功能模块
1. **首页/时间线浏览** - 浏览本地时间线、联邦时间线、全局时间线
2. **发帖页/发布帖子** - 创建新帖子，包含文本、媒体附件、投票等
3. **发帖页/上传媒体** - 上传媒体文件到服务器
4. **个人主页/查看资料** - 查看和编辑用户个人资料
5. **设置页/账户设置** - 管理账户设置、通知偏好等
6. **搜索页/搜索功能** - 搜索用户、帖子、标签等
7. **通知页/查看通知** - 查看关注、点赞、转发等通知
8. **分享页/分享内容** - 通过iOS分享扩展分享内容到Mastodon
9. **小组件/关注者计数** - iOS小组件显示关注者数量
10. **通知服务/推送通知处理** - 处理加密的推送通知
11. **打开扩展/网页链接处理** - 在Mastodon中打开网页链接
12. **登录页/用户认证** - 通过OAuth协议进行用户身份验证
13. **社交互动/关注用户** - 关注、取消关注其他用户

## 隐私数据收集点
### 1. 设备信息
- **User-Agent**: 包含应用版本信息
- **设备型号**: 用于界面适配

### 2. 网络信息
- **网络请求**: 与Mastodon服务器通信
- **缓存**: 本地缓存网络数据

### 3. 媒体文件
- **相册访问**: 用户选择图片/视频上传
- **相机访问**: 拍照上传
- **文件保存**: 保存图片到相册

### 4. 用户生成内容
- **帖子内容**: 用户发布的文本、媒体
- **个人资料**: 用户头像、昵称、简介等

### 5. 推送通知
- **加密通知**: 通过Apple推送服务接收加密通知
- **本地解密**: 使用私钥在本地解密通知内容
- **通知图标**: 从服务器下载通知图标到临时目录
- **通知计数**: 使用UserDefaults存储未读通知数量

### 6. 认证存储
- **Keychain访问**: 使用Keychain安全存储认证令牌
- **相册权限**: 保存图片到相册需要PHPhotoLibrary权限

### 7. 小组件
- **关注者数量**: 从服务器获取用户关注者数量
- **用户头像**: 从服务器下载用户头像

## 注意事项
- Mastodon是去中心化应用，数据主要存储在用户选择的服务器上
- 应用本身不收集位置信息、通讯录等敏感数据
- 媒体访问仅用于用户主动上传功能
- 所有网络通信都通过HTTPS加密
- Keychain用于安全存储认证令牌，确保数据安全
- 通知图标下载到临时目录，使用后自动清理
- 保存图片到相册需要用户授权PHPhotoLibrary权限