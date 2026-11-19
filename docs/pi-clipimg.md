# Pi 剪贴板图片扩展

`extensions/clipboard_image.ts` 调用 `clipboard-image` 读取剪贴板图片，将其加入 Pi 的待发送列表；不修改输入内容，也不自动发送。图片保存在 `~/.pi/agent/media/clipboard_image/`，发送时作为图片加入模型上下文。

## 使用

- macOS：`Ctrl+V`；其他平台：`Alt+V`。也可使用 `/clipboard_image`。
- `/clipboard_image clear`：清空待发送列表。
- `/clipboard_image clear 1,3-5`：按序号移除待发送图片。

macOS Kitty 需配置 `map ctrl+v send_key ctrl+v`，让按键传给 Pi；可用 `map cmd+v paste_from_clipboard` 保留文本粘贴。其他终端需自行放行快捷键。若与 Pi 内置图片粘贴快捷键冲突，需在 `~/.pi/agent/keybindings.json` 中禁用 `app.clipboard.pasteImage`。

## 运行环境

本地模式调用 `PATH` 中的 `clipboard-image`（Windows 为 `clipboard-image.exe`）。安装方法见 [README.md](../README.md)。

如需通过 SSH 读取 Windows 桌面剪贴板，显式设置 Windows SSH 别名：

```bash
export WIN_SSH_HOST=windows
```

Windows 端需将 `clipboard-image.exe` 放入 `PATH`，将 `.win-launch.exe` 放在用户目录，并在桌面会话中运行 `.win-launch.exe --server`。可使用 MinGW 编译辅助程序：

```bash
x86_64-w64-mingw32-gcc -municode -mwindows -Os -s ../win-launch.c \
  -o .win-launch.exe -lshell32
```
