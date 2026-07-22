# SimpleX Chat iOS - 隐私数据流分析

## 源码信息
- **仓库地址**: https://github.com/simplex-chat/simplex-chat
- **Commit Hash**: d492606f0
- **平台**: iOS (Swift + Haskell Core)

## 目录结构
```
SimpleX Chat/
├── README.md
├── 首页/
│   └── 消息列表/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 聊天页/
│   ├── 发送消息/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   ├── 接收消息/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   ├── 发送图片视频/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   ├── 语音通话/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 视频通话/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 设置页/
│   ├── 个人资料/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   ├── 通知设置/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   ├── 隐私设置/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 网络设置/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
└── 新用户引导/
    ├── 创建资料/
    │   ├── dataflows.json
    │   ├── statement.json
    │   └── statement.txt
    └── 选择通知模式/
        ├── dataflows.json
        ├── statement.json
        └── statement.txt
```

## 权限汇总
| 权限 | 用途 |
|------|------|
| NSCameraUsageDescription | QR码扫描和视频通话 |
| NSMicrophoneUsageDescription | 语音消息和通话 |
| NSPhotoLibraryUsageDescription | 选择图片/视频 |
| UIBackgroundModes.remote-notification | APNs推送通知 |
| UIBackgroundModes.fetch | 后台消息获取 |
| UIBackgroundModes.audio | 通话音频 |
| UIBackgroundModes.voip | VoIP通话 |

## 隐私特点
1. **端到端加密**: 所有消息和通话均使用端到端加密
2. **无中心服务器**: 使用去中心化的SMP协议
3. **本地存储**: 数据主要存储在本地加密数据库
4. **无追踪**: 不收集用户行为数据
5. **匿名支持**: 支持创建匿名资料（Incognito模式）
6. **Keychain安全存储**: 敏感数据（如设备令牌）存储在Keychain中
