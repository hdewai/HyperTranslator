# Changelog

本项目的发行记录遵循 [Semantic Versioning](https://semver.org/)。

## [0.1.1] - 2026-07-31

### Changed

- 调整仓库跟踪规则，仅提交发行文档、提交模板与发布 workflow；发行版二进制程序仅通过 GitHub Release 分发。
- 调整发布 workflow：`main` 推送同步 Release 说明，`hyper-translator-v*` 临时分支推送上传发行版二进制。

## [0.1.0] - 2026-07-28

### Added

- 新增 Windows 10/11 全局划词翻译功能。
- 新增 `Win + Shift + Z` 全局快捷键。
- 新增中英文目标语言切换，默认目标语言为中文。
- 新增托盘菜单及系统通知。
- 新增空文本与非文本选区过滤。
- 新增剪贴板文本恢复机制。
- 新增后台翻译任务，保持托盘交互流畅。
- 新增独立的应用、托盘和通知图标资源。

[0.1.1]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.1
[0.1.0]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.0
