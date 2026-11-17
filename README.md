# clipboard_image

Rust 命令行工具：读取本机剪贴板中的图片，编码为 PNG 并输出到标准输出或文件。支持 macOS 和 Windows。

```bash
clipboard_image --stdout > shot.png  # 输出 PNG 二进制
clipboard_image --output shot.png    # 保存到指定路径
```

编码后的 PNG 上限为 18 MiB。剪贴板无图片、图片超限或写入失败时，错误输出至标准错误，程序以非零状态退出。

## 安装与构建

在目标机器上安装：

```bash
cargo install --path .
```

也可交叉编译 Windows 版本（需安装对应 Rust target 和 MinGW 工具链）：

```bash
cargo build --release --target x86_64-pc-windows-gnu
```

读取剪贴板时须能访问目标机器的桌面会话。Pi 扩展的使用方法见 [pi-clipboard_image.md](pi-clipboard_image.md)。
