# LocalSend 隐私数据流分析 (iOS)

## 源码信息
- **仓库地址**: https://github.com/localsend/localsend
- **Commit Hash**: b43b79504953001156f5c1728f7ab7df565dda4a

## 应用概述
LocalSend是一个开源的跨平台文件传输应用，支持在局域网内无需互联网即可传输文件。该应用基于Flutter开发，Android和iOS共享代码。

## 目录结构
```
iOS/LocalSend/
├── README.md
├── 首页/
│   └── 设备发现/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 发送页/
│   └── 文件选择/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
└── 接收页/
    └── 接收文件/
        ├── dataflows.json
        ├── statement.json
        └── statement.txt
```

## 隐私数据收集点总结

### 1. 首页 - 设备发现
- **设备型号**: 通过device_info_plus获取，用于局域网内设备识别
- **本地IP地址**: 通过network_info_plus和connectivity_plus获取，用于设备发现
- **网络接口列表**: 通过系统API获取，用于确定本机网络配置
- **设备型号**: 通过device_info_plus获取，用于设备识别
- **设备类型**: 通过device_info_plus获取，区分移动和桌面设备
- **证书指纹**: 本地生成，用于设备身份验证
- **协议版本**: 应用配置，用于协议兼容性检查
- **WebRTC信令服务器连接**: 通过rust库连接WSS服务器，用于P2P通信
- **私钥调试打印**: 调试模式下输出私钥信息（安全隐患）
- **RSA密钥对生成**: 通过basic_utils生成，用于设备身份验证
- **应用版本信息**: 通过package_info_plus获取，用于显示和兼容性检查
- **WebRTC密钥对生成**: 通过rust库生成，用于WebRTC安全通信
- **收藏设备列表存储**: 通过UserDefaults存储用户收藏的设备
- **WebRTC信令服务器配置存储**: 通过UserDefaults存储信令服务器配置
- **WebRTC STUN服务器配置存储**: 通过UserDefaults存储STUN服务器配置
- **设备别名生成和存储**: 本地生成并存储在UserDefaults
- **发现日志记录**: 通过logging库记录设备发现日志

### 2. 发送页 - 文件选择
- **剪贴板文本数据**: 通过系统剪贴板获取，用户主动选择发送
- **剪贴板图片数据**: 通过pasteboard获取，用户主动选择发送
- **剪贴板文件列表**: 通过pasteboard获取，用户主动选择发送
- **用户选择的文件**: 通过file_selector获取，用户主动选择
- **媒体文件**: 通过wechat_assets_picker获取，用户从相册选择
- **目录路径**: 通过file_selector获取，用户主动选择
- **用户输入文本**: 通过对话框获取，用户主动输入
- **已安装应用列表**: 通过device_apps获取，用户选择APK发送
- **HTTP日志记录**: 通过logging库记录HTTP请求/响应日志

### 3. 接收页 - 接收文件
- **接收的文件数据**: 从局域网设备接收，保存到本地
- **文件保存路径**: 本地配置，确定文件保存位置
- **发送者设备信息**: 从发送方获取，显示在界面上
- **接收历史记录**: 本地记录，存储在本地数据库
- **相册存储权限**: 通过gal插件保存到系统相册
- **缓存目录管理**: 通过path_provider管理缓存目录
- **HTTP日志记录**: 通过logging库记录HTTP请求/响应日志

## 使用的插件
- `device_info_plus`: 获取设备信息
- `network_info_plus`: 获取网络信息
- `connectivity_plus`: 监听网络变化
- `pasteboard`: 访问系统剪贴板
- `file_selector`: 文件选择器
- `wechat_assets_picker`: 媒体选择器
- `gal`: 相册访问
- `path_provider`: 路径获取
- `package_info_plus`: 获取应用版本信息
- `basic_utils`: RSA密钥对生成
- `device_apps`: 获取已安装应用列表
- `logging`: 日志记录
- `rust`: WebRTC和加密功能

## 隐私特点
1. **局域网通信**: 所有数据传输仅在局域网内进行，不经过互联网
2. **本地处理**: 设备信息、网络信息等均在本地处理，不上传到服务器
3. **用户控制**: 剪贴板访问、文件选择等均需用户主动触发
4. **透明性**: 所有数据收集点均有明确的用户交互触发
5. **最小化收集**: 仅收集功能必需的数据，如设备型号、IP地址等
6. **WebRTC支持**: 支持P2P通信，信令服务器仅用于建立连接
7. **调试日志**: 调试模式下会记录详细日志，生产环境不包含敏感信息

## iOS特殊说明
- iOS系统对剪贴板访问有更严格的隐私控制，iOS 16+会显示剪贴板访问提示
- iOS系统对应用间文件访问有更严格的沙盒限制
- iOS系统相册访问需要用户授权
- iOS使用UserDefaults替代SharedPreferences进行本地存储
- iOS权限声明使用Info.plist中的隐私描述字符串

