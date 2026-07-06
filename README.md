# Wateray Release

官网：[https://wateray.net/](https://wateray.net/)

Wateray 的公开发布仓库，用于分发已纳入公开发布流程的平台客户端安装包、版本说明与升级索引文件。
此 README 由发布流程自动更新。

## 当前稳定版本

- 版本：`2.2.0`
- 发布渠道：稳定版
- 当前公开发布平台：Windows（ZIP 整包）, Linux（ZIP / DEB / AppImage）, Android（APK）
- 本次未发布：macOS（DMG 安装镜像）（本次无更新，无发布版本）
- Release 页面：[Wateray v2.2.0](https://github.com/water-ray/wateray-release/releases/tag/v2.2.0)
- 全部版本：[查看 Releases](https://github.com/water-ray/wateray-release/releases)

## 更新摘要
- 新功能：本次版本未记录独立新功能。
- 修复：修复Windows编译
- 优化：增加从http头获得流量信息；增加tuic/snell代理协议，增加cert://订阅解析证书；开始2.2.0版本，增加snell,tuic协议
- 兼容性说明：当前公开发布包包含：Windows（ZIP 整包）, Linux（ZIP / DEB / AppImage）, Android（APK）。请按对应平台下载使用。

## 下载文件

### Windows（ZIP 整包）

- [Wateray-windows-v2.2.0.zip](https://github.com/water-ray/wateray-release/releases/download/v2.2.0/Wateray-windows-v2.2.0.zip)：Windows ZIP 便携整包（21.33 MB，推荐下载）

### Linux（ZIP / DEB / AppImage）

- [Wateray-linux-v2.2.0.zip](https://github.com/water-ray/wateray-release/releases/download/v2.2.0/Wateray-linux-v2.2.0.zip)：Linux ZIP 便携整包（21.99 MB，推荐下载）
- [wateray_2.2.0_amd64.deb](https://github.com/water-ray/wateray-release/releases/download/v2.2.0/wateray_2.2.0_amd64.deb)：Linux Debian/Ubuntu 安装包（17.89 MB）
- [Wateray-linux-v2.2.0-x86_64.AppImage](https://github.com/water-ray/wateray-release/releases/download/v2.2.0/Wateray-linux-v2.2.0-x86_64.AppImage)：Linux AppImage 便携包（21.15 MB）

### Android（APK）

- [Wateray-Android-v2.2.0-universal-release.apk](https://github.com/water-ray/wateray-release/releases/download/v2.2.0/Wateray-Android-v2.2.0-universal-release.apk)：Android 通用 APK 安装包（108.29 MB，推荐下载）

### macOS（DMG 安装镜像）

- 本次无更新，无发布版本。

# 订阅自定义证书配置

Wateray 支持在订阅内容中声明订阅分组内生效的代理服务端 CA 证书。证书规则只用于匹配代理节点的 TLS SNI / `server_name`，不会匹配最终访问的网站域名，也不会写入系统信任区。

## CERT URI

一行一条证书规则：

```text
CERT://+.example.com?type=ca&sha256=<spki-sha256>#<base64url-pem>
```

- `+.example.com` 匹配 `example.com`、`a.example.com` 和多级子域。
- `type` 当前只支持 `ca`。
- `sha256` 是证书第一张证书公钥 SPKI 的 SHA256，使用标准 base64；未转义的 `+` 会按 URL 规则处理，推荐 URL encode 或使用无 `+` 的值。
- fragment 是 PEM 内容的 base64url 编码，可不带 padding。

订阅中只要声明了证书，Wateray 会校验 PEM 和 SPKI SHA256。校验失败会阻止本次订阅拉取，避免节点静默降级到不安全 TLS 配置。

## Clash YAML

```yaml
wateray-certificates:
  - pattern: "+.example.com"
    type: ca
    sha256: "<spki-sha256>"
    certificate: |
      -----BEGIN CERTIFICATE-----
      ...
      -----END CERTIFICATE-----

proxies:
  - name: Demo
    type: tuic
    server: edge.example.com
    port: 443
    uuid: 00000000-0000-0000-0000-000000000000
    password: secret
    sni: node.example.com
```

## sing-box JSON

```json
{
  "wateray_certificates": [
    {
      "pattern": "+.example.com",
      "type": "ca",
      "sha256": "<spki-sha256>",
      "certificate": "-----BEGIN CERTIFICATE-----\n...\n-----END CERTIFICATE-----\n"
    }
  ],
  "outbounds": [
    {
      "type": "tuic",
      "tag": "Demo",
      "server": "edge.example.com",
      "server_port": 443,
      "uuid": "00000000-0000-0000-0000-000000000000",
      "password": "secret",
      "tls": {
        "enabled": true,
        "server_name": "node.example.com"
      }
    }
  ]
}
```

## Proxy INI

```ini
[Certificate]
+.example.com = ca, sha256=<spki-sha256>, certificate=<base64url-pem>
; 等价写法：+.example.com = type=ca, sha256=<spki-sha256>, pem=<base64url-pem>

[Proxy]
Demo = tuic, edge.example.com, 443, uuid=00000000-0000-0000-0000-000000000000, password=secret, sni=node.example.com
```

上例中的 `+.example.com` 在 INI 文件中应写成单个 `+` 开头；这里没有额外转义要求。

## SPKI SHA256

使用 OpenSSL 从 PEM 证书计算：

```powershell
openssl x509 -in ca.pem -pubkey -noout |
  openssl pkey -pubin -outform der |
  openssl dgst -sha256 -binary |
  openssl base64
```

将 PEM 编码为 base64url：

```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes("ca.pem")).TrimEnd("=") -replace "\+","-" -replace "/","_"
```

## 运行时行为

- 证书规则只在当前订阅分组内生效。
- 运行时按节点 TLS SNI / `server_name` 匹配规则；没有 SNI 时回退到节点服务器域名，回退值中的端口会被忽略，IP 节点不匹配 `+.domain`。
- 多条规则命中时，精确域名优先；否则后缀更长的规则优先。
- 命中后，Wateray 会把 PEM 写入本地应用数据目录，并在 sing-box outbound `tls` 中生成 `certificate_path`。
- 命中证书规则的节点会强制移除 `insecure`，并替换节点原有的 `tls.certificate` / `tls.certificate_public_key_sha256`，不会回退到跳过证书校验。
- Wateray 不安装系统信任证书，也不管理本地系统级证书防篡改。


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
