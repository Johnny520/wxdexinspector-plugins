# WxDexInspector 插件仓库

本仓库是 [WxDexInspector](https://github.com/Johnny520/WxDexInspector) 的**在线插件商店**数据源。

## 特性

- 全部为**数据插件**：只提供静态特征 / 规则数据（JSON），**不执行任何代码**，因此不存在任意代码执行风险。
- **不含**任何破解、脱壳、重打包、篡改、去广告、绕过授权类内容；仅用于**静态识别与信息展示**。

## 当前插件（7 个）

| 插件 | 类型 | 内容 |
| --- | --- | --- |
| hardening-pack-cn | 加固特征包 | 国内 60+ 家加固 / 壳厂商的 so 文件名与特征类名（腾讯乐固、360 加固、爱加密、梆梆、阿里聚安全、百度、娜迦、通付盾、网易易盾、几维、顶象 等） |
| hardening-global-pack | 加固特征包 | 海外 / 开源壳与保护方案（DexProtector、AppSealing、Arxan、APKiD 收录的其他 packer 等） |
| sdk-pack-ads | SDK 特征包 | 广告 / 统计 / 推送类 SDK 类名前缀（穿山甲、优量汇、百度联盟、快手、Mintegral、AppLovin、Unity Ads、友盟、神策、AppsFlyer、极光、个推、厂商推送 等） |
| sdk-pack-lib | SDK 特征包 | 支付、地图定位、IM、音视频、网络与序列化、图片、框架、热修复、插件化、数据库、风控安全、崩溃监控、云服务、语音与二维码等通用库 |
| wx-hook-core | Hook 特征包 | 微信核心：消息 CGI 接口、消息 XML 类型、联系人与标签、群聊、数据库表列名、聊天 UI、设置页、进程名、scheme、ID 前缀后缀 |
| wx-hook-feature | Hook 特征包 | 微信业务：小程序、支付 / 红包 / 钱包、视频号 / 直播、朋友圈、扫一扫、收藏、卡包、游戏、公众号、备份导出等 |
| wx-hook-environment | Hook 特征包 | 安全与环境检测：风控 CGI、反调试、Root / 模拟器检测、Xposed / Frida 相关字符串、设备绑定等静态特征 |

> 合计约 **570 条**特征 / 规则条目，覆盖 86 个加固厂商、270 个 SDK 包名前缀、234 条微信 Hook 特征。

## 目录结构

```
plugins.json                  # 商店索引（App 拉取入口）
payloads/
  hardening-pack-cn.json      # {"rules":[{"vendor":"..","so":[".."],"classes":[".."]}]}
  hardening-global-pack.json
  sdk-pack-ads.json           # {"sdks":[{"name":"..","prefixes":["com.x.y"]}]}
  sdk-pack-lib.json
  wx-hook-core.json           # {"features":[{"id":"..","description":"..","allStrings":[],"anyStrings":[],"classHints":[]}]}
  wx-hook-feature.json
  wx-hook-environment.json
```

## 匹配语义

- 加固：`so` / `classes` 均为**子串**匹配（zip 条目名或 DEX 类名拼接串），so 名统一小写。
- SDK：类名 `startsWith(prefix)`。
- Hook：对方法的字符串常量集合（小写）做 AND（`allStrings`）/ OR（`anyStrings`）判定。

## 镜像

App 会依次尝试：jsDelivr → raw.githubusercontent.com → ghproxy。

## 参与贡献

欢迎通过 Issue / PR 提交新的特征数据；请确保特征**真实存在且可静态匹配**，不要提交破解、脱壳、篡改类内容。
