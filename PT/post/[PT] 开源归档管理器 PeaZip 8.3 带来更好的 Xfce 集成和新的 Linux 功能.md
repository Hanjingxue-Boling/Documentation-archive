----

- 类型：个人翻译
- 时间：2021年11月15日
- 标签：Peazip
- 原文：[PeaZip 8.3 Open-Source Archive Manager Brings Better Xfce Integration, New Linux Features](https://9to5linux.com/peazip-8-3-open-source-archive-manager-brings-better-xfce-integration-new-linux-features)

----

## 开源归档管理器 PeaZip 8.3 带来更好的 Xfce 集成和新的 Linux 功能

开源和跨平台归档管理器 PeaZip 8.3 现在可供 GNU/Linux、macOS 和 Windows 平台下载，其中包含面向 Linux 用户的各种新功能和改进。

PeaZip 8.3 为想要使用强大归档管理器的 Linux 用户提供了许多好东西，首先是能够从`选项` > `设置` > `常规、性能` 中自定义应用程序生成的命令脚本的最大长度（从 32KB 到 2MB ）。

如果定义了 `$XDG_CONFIG_HOME` 变量（如果未定义，配置将保存到 `$HOME/.config/peazip`），它还可以通过将配置文件保存在 `$XDG_CONFIG_HOME/peazip` 目录中来提高对 [开放桌面规范](https://www.freedesktop.org/wiki/Specifications/) 的遵从性。 用户可以通过将 `$HOME/.PeaZip` 目录的内容复制到新位置来导入配置。

对于 [Xfce 桌面环境](https://xfce.org/) 的用户来说，还有一个好消息，因为 PeaZip 8.3 通过自动改进在 “打开方式” 右键单击上下文菜单中配置 Xfce 应用程序替代方案的方式，提供了与 Xfce 更好的集成。 这适用于 Midori 网络浏览器、Mousepad 文本编辑器、Parole 视频播放器和 Ristretto 图像查看器等应用程序。

对于 Linux 用户，PeaZip 8.3 在导航树中的文件系统组下增加了 /media、/run/media 和 /mnt 挂载的快捷方式，修复了 GTK+ 2 的一些主题问题，改进了 ZIP 归档文件的处理；并通过更好地符合文件系统层次结构标准，分离架构和非架构特定资源，改进了适用于基于 Ubuntu/Debian 和 Red Hat/Fedora 的发行版 DEB 和 RPM 安装程序。

除此之外，PeaZip 8.3 版本为 7z 归档格式添加了 Deflate 和 Deflate64 压缩选项，改进了 `-ext2here`、`-ext2folder`（`-alias -ext2smart`）和` -ext2newfolder` 功能，并使用新的命令行选项，如 `-i` 来忽略提取后删除原始存档，`-o` 用于输出目录，`-p` 用于密码。

在这次更新中，内部文件结构被重构，通过明确地将二进制和架构相关的文件与其他资源分开，使 PeaZip 更容易被移植到对其层次结构有特殊要求的多个操作系统和架构上。

此版本中另一个有趣的功能是能够自定义用于计算文件校验和和哈希的首选算法列表。 此外，PeaZip 现在允许用户将多字节单位设置为二进制、1024（IEC 千字节）、十进制、1000（IEC 千字节）或无（精确字节大小）。

当然，几个错误被解决了，主题设计也得到了改进，新增了色温和高亮标签选项，通过使用较暖或较冷的颜色使应用程序适应你的桌面环境，并以交替的颜色来突出包含标签的列或行。

您现在可以从 [官方网站](https://peazip.github.io/peazip-linux.html) 下载 PeaZip 8.3，作为 GTK+ 或 Qt 环境的 DEB、RPM 或通用安装程序，或者从 Flathub 下载 [Flatpak](https://flathub.org/apps/details/io.github.peazip.PeaZip)。 有关此更新中包含的更改的更多详细信息，请查看 [完整的更改日志](https://peazip.github.io/changelog.html)。