# WxDexInspector 插件仓库

这是 **WxDexInspector** 的官方在线插件商店数据源，应用内「设置 → 插件与扩展 → 打开插件商店」会读取本仓库的 [`plugins.json`](plugins.json)。

## 插件是什么

本商店的插件是**纯数据插件**（一份 JSON 特征/规则文件），安装后会被合并进应用的特征库，用于提升**静态识别**能力。插件不包含、也不执行任何代码。

目前支持三种类型：

| type | 说明 | payload 格式 |
|---|---|---|
| `hardening_pack` | 加固厂商特征包 | `{"rules":[{"vendor":"名称","so":["libxx.so"],"classes":["com/xx/Yy"]}]}` |
| `sdk_pack` | 第三方 / 广告 SDK 特征包 | `{"sdks":[{"name":"名称","prefixes":["com.xx."]}]}` |
| `hook_pack` | 微信 Hook 特征包 | `{"features":[{"id":"x","description":"说明","allStrings":[],"anyStrings":[],"classHints":[]}]}` |

## 收录范围（重要）

✅ 收录：静态特征/规则数据，用于增强加固识别、SDK 识别、微信特征匹配等**分析类能力**。

❌ 不收录：任何破解、脱壳、重打包、篡改、去广告、绕过授权/验证类内容。

提交插件请开 Issue；维护者会按上述范围审核。

## 已收录插件

| id | 类型 | 来源 |
|---|---|---|
| `hardening-pack-community` | 加固特征包 | 公开加固特征资料汇总（参考 ApkCheckPack 等开源项目） |
| `sdk-pack-common` | SDK 特征包 | 公开 SDK 类名前缀汇总 |
| `wx-hook-pack-extra` | Hook 特征包 | 微信公开字符串常量汇总 |

## 免责声明

本仓库仅汇总**公开可查的静态特征字符串**（so 文件名、类名前缀、日志字符串等），用于辅助逆向分析定位。特征可能随版本更新失效，请勿依赖单一来源。

上游参考项目：
- [moyuwa/ApkCheckPack](https://github.com/moyuwa/ApkCheckPack)（加固特征检查工具，40+ 厂商）
- [rednaga/APKiD](https://github.com/rednaga/APKiD)（APK 识别）
