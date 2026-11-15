# Kirara_Media

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.5.0-blue" alt="Version">
  <img src="https://img.shields.io/badge/Platform-Android%2011%2B%20%7C%20iOS%2016%2B-3DDC84" alt="Platform">
  <img src="https://img.shields.io/badge/Kotlin-Multiplatform-7F52FF" alt="Kotlin Multiplatform">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-lightgrey" alt="License">
</p>

<p align="center"><a href="README.en.md">English</a> | 简体中文</p>

**Kirara Media 的手机客户端。** Kirara Media 是 Kirara_Server 上的影视媒体站；登录一次通行证，之后自动登录，片库、评论、社区与互动提醒都在这里。

Android 与 iOS 共用同一套业务代码，界面按平台各自呈现原生观感。

---

## 功能一览

| 能力 | 说明 |
| --- | --- |
| **媒体浏览与播放** | 片库、详情、播放与电脑端保持一致；播放时横屏自动进入全屏，退出全屏后视频继续播放。 |
| **一次登录** | 通行证登录后自动续期；用过的账号会被记住，密码从不保存。 |
| **令牌导入** | 扫桌面端的动态二维码，或在「设置 → 令牌管理器」手动录入；令牌加密保存在本机。 |
| **评论与社区** | 评论、回复、点赞、@ 好友与隐私提及；社区页、我的最近评论与收藏都在这里。 |
| **互动提醒** | 被 @、被回复、被点赞，以及催更被点赞或被管理员审批时收到提醒，点开可直达对应资源。 |
| **个人资料** | 头像支持拖动与双指缩放裁剪，昵称随时可改，所有页面立即更新。 |
| **外观** | 跟随系统、日间 / 暗夜模式与 48 色主题。 |
| **应用内更新** | Android 端下载后做 SHA-256 校验再覆盖安装；iOS 端只检查更新，换版本需重新侧载。 |

## Android 与 iOS 的差别

| 项目 | Android 11+ | iOS 16+ |
| --- | --- | --- |
| 安装包 | `Kirara_Media_vX.X.X.apk`，允许「安装未知来源应用」后直接安装 | `Kirara_Media_vX.X.X.ipa`，与 APK 同命名并配一份 `.sha256`；不上架 App Store，需要侧载 |
| 更新 | 应用内下载、校验后由系统安装器覆盖安装 | 只能检查更新，换版本要重新安装新 IPA |
| 互动提醒 | 退出应用后仍能收到 | 没有 APNs：应用完全退出后收不到，回到前台会立即补拉 |
| 全屏 | 旋转横屏自动进入页面级全屏 | iPhone 由原生沉浸实现（收起系统栏、隐藏底部导航、屏幕常亮）；iPad 支持元素全屏 |
| 后台与返回 | 系统返回键 / 手势；「设置 → 通知优化设置」可跳到厂商的电池 / 自启动页面 | 没有返回键与厂商保活设置，返回改用页面内控件与手势 |

## 系统要求

**Android**

- 系统：Android 11（API 30）及以上
- 内存：建议 4 GB 及以上
- 存储：安装包约 85 MB，另需预留 200 MB 以上缓存空间
- 无需 Google 服务框架，国产手机可以直接使用

**iOS**

- 系统：iOS 16.0 及以上，iPhone 与 iPad 通用
- 安装：仓库产出的是未签名 IPA，需要用你自己的 Apple ID 重签，或由维护者用含你设备 UDID 的描述文件签名后安装
- 免费 Apple ID 签出的描述文件 7 天过期，到期重签一次即可
- 日常安装与使用不需要 Mac，只有出包和改代码才需要 macOS + Xcode

**两端**

- 需要能连接 Kirara Server；观看视频建议使用 WiFi 或稳定网络

## 下载与安装

### Android

1. 在仓库 **Releases** 页下载最新安装包 `Kirara_Media_vX.X.X.apk`。
2. 允许「安装未知来源应用」后完成安装。
3. 启动后登录 Kirara_Server 通行证，再按下方「快速开始」链接令牌。
4. 之后在「设置 → 软件更新」里检查新版本，应用内下载、校验并覆盖安装。

> 自 0.9.3-beta 起统一使用正式签名，新版本可直接覆盖安装，登录状态、令牌与设置都会保留；只有签名不一致的旧调试包需要先卸载。新版本首次启动会清理之前下载的安装包。

### iOS（不上架 App Store）

发布页的 IPA 与 Android 同一套命名：`Kirara_Media_v<版本>.ipa` + 同名 `.sha256`。自行构建用 `bash iosApp/deploy-device.sh build`，产物在 `iosApp/build/device/`（`KiraraMedia-Release.ipa`；只要未签名包用 `unsigned` 子命令）。按手边的条件选一种装法：

