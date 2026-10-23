# 发布与维护更新

本仓库用于公开分发明语星辰。用户固定更新入口：

[manifest.json](https://github.com/CGM2026/mingyu-stars/releases/latest/download/manifest.json)

每个版本的安装包资产名固定为 **mingyu-stars.apk**，清单资产名固定为 **manifest.json**。不要求用户随版本重新填写地址。

## 首次发布 0.1.5-dev

1. 使用最终审核的 Android APK：application_id 为 com.changgeng.astro、version_name 为 0.1.5-dev、version_code 为 6；核对实际包内版本、签名和旧版覆盖兼容性。将上传副本命名为 mingyu-stars.apk。
2. 对这份最终上传文件计算完整 SHA256 和字节数。清单必须引用同一份 APK，不得沿用候选包的校验值。
3. 建立 tag 为 v0.1.5 的 Release 草稿，放入本版发布说明、APK、清单，以及与二进制对应的源码包、依赖来源和必要构建材料。源码包由源码维护线提供；仅给上游链接或分发仓自动源码压缩包不够。
4. 完成资产核对后，发布为 GitHub 正式 Release，并明确设为 Latest。**不要勾选 pre-release，也不要停在 draft**；名称和正文仍写“公开试用版”。版本名含 dev 不影响其作为正式 Release，产品也不因此宣称稳定。
5. 从匿名访问的公网入口下载清单与 APK，核对应用ID、版本、文件大小和 SHA256；确认 latest 解析到本次版本。再验证手机的检查、下载、校验及手动安装流程，按实际结果记录验收范围。

GitHub 官方说明：[Latest 资产链接](https://docs.github.com/en/repositories/releasing-projects-on-github/linking-to-releases)、[Latest Release API](https://docs.github.com/en/rest/releases/releases#get-the-latest-release)。Latest 不取草稿或预发布版本。

## 清单字段

| 字段 | 本版要求 |
|---|---|
| schema_version | 数字 1 |
| application_id | com.changgeng.astro |
| version_code | 数字 6 |
| version_name | 0.1.5-dev |
| apk_url | 本版本固定地址 https://github.com/CGM2026/mingyu-stars/releases/download/v0.1.5/mingyu-stars.apk |
| sha256 | 最终APK的64位十六进制SHA256 |
| size_bytes | 最终APK的实际字节数，整数 |
| notes | 简短中文更新说明，字符串 |

清单入口使用 latest，但清单内部 apk_url 使用固定 tag 的下载地址，避免用户读取旧清单期间 latest 切换，下载到另一个版本的 APK。

## 后续版本

- 每次提高 version_code，更新 version_name 与 tag；继续使用相同 application_id、签名、固定资产名和公开仓库。
- 先准备新草稿及完整资产，再发布并设为 Latest。保留旧版 Release 和它对应的源码；不要悄悄替换已发布 APK 后沿用旧校验值。
- 发布前检查清单、APK和源码包属于同一版本；公开包内不得包含个人案例、聊天导出、模型密钥、访问凭证、签名私钥或仅本机可用的更新地址。
- GitHub 可能将下载请求转到资产分发域名；应用实际检查和完整下载必须通过验收，不能只以网页能打开为准。该流程不要求用户登录 GitHub，不给应用配置仓库访问凭证。
- 若新版本有问题，保留旧资产供核对，并发布 version_code 更高的修复版本。Android 通常拒绝覆盖降级；仅将 Latest 指回旧版不能让已升级用户自动降级。

## 用户从旧版迁移

旧版需先手动覆盖安装一次公网更新版，之后自动使用内置公网来源；你自行配置的其他来源保留，可在“高级来源”中清空并保存以恢复默认。之后使用应用更新入口；安装权限和系统确认始终由用户操作。

## 许可与交付

README 和发布说明都区分 GPLv3 应用部分、AGPL-3.0-only 占星 core 及第三方许可。每个正式资产都应提供同版对应源码和构建材料。保留署名、修改记录、组件许可及依赖归属；发布文档不得把脚本协议测试写成真实模型或真机验收完成。
