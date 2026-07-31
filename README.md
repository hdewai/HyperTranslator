# HyperTranslator

轻量、快速的 Windows 10/11 划词翻译工具。选中文本并按下全局快捷键，即可通过系统通知查看翻译结果。

[![Telegram](https://img.shields.io/badge/Telegram-hdewai-26A5E4?logo=telegram&logoColor=white)](https://t.me/+F1DotFYPlfdlMmI9) [![GitHub](https://img.shields.io/badge/GitHub-Release-181717?logo=github&logoColor=white)](https://github.com/hdewai/HyperTranslator/releases) [![版本号](https://img.shields.io/github/v/release/hdewai/HyperTranslator?label=%E7%89%88%E6%9C%AC&logo=github)](https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.0)

## 赞助

## 仓库内容

本仓库只跟踪发行相关元数据：`README.md`、`CHANGELOG.md`、`.gitmessage` 和发布 workflow。发布版二进制程序通过 GitHub Release 分发，不提交到仓库 Code 区。

## 功能

- 使用 `Win + Shift + Z` 翻译当前选中文本
- 自动识别源语言
- 目标语言可切换为中文或英文，默认为中文
- 托盘菜单快速切换目标语言
- 通过系统通知显示翻译结果
- 空文本和非文本选区自动忽略
- 后台完成网络请求，不阻塞托盘交互
- 单文件可执行程序，无需安装

## 使用方法

1. 下载并启动 `hyper-translator.exe`。
2. 在支持复制文本的程序中选中文字。
3. 按下 `Win + Shift + Z`。
4. 在系统通知中查看翻译结果。
5. 单击或右键托盘图标可切换目标语言、查看说明或退出程序。

## 系统要求

- Windows 10 或 Windows 11
- 可用的网络连接

## 注意事项

- 如果 `Win + Shift + Z` 已被其他程序占用，启动时会显示提示。
- 对于以管理员权限运行的程序，HyperTranslator 可能也需要使用相同权限，才能读取其选中文本。
- 系统的“勿扰”模式或通知设置可能隐藏翻译通知。
- 在线翻译服务的可用性及响应结果可能随服务状态变化。
