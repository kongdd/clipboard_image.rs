# system-media

[![CI](https://github.com/kongdd/system-media.rs/actions/workflows/ci.yml/badge.svg)](https://github.com/kongdd/system-media.rs/actions/workflows/ci.yml)
[![codecov](https://codecov.io/gh/kongdd/system-media.rs/graph/badge.svg)](https://codecov.io/gh/kongdd/system-media.rs)

两个 Rust 命令行工具：`clipboard-image` 将剪贴板图片导出为 PNG，`audio-player` 播放本地 MP3 文件。

```bash
clipboard-image --stdout > shot.png  # 输出 PNG 二进制
clipboard-image --output shot.png    # 保存到指定路径
audio-player song.mp3                # 播放 MP3
```

`clipboard-image` 需要访问桌面剪贴板，输出的 PNG 不得超过 18 MiB。剪贴板无图片、图片超限或写入失败时，程序向标准错误输出错误信息，并以非零状态退出。Pi 扩展的用法见 [Pi 扩展文档](docs/pi-clipimg.md)。

## 安装与构建

在仓库根目录构建两个程序，产物默认位于 `target/release/`：

```bash
cargo build --workspace --bins --release
```

也可分别安装：

```bash
cargo install --path crates/clipboard-image
cargo install --path crates/audio-player
```

也可交叉编译 Windows 版本（需安装对应 Rust target 和 MinGW 工具链）：

```bash
cargo build --workspace --bins --release --target x86_64-pc-windows-gnu
```