| 方式 | 适合 | 做法 |
| --- | --- | --- |
| Xcode 直连 | 有 Mac 和 Xcode，手机能被 Xcode 识别 | 打开 `iosApp/iosApp.xcodeproj`，选设备后按 ⌘R，签名走自动管理。详见 [iosApp/README.md](iosApp/README.md) |
| 无线 OTA | 维护者已用含你设备 UDID 的描述文件签名 | 把 IPA、`manifest.plist` 与安装页放到同一个 HTTPS 目录，用手机 Safari 打开安装页 |
| Sideloadly / AltStore | 手上只有未签名 IPA | 用自己的 Apple ID 重签后装进手机 |

> 未签名 IPA 不能直接安装：苹果只允许签名与设备 UDID 匹配的应用运行。iOS 自 1.5.0 起与 Android 使用同一版本号，同版本重出包时只递增构建号。

## 快速开始

```
① 登录通行证  →  ② 链接令牌  →  ③ 打开媒体页
```

1. **登录通行证**：输入 Kirara_Server 账号密码，勾选「保存账号」，以后打开应用会自动进入。
2. **链接令牌**：在桌面端「令牌管理器」点开对应令牌的扫码按钮，用手机「设置 → 令牌管理器 → 扫码导入」扫描；也可以在手机上手动录入令牌。
3. **打开媒体**：进入「媒体」标签页，应用会自动完成登录并停在 Kirara Media 首页。

二维码约每 15 秒刷新一次，提示过期时等图案刷新后立刻重扫。

## 常用操作

- **评论区**：视频详情页右下角按钮展开；回复直接复用底部输入栏；@ 列表包含自己。
- **社区**：浏览首页分享并点赞，点「查看」跳回媒体页观看；「我的最近评论」汇总你发过的评论、回复与分享。
- **收藏**：详情页星标收藏，收藏页可展开预览图并直接播放。
- **互动**：导航栏绿点提示未读，支持单条已读、全部已读与全部清除。
- **设置**：外观与个性化、资源预览、评论区自动展开、数据管理、通知优化。

## 常见问题

<details>
<summary><b>应用内更新提示需要「安装未知应用」权限？</b></summary>

这是 Android 对非应用商店来源安装的正常限制，无法跳过。首次更新时在系统弹窗里允许一次即可，之后可在系统设置中随时关闭该权限。
</details>

<details>
<summary><b>退到后台一段时间就收不到提醒？</b></summary>

部分国产系统会限制应用的后台联网。到「设置 → 通知优化设置」，把「后台优化策略」设为「无限制」，并打开「自动启动」；这两项会按手机品牌跳到对应的系统页面。应用被系统回收后，消息最坏延迟约 15 分钟。
</details>

<details>
<summary><b>断网打开应用，为什么回到了登录页？</b></summary>

勾选「保存账号」后，启动时会自动尝试登录，没有网络时这一步必然失败，于是回到登录页并提示「网络请求失败，请检查网络连接」。登录凭据不会被清除，恢复网络后重新打开即可自动登录。
</details>

<details>
<summary><b>扫码导入令牌失败？</b></summary>

手机和桌面端要登录同一个 Kirara 账户，令牌只能导入到它所属的账户。二维码约每 15 秒刷新，提示「二维码已过期」时等桌面端刷新后立刻重扫，并保持桌面端扫码窗口打开。
</details>

<details>
<summary><b>iOS 为什么要重签？7 天过期怎么办？</b></summary>

苹果只允许签名与设备 UDID 匹配的应用运行，仓库提供的是未签名 IPA，需要用自己的 Apple ID 重签后才能安装。免费账号签出的描述文件 7 天过期，重新签一次即可；付费开发者账号签的包有效期更长。
</details>

<details>
<summary><b>数据存在哪里？怎么彻底重置？</b></summary>

数据保存在应用内部，令牌等敏感信息已加密，其它应用和文件管理器都读不到，卸载应用即全部清除。需要重置时，在「设置 → 数据管理」选择「清空全部数据」，它会连同登录页记住的账号与外观设置一起清掉，随后应用自动关闭。
</details>

## 相关文档

- [iOS 安装与出包](iosApp/README.md)
- [安卓版技术栈文档](app/docs/Kirara%20Media%20安卓版技术栈文档.md)
- [iOS 迁移路线与已知边界](app/docs/Kirara%20Media%20iOS%20迁移路线.md)
- 桌面端：[Kirara_Server_Studio](https://gitee.com/kiraramoe/kirara_server_studio)

## 许可证

本软件为闭源专有软件，保留所有权利（All Rights Reserved）。

未经授权，禁止对本软件进行反编译、分发、修改或再发布。软件使用的第三方开源组件版权归其各自作者所有。

## 致谢

- [Jellyfin](https://github.com/jellyfin/jellyfin)
- [Jetpack Compose](https://developer.android.com/jetpack/compose)
- [Compose Multiplatform](https://github.com/JetBrains/compose-multiplatform) / [Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform.html)
- [Coil](https://github.com/coil-kt/coil)
- [OkHttp](https://github.com/square/okhttp)

---

<p align="center">Made with ❤ by SenVenth AC</p>
