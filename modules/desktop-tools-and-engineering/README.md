# 桌面工具与工程化

> [← 返回作品集](../../README.md)

围绕 Electron、Node.js、自动打包与持续发布，展示桌面产品交付能力。

## DeepSeek-Harness-Desktop（2026.08）

**技术栈：** Electron、Node.js、PowerShell、NSIS、GitHub Actions

将开源 DeepSeek Harness 封装为 Windows 桌面应用，用户无需单独安装 Node.js、DeepSeek Harness 或 Microsoft Edge，下载安装包即可使用。项目已获得 100+ GitHub Stars。

- 使用 Electron 自带 Node 启动和管理 `dsh` 服务，实现单实例锁、关窗停服与服务进程树清理
- 内置插件商城、插件启停、主题色和背景图自定义，并预装常用 Web UI 扩展
- 通过运行时裁剪移除多平台二进制、调试文件、类型声明和文档，将安装包从约 150 MB 降至约 99 MB
- GitHub Actions 每日跟踪上游版本、自动打包并发布 NSIS 安装包

**链接：** [源码](https://github.com/chnnasn/DeepSeek-Harness-Desktop) · [最新版本](https://github.com/chnnasn/DeepSeek-Harness-Desktop/releases/tag/v0.1.5-rc.1)

---

[← 返回作品集](../../README.md)