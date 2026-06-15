Codex Usage Widget
==================

What it does
------------
- Shows a topmost desktop floating window with Codex usage from local Codex session logs.
- Displays short-window and long-window used/remaining percentages plus reset estimates.
- Starts automatically when Codex opens after you install the monitor.
- Supports light, dark, and system theme modes.
- Supports CN and EN language switching.
- Supports pin-to-top mode and a collapsible settings section.

Important limitation
--------------------
This is not an official Codex usage API. It reads the newest rate_limits object written in
local Codex session JSONL files under %USERPROFILE%\.codex\sessions. If Codex changes its
local log format, the script may need to be updated.

Files
-----
- CodexUsageWidget.exe: the floating window.
- Start-CodexUsageWidget.cmd: manual launcher.
- CodexUsageWidgetMonitor.exe: background monitor that starts the window when Codex.exe is running.
- Install-AutoStart.ps1: installs the monitor into the current user's Windows Startup folder.
- Uninstall-AutoStart.ps1: removes the Startup shortcut and stops the floating window.
- CodexUsageWidgetSettings.json: created on first settings change; stores theme, language, and pin state.
- `*.cs`: source code for the native executables.

Install
-------
1. Extract the folder somewhere permanent.
2. Right-click PowerShell, or open PowerShell in this folder.
3. Run:

   powershell -ExecutionPolicy Bypass -File .\Install-AutoStart.ps1 -StartNow

After that, the native monitor executable starts at Windows login and opens the floating
window whenever Codex is running.

Manual start
------------
Double-click Start-CodexUsageWidget.cmd.

Notes
-----
- The close button dismisses the widget for the current Codex session. It appears again the next time Codex is opened.
- Settings are stored in the same folder as the executables, so keep the files together.

Uninstall
---------
Run:

   powershell -ExecutionPolicy Bypass -File .\Uninstall-AutoStart.ps1
