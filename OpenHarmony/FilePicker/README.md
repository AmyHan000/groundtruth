# OpenHarmony FilePicker 隐私数据流分析

## 项目信息
- **项目名称**: applications_filepicker
- **仓库链接**: https://gitcode.com/openharmony/applications_filepicker
- **Commit Hash**: 2255fe0ce2e7e42ac015844f0027836f0b66d35c

## 应用概述
OpenHarmony FilePicker 是系统级文件选择器应用，提供以下核心功能：
1. 文件选择器 (OPEN_FILE) - 允许第三方应用选择本地文件
2. 路径选择器 (CREATE_FILE) - 允许第三方应用选择保存路径并创建文件
3. 音频选择器 - 专门用于选择音频文件
4. 批量授权模式 - 支持批量文件权限授权

## 目录结构

```
FilePicker/
├── README.md
├── 文件选择页/
│   ├── 浏览文件/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 选择文件/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 路径选择页/
│   ├── 选择保存路径/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 保存文件/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
├── 音频选择页/
│   ├── 浏览音频/
│   │   ├── dataflows.json
│   │   ├── statement.json
│   │   └── statement.txt
│   └── 选择音频/
│       ├── dataflows.json
│       ├── statement.json
│       └── statement.txt
└── 批量授权页/
    └── 批量授权/
        ├── dataflows.json
        ├── statement.json
        └── statement.txt
```

```
文件选择页/
├── 浏览文件/        # 用户浏览本地文件系统
│   ├── dataflows.json
│   ├── statement.json
│   └── statement.txt
└── 选择文件/        # 用户选择文件并返回URI
    ├── dataflows.json
    ├── statement.json
    └── statement.txt

路径选择页/
├── 选择保存路径/    # 用户选择文件保存目录
│   ├── dataflows.json
│   ├── statement.json
│   └── statement.txt
└── 保存文件/        # 创建文件并返回URI
    ├── dataflows.json
    ├── statement.json
    └── statement.txt

音频选择页/
├── 浏览音频/        # 浏览本地音频文件
│   ├── dataflows.json
│   ├── statement.json
│   └── statement.txt
└── 选择音频/        # 选择音频文件并返回
    ├── dataflows.json
    ├── statement.json
    └── statement.txt

批量授权页/
└── 批量授权/        # 批量授权文件访问权限
    ├── dataflows.json
    ├── statement.json
    └── statement.txt
```

## 权限声明
本应用需要以下敏感权限：
- `ohos.permission.READ_MEDIA` - 读取媒体库
- `ohos.permission.WRITE_MEDIA` - 写入媒体库
- `ohos.permission.MEDIA_LOCATION` - 访问媒体位置信息
- `ohos.permission.FILE_ACCESS_MANAGER` - 文件管理器权限
- `ohos.permission.PROXY_AUTHORIZATION_URI` - URI代理授权

## 隐私数据类型
1. **文件路径/URI** - 本地文件的唯一标识符
2. **文件元数据** - 文件名、大小、修改时间、MIME类型等
3. **存储权限** - 对文件系统的读写权限
4. **调用方信息** - 第三方应用的包名、UID、Token
5. **设备信息** - 设备根目录信息
6. **账号管理信息** - 用于判断是否为隐私空间模式
7. **设备详细信息** - 设备ID、设备类型、品牌、制造商、ROM版本、产品型号
8. **IPC通信** - 跨进程文件管理服务通信
