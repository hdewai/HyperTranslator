# Changelog

本项目的发行记录遵循 [Semantic Versioning](https://semver.org/)。

## [0.1.3] - 2026-08-19

### Added

- 新增 Tauri 2 设置页与 shadcn/ui Sonner 翻译通知，加载态原位更新为翻译结果。
- 新增源语言 `AUTO`/`ZH`/`EN` 与目标语言 `ZH`/`EN` 设置，默认目标语言为英文。
- 新增 `Shift + 方向键`、`Shift + Ctrl + 方向键`选区翻译支持。
- 新增最多三条的 FIFO 翻译结果队列，新通知从底部进入，顶部最旧通知先退出。

### Changed

- 使用 Tauri Toast 替代 Windows 系统通知，并修正弹窗宽高、右侧边框裁切、圆角和动态高度。
- 搜狗与 Bing 翻译接口改为轮询调用；当前接口失败后自动尝试下一个，全部接口失败后才显示错误。
- 构建产物统一放在 `dist/debug/` 与 `dist/release/`，移除旧 Win32/GDI 客户端构建入口。
- Release 构建改用隔离 staging 目录，并在目标程序运行时提前报告文件锁定错误。
- 托盘菜单精简为“设置”和“退出”；通知时长可选择 1–5 秒，默认 5 秒。

### Fixed

- 修复全局快捷键已注册但处理回调不执行的问题。
- 修复快速重复快捷键导致一次翻译显示多条通知的问题。
- 修复通知入队方向与 FIFO 语义不一致、动画高度被覆盖和滚动条闪烁问题。
- 修复键盘扩选后修饰键未完全释放导致 `Ctrl+C` 捕获失败的问题。

## [0.1.2] - 2026-08-01

### Fixed

- 修复浏览器网页中选中文本后按 `Win + Shift + Z` 偶发读取不到选中文本的问题。
- 改用更稳定的键盘输入注入流程，并放宽剪贴板等待窗口，提升浏览器复制检测成功率。

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

[0.1.3]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.3
[0.1.2]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.2
[0.1.1]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.1
[0.1.0]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.0
