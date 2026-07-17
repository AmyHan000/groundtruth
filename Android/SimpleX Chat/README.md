# SimpleX Chat Android - 隐私数据流分析

## 源码信息
- **仓库地址**: https://github.com/simplex-chat/simplex-chat
- **Commit Hash**: d492606f0
- **平台**: Android (Kotlin Multiplatform)

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
| INTERNET | 网络通信 |
| ACCESS_NETWORK_STATE | 监控网络状态 |
| CAMERA | QR码扫描和视频通话 |
| VIDEO_CAPTURE | 视频录制 |
| RECORD_AUDIO | 语音消息和通话 |
| MODIFY_AUDIO_SETTINGS | 音频设置 |
| POST_NOTIFICATIONS | 显示通知 |
| FOREGROUND_SERVICE | 后台消息接收 |
| WAKE_LOCK | 保持设备唤醒 |
| RECEIVE_BOOT_COMPLETED | 开机自启动 |
| REQUEST_IGNORE_BATTERY_OPTIMIZATIONS | 电池优化豁免 |
| WRITE_EXTERNAL_STORAGE | 文件存储 |

## 隐私特点
1. **端到端加密**: 所有消息和通话均使用端到端加密
2. **无中心服务器**: 使用去中心化的SMP协议
3. **本地存储**: 数据主要存储在本地加密数据库
4. **无追踪**: 不收集用户行为数据
5. **匿名支持**: 支持创建匿名资料（Incognito模式）
