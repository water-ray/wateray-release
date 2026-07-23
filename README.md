# Wateray Release

官网：[https://wateray.net/](https://wateray.net/)

Wateray 的公开发布仓库，用于分发已纳入公开发布流程的平台客户端安装包、版本说明与升级索引文件。
此 README 由发布流程自动更新。

## 当前稳定版本

- 版本：`2.2.1`
- 发布渠道：稳定版
- 当前公开发布平台：Windows（ZIP 整包）, Linux（ZIP / DEB / AppImage）, Android（APK）
- 本次未发布：macOS（DMG 安装镜像）（本次无更新，无发布版本）
- Release 页面：[Wateray v2.2.1](https://github.com/water-ray/wateray-release/releases/tag/v2.2.1)
- 全部版本：[查看 Releases](https://github.com/water-ray/wateray-release/releases)

## 更新摘要
- 新功能：本次版本未记录独立新功能。
- 修复：本次版本未记录独立缺陷修复。
- 优化：优化健康检查；Fingerprint 和 allow-insecure证书安全；升级已完成 sing-box 升级到 v1.14.0-alpha.47，并修复启动代理时偶发弹出微软网页的问题。
- 兼容性说明：当前公开发布包包含：Windows（ZIP 整包）, Linux（ZIP / DEB / AppImage）, Android（APK）。请按对应平台下载使用。

## 下载文件

### Windows（ZIP 整包）

- [Wateray-windows-v2.2.1.zip](https://github.com/water-ray/wateray-release/releases/download/v2.2.1/Wateray-windows-v2.2.1.zip)：Windows ZIP 便携整包（22.02 MB，推荐下载）

### Linux（ZIP / DEB / AppImage）

- [Wateray-linux-v2.2.1.zip](https://github.com/water-ray/wateray-release/releases/download/v2.2.1/Wateray-linux-v2.2.1.zip)：Linux ZIP 便携整包（22.68 MB，推荐下载）
- [wateray_2.2.1_amd64.deb](https://github.com/water-ray/wateray-release/releases/download/v2.2.1/wateray_2.2.1_amd64.deb)：Linux Debian/Ubuntu 安装包（18.42 MB）
- [Wateray-linux-v2.2.1-x86_64.AppImage](https://github.com/water-ray/wateray-release/releases/download/v2.2.1/Wateray-linux-v2.2.1-x86_64.AppImage)：Linux AppImage 便携包（21.78 MB）

### Android（APK）

- [Wateray-Android-v2.2.1-universal-release.apk](https://github.com/water-ray/wateray-release/releases/download/v2.2.1/Wateray-Android-v2.2.1-universal-release.apk)：Android 通用 APK 安装包（112.89 MB，推荐下载）

### macOS（DMG 安装镜像）

- 本次无更新，无发布版本。

## 客户端界面截图

以下截图存放在仓库 `images/screenshots/` 目录，便于在 Release 页面之外快速了解客户端主要界面。

### Android 客户端

- 安卓客户端：代理运行与订阅节点列表
![代理运行中的安卓订阅页](images/screenshots/android-subscriptions.png)

- 安卓客户端：规则分组与节点池管理
![安卓规则与节点池页](images/screenshots/android-rules.png)

### Windows / Linux 桌面端

桌面端在 Windows 与 Linux 上保持相同的信息架构与主操作流，以下截图展示核心页面布局。

- Windows / Linux 桌面端：代理主页与启动控制
![桌面端代理主页](images/screenshots/desktop-proxy.png)

- Windows / Linux 桌面端：订阅列表与节点评分
![桌面端订阅页](images/screenshots/desktop-subscriptions.png)

- Windows / Linux 桌面端：规则管理与节点池
![桌面端规则页](images/screenshots/desktop-rules.png)

- Windows / Linux 桌面端：请求监控与规则建议
![桌面端监控页](images/screenshots/desktop-monitor.png)

## 说明

- 该仓库默认只保留公开发布所需文件，不包含源码与开发文档。
- 最终可下载平台以本 README 与对应 Release 附件为准。
