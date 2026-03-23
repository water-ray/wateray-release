# Wateray Release

官网：[https://wateray.net/](https://wateray.net/)

Wateray 的公开发布仓库，用于分发已纳入公开发布流程的平台客户端安装包、版本说明与升级索引文件。
此 README 由发布流程自动更新。

## 当前稳定版本

- 版本：`1.6.1`
- 发布渠道：稳定版
- 当前公开发布平台：Windows（ZIP 整包）, Linux（ZIP / DEB / AppImage）, macOS（DMG 安装镜像）, Android（APK）
- Release 页面：[Wateray v1.6.1](https://github.com/water-ray/wateray-release/releases/tag/v1.6.1)
- 全部版本：[查看 Releases](https://github.com/water-ray/wateray-release/releases)

## 更新摘要
- 新功能：本次版本未记录独立新功能。
- 修复：修复拖拽问题；Ss混淆插件解析；修复linux监控功能
- 优化：优化git代码提交；优化进程图标；优化节点编辑/管理
- 兼容性说明：当前公开发布包包含：Windows（ZIP 整包）, Linux（ZIP / DEB / AppImage）, macOS（DMG 安装镜像）, Android（APK）。请按对应平台下载使用。

## 下载文件

### Windows（ZIP 整包）

- [Wateray-windows-v1.6.1.zip](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/Wateray-windows-v1.6.1.zip)：Windows ZIP 便携整包（16.64 MB，推荐下载）

### Linux（ZIP / DEB / AppImage）

- [Wateray-linux-v1.6.1.zip](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/Wateray-linux-v1.6.1.zip)：Linux ZIP 便携整包（18.52 MB，推荐下载）
- [wateray_1.6.1_amd64.deb](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/wateray_1.6.1_amd64.deb)：Linux Debian/Ubuntu 安装包（15.30 MB）
- [Wateray-linux-v1.6.1-x86_64.AppImage](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/Wateray-linux-v1.6.1-x86_64.AppImage)：Linux AppImage 便携包（18.00 MB）

### macOS（DMG 安装镜像）

- [Wateray-macos-v1.6.1.dmg](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/Wateray-macos-v1.6.1.dmg)：macOS 客户端 DMG 安装镜像（37.98 MB，推荐下载）

### Android（APK）

- [Wateray-Android-v1.6.1-arm64-release.apk](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/Wateray-Android-v1.6.1-arm64-release.apk)：Android arm64 APK 安装包（72.29 MB，推荐下载）
- [Wateray-Android-v1.6.1-x86_64-release.apk](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/Wateray-Android-v1.6.1-x86_64-release.apk)：Android x86_64 APK 安装包（75.97 MB）

## 附加文件

- [SHA256SUMS.txt](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/SHA256SUMS.txt)：发布文件校验值。
- [latest.json](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/latest.json)：机器可读版本摘要。
- [latest-github.json](https://github.com/water-ray/wateray-release/releases/download/v1.6.1/latest-github.json)：带 GitHub 下载地址的版本摘要。
- [本次版本说明](https://github.com/water-ray/wateray-release/releases/tag/v1.6.1)：查看完整 Release Notes。

## 说明

- 该仓库默认只保留公开发布所需文件，不包含源码与开发文档。
- 最终可下载平台以本 README 与对应 Release 附件为准。
- macOS 当前未使用 Network Extension，无法完全接管系统 DNS，可能出现 DNS 污染。
- macOS 当前安装包未签名，首次打开需用户手动确认；后续是否购买 Apple 开发者证书以完善签名与发布体验，再单独评估。
