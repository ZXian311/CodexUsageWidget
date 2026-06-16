# Codex Usage Widget

Codex Usage Widget is a lightweight Windows desktop widget that reads local Codex session logs and displays current usage limits in a clean floating interface.

It is designed for people who want a simple desktop view of Codex usage without repeatedly checking local logs or manually estimating reset times.

> This project is **not** an official Codex API client.

## Features

- Floating Windows desktop widget
- Displays both **5-hour** and **1-week** usage windows
- Shows **used percentage**, **remaining percentage**, and **reset countdown**
- Remaining quota color thresholds:
  - `< 10%` red
  - `10% ~ 20%` yellow
  - `>= 20%` green
- Light / dark / system theme modes
- Chinese / English language switching
- Pin-to-top toggle
- Manual refresh
- System tray integration with **Show** and **Exit**
- Minimize to tray
- Remembers the last window position
- Auto-start monitor when Codex is running

## How It Works

The widget reads the latest `rate_limits` data written by Codex under:

```text
%USERPROFILE%\.codex\sessions
```

If Codex changes its local session log format in the future, this project may need updates.

## Files

- `CodexUsageWidget.cs`  
  Native WPF widget source
- `CodexUsageWidgetMonitor.cs`  
  Native monitor source
- `CodexUsageWidget.ps1`  
  PowerShell widget implementation kept as reference / fallback
- `CodexUsageWidgetMonitor.ps1`  
  PowerShell monitor implementation kept as reference / fallback
- `Build-CodexUsageWidget.ps1`  
  Build script for the native executables
- `Generate-CodexUsageWidgetIcon.ps1`  
  Icon generation script
- `Install-AutoStart.ps1`  
  Installs startup integration
- `Uninstall-AutoStart.ps1`  
  Removes startup integration

## Requirements

- Windows
- Local Codex desktop/runtime environment
- Available local Codex session logs
- .NET Framework WPF runtime
- PowerShell for helper scripts

## Quick Start

### Run manually

Run:

```text
CodexUsageWidget.exe
```

or:

```text
Start-CodexUsageWidget.cmd
```

### Install auto-start

Run:

```powershell
powershell -ExecutionPolicy Bypass -File .\Install-AutoStart.ps1 -StartNow
```

This installs:

- a Startup-folder shortcut
- a user scheduled task for the monitor

The scheduled task helps keep the monitor alive more reliably across Codex restarts and Windows logins.

### Remove auto-start

Run:

```powershell
powershell -ExecutionPolicy Bypass -File .\Uninstall-AutoStart.ps1
```

## Privacy

This tool reads local Codex session logs from the current Windows user profile. It does not call an official Codex usage API.

## Repository Scope

This repository is intended to track source code and helper scripts. Packaged binaries, zip archives, local settings, and temporary runtime state should generally not be treated as the primary source of truth.

## Contact

For feedback, bug reports, or collaboration:

- Email: `ZXian311@gmail.com`

## License

MIT

---

# Codex 用量小组件

Codex 用量小组件是一个轻量级 Windows 桌面悬浮小组件，用于读取本地 Codex 会话日志，并以简洁界面显示当前用量限制信息。

它适合希望快速查看 Codex 用量状态的用户，不需要反复翻看本地日志，也不需要手动估算重置时间。

> 本项目**不是**官方 Codex API 客户端。

## 功能特性

- Windows 桌面悬浮小组件
- 同时显示 **5 小时** 与 **1 周** 两个用量窗口
- 显示 **已用百分比**、**剩余百分比** 和 **重置倒计时**
- 剩余额度颜色规则：
  - `< 10%` 为红色
  - `10% ~ 20%` 为黄色
  - `>= 20%` 为绿色
- 支持浅色 / 深色 / 跟随系统主题
- 支持中文 / 英文切换
- 支持置顶
- 支持手动刷新
- 支持系统托盘集成，包含 **Show** 和 **Exit**
- 支持最小化到托盘
- 记忆窗口上次停留位置
- 支持在 Codex 运行时自动监视并自动拉起小组件

## 工作方式

小组件会读取 Codex 在本地写入的最新 `rate_limits` 数据，目录为：

```text
%USERPROFILE%\.codex\sessions
```

如果未来 Codex 修改了本地会话日志格式，本项目可能需要同步更新。

## 文件说明

- `CodexUsageWidget.cs`  
  原生 WPF 小组件源码
- `CodexUsageWidgetMonitor.cs`  
  原生后台监视器源码
- `CodexUsageWidget.ps1`  
  作为参考 / 备用保留的 PowerShell 版本小组件
- `CodexUsageWidgetMonitor.ps1`  
  作为参考 / 备用保留的 PowerShell 版本监视器
- `Build-CodexUsageWidget.ps1`  
  原生可执行文件构建脚本
- `Generate-CodexUsageWidgetIcon.ps1`  
  图标生成脚本
- `Install-AutoStart.ps1`  
  安装自动启动
- `Uninstall-AutoStart.ps1`  
  卸载自动启动

## 运行要求

- Windows
- 可用的本地 Codex 桌面 / 运行环境
- 可读取的本地 Codex 会话日志
- .NET Framework WPF 运行环境
- PowerShell（用于辅助脚本）

## 快速开始

### 手动运行

运行：

```text
CodexUsageWidget.exe
```

或者：

```text
Start-CodexUsageWidget.cmd
```

### 安装自动启动

运行：

```powershell
powershell -ExecutionPolicy Bypass -File .\Install-AutoStart.ps1 -StartNow
```

这会安装：

- 启动文件夹快捷方式
- 当前用户的计划任务监视器

计划任务的作用，是在 Windows 登录后以及 Codex 重启场景下，更稳定地保持监视器存活。

### 卸载自动启动

运行：

```powershell
powershell -ExecutionPolicy Bypass -File .\Uninstall-AutoStart.ps1
```

## 隐私说明

本工具读取当前 Windows 用户目录下的本地 Codex 会话日志，不调用官方 Codex 用量 API。

## 仓库范围

这个仓库主要用于维护源码和辅助脚本。打包后的二进制文件、压缩包、本地设置以及临时运行状态文件，不应被视为主要维护对象。

## 联系方式

如有反馈、Bug 报告或合作交流需求，可通过以下方式联系：

- 邮箱：`ZXian311@gmail.com`

## 许可证

MIT

