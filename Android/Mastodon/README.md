# Mastodon for Android 隐私数据流分析

## 源码信息

- **GitHub仓库**: https://github.com/mastodon/mastodon-android
- **Commit Hash**: ddfa184f

## 应用概述

Mastodon是一个去中心化的社交网络客户端，允许用户连接到各种Mastodon实例服务器。该应用注重隐私保护，使用OAuth PKCE进行认证，不收集设备信息或位置数据。

## 目录结构

```
Mastodon/
├── README.md
├── 首页/
│   ├── 时间线浏览/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 发现内容/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 登录注册/
│   └── OAuth登录/
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
│   ├── 查看资料/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 编辑资料/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 通知页/
│   └── 接收通知/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 搜索页/
│   └── 搜索功能/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
└── 设置页/
    └── 用户偏好/
        ├── dataflows.json
        ├── statement.json
        └── statement.txt
```

## 权限分析

### 声明的权限

| 权限 | 用途 | 必要性 |
|------|------|--------|
| INTERNET | 网络通信 | 必需 |
| FOREGROUND_SERVICE | 前台服务（音频播放） | 必需 |
| FOREGROUND_SERVICE_MEDIA_PLAYBACK | 媒体播放 | 必需 |
| VIBRATE | 振动反馈 | 可选 |
| WRITE_EXTERNAL_STORAGE | 保存媒体文件（Android 9及以下） | 可选 |
| POST_NOTIFICATIONS | 显示通知（Android 13+） | 可选 |
| C2D_MESSAGE | Google Cloud Messaging | 推送通知必需 |
| com.google.android.c2dm.permission.RECEIVE | 接收推送 | 推送通知必需 |

### 未声明的敏感权限

- ACCESS_FINE_LOCATION / ACCESS_COARSE_LOCATION（位置信息）
- READ_CONTACTS / WRITE_CONTACTS（联系人）
- READ_CALL_LOG（通话记录）
- READ_SMS / SEND_SMS（短信）
- CAMERA（相机）
- RECORD_AUDIO（麦克风）

## 隐私特性

### 正面特性

1. **不收集设备信息**: 应用仅在User-Agent头中发送应用版本号，不收集设备型号、制造商、IMEI等信息
2. **不收集位置信息**: 没有位置相关权限，不收集地理位置数据
3. **不收集联系人**: 没有联系人权限，不访问通讯录
4. **本地存储**: 用户偏好设置存储在本地SharedPreferences，不传输到服务器
5. **加密推送**: 使用VAPID密钥对推送通知进行端到端加密
6. **OAuth PKCE**: 使用Proof Key for Code Exchange增强认证安全性

### 数据流向

1. **服务器通信**: 所有数据通过HTTPS与用户选择的Mastodon实例服务器通信
2. **认证令牌**: OAuth访问令牌存储在本地SQLite数据库，仅用于API认证
3. **媒体文件**: 用户主动上传的媒体文件发送到服务器，不访问设备其他文件
4. **推送通知**: 通过Google FCM接收推送，但推送内容使用VAPID加密
5. **搜索历史**: 用户搜索关键词存储在本地SQLite数据库，仅用于显示历史记录
6. **通知权限**: Android 13+需要显式请求POST_NOTIFICATIONS权限
7. **存储权限**: 保存二维码和媒体文件需要WRITE_EXTERNAL_STORAGE权限（Android 9及以下）
8. **条码扫描**: 使用Google ML Kit进行二维码扫描，需要安装相应模块

## 技术实现

### 网络层

- 使用OkHttp进行HTTP请求
- HTTP缓存大小为10MB
- 所有API请求使用Bearer令牌认证

### 存储层

- SQLite数据库存储会话和账户信息
- SharedPreferences存储用户偏好
- 文件缓存存储HTTP响应

### 推送通知

- 使用Google Cloud Messaging (FCM)
- VAPID (Voluntary Application Server Identification) 加密
- 每30天刷新推送令牌

## 总结

Mastodon for Android是一个隐私友好的社交网络客户端，严格遵循最小权限原则，不收集不必要的用户数据。所有通信都通过HTTPS加密，推送通知使用VAPID进行端到端加密。用户数据主要存储在本地，只有用户主动分享的内容才会发送到服务器。
