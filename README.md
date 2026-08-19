# HyperTranslator

轻量、快速的 Windows 10/11 划词翻译工具。选中文本并按下全局快捷键，即可通过 Tauri Toast 查看翻译结果。

[![Telegram](https://img.shields.io/badge/Telegram-hdewai-26A5E4?logo=telegram&logoColor=white)](https://t.me/+F1DotFYPlfdlMmI9) [![GitHub](https://img.shields.io/badge/GitHub-Release-181717?logo=github&logoColor=white)](https://github.com/hdewai/HyperTranslator/releases) [![版本号](https://img.shields.io/github/v/release/hdewai/HyperTranslator?label=%E7%89%88%E6%9C%AC&logo=github)](https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.3)

## 赞助

## 仓库内容

本仓库只跟踪发行相关元数据与开源许可证：`README.md`、`CHANGELOG.md`、`LICENSE`、`.gitmessage` 和发布 workflow。发布版二进制程序通过 GitHub Release 分发，不提交到仓库 Code 区。

## 功能

- 使用 `Win + Shift + Z` 翻译当前选中文本
- 支持鼠标、`Shift + 方向键` 和 `Shift + Ctrl + 方向键`选区
- 源语言支持 `AUTO`、`ZH`、`EN`，默认自动识别
- 目标语言支持 `ZH`（中文）和 `EN`（英文），默认英文
- 搜狗与 Bing 按轮询顺序调用；当前接口失败时自动尝试下一个，全部失败后才显示错误
- 通过 Tauri + shadcn/ui Sonner 显示弹性翻译通知
- 通知最多堆叠三条，按 FIFO 从底部入队、顶部先出
- 长结果自动换行并增高，通知最多显示 5 秒
- 设置页可配置源语言、目标语言和通知时长
- 托盘菜单只包含设置与退出
- 捕获选区后恢复原剪贴板文本
- 单文件可执行程序，无需安装

## 使用方法

1. 从 GitHub Releases 下载并启动 `hyper-translator.exe`。
2. 在支持复制文本的程序中选中文字。
3. 按下 `Win + Shift + Z`。
4. 在屏幕右下角的翻译通知中查看结果；连续翻译时最多保留三条。
5. 右键托盘图标可打开设置或退出程序。

## 系统要求

- Windows 10 或 Windows 11
- 可用的网络连接

## 注意事项

- 如果 `Win + Shift + Z` 已被其他程序占用，启动时会显示提示。
- 对于以管理员权限运行的程序，HyperTranslator 可能也需要使用相同权限，才能读取其选中文本。
- Toast 窗口不会抢占焦点；如果结果没有出现，请确认应用仍在托盘运行。
- 在线翻译服务的可用性及响应结果可能随服务状态变化。
