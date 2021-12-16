----

- 类型：个人翻译
- 时间：2021年12月16日
- 标签：GNOME
- 原文: [An Optimization Proposed For GNOME + NVIDIA On High Refresh Rate Displays](https://www.phoronix.com/scan.php?page=news_item&px=GNOME-NV-HRR-Fraction)

----

## 针对 GNOME + NVIDIA 的高刷新率显示器的优化建议

来自 Canonical ，专注于 GNOME 的 Ubuntu 桌面开发人员 Daniel Van Vugt 提出了一种优化方案，可以帮助在高刷新率显示器上运行 NVIDIA 图形驱动。

对于那些在 GNOME 上使用高刷新率显示和 NVIDIA 图形驱动的人，尤其是在今天的 240Hz 甚至 360Hz 显示中，更好的处理方式即将到来，在 GNOME 的 Mutter 回落到较慢的帧间隔之前，允许有更多时间来完成每一帧的渲染。

Mutter 目前具有 2ms 的静态同步延迟回退值。在刷新间隔约为 4.1 毫秒的 240Hz 显示器上运行 NVIDIA 图形驱动时，在回落到 120Hz 刷新率之前只剩下 2.1 毫秒的最大渲染时间。但是通过将该值更改为分数（值为 0.875），它不会回归常见 60Hz 显示器的行为，但允许最大渲染时间约为 3.6 毫秒，而不是 2.1 毫秒，然后再回落到较低的速率。 每帧额外的 1.5 毫秒渲染时间，有更大的机会满足最后期限并避免 Mutter 缩小到 120Hz。 同样，使用分数而不是静态值应该对 360Hz 和其他越来越高刷新率的显示器上市有更大的帮助。

改变 Clutter 帧时钟值的[补丁](https://gitlab.gnome.org/GNOME/mutter/-/merge_requests/2158?commit_id=07a6a78e2255f03d24e78f9fc5a7b133ccdfa0f0)目前正在为 Mutter 进行审查，并可能在 GNOME 42 上登陆。

与此同时，Daniel Van Vugt 仍在[为 GNOME 寻求三重缓冲](https://www.phoronix.com/scan.php?page=news_item&px=GNOME-42-Likely-Triple-Buffers)。在这方面，他一直致力于改进缩放算法并重新实施平滑解决方法。

----

## 英特尔启用 Resizable BAR 以在 Linux 上使用 I/O 虚拟化

Resizable BAR 支持（也称为 ReBAR / [AMD 显存智取技术](https://www.amd.com/zh-hans/technologies/smart-access-memory)）一直受到游戏玩家的欢迎，因为它支持的配置[能够提高 GPU 性能](https://www.phoronix.com/scan.php?page=article&item=nvidia-rebar-rtx30&num=1)。英特尔现在正致力于使 Linux 内核在 I/O 虚拟化环境中支持 ReBAR。

Resizable BAR 是一项 PCIe 功能，可以允许 CPU 访问整个 vRAM 内容，而不是仅限于 256MB 的窗口。反过来，这可以提高 CPU 和 GPU 之间的传输效率，但取决于 CPU/GPU/系统支持情况。Linux 支持 Resizable BAR 行为作为 PCIe 规范的一部分，并且各种 Linux 图形驱动程序确实在功能强大的系统配置中使用 Resizable BAR。

英特尔正在开发的新补丁用于在 PCI VF（虚拟功能）代码中启用 Resizable BAR 支持，以便现有的 ReBAR 查询/启用接口也可以与 I/O 虚拟化 (IOV，I/O Virtualization) BAR 一起使用。这反过来对于那些通过 SR-IOV 分配显卡以在虚拟机等中进行游戏的人来说应该是有用的，以便能够启用 Resizable BAR。

你可以通过[此补丁线程](https://lore.kernel.org/lkml/20211215141626.3090807-1-michal.winiarski@intel.com/)找到正在进行的对 IOV 的 Resizable BAR 支持。