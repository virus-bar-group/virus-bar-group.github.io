---
title: 在系统重装时加载 Intel RST 驱动
date: 2023-09-26 22:22:00
tags:
- 帮助
---

> 感谢 @永恒者 投稿，有改动

**Intel** **R**apid **S**torage **T**echnology，即英特尔快速存储技术，据英特尔公司称可以实现加速硬盘、保证数据可靠性等功能。

在安装对应驱动程序，并将 BIOS 中的硬盘模式设置为 Intel RST 后即可启用该功能。然而，在某些情况下，驱动程序可能无法正常加载，导致系统无法读取硬盘并引发一系列问题。

如果你在重装系统时遇到了这种状况，可以尝试加载 Intel RST 驱动。前往 [Intel 支持页面](https://www.intel.cn/content/www/cn/zh/support/products/55005/technologies/intel-rapid-storage-technology-intel-rst.html)，向下拉至“最新驱动程序和软件”一节，如图：

<div style="width: 80%; margin: auto;">{% asset_img 1.png %}</div>

> 如果你不知道该如何选择 `第？代平台`，可以查看你的 CPU 型号，去掉后三位之后的数字就是。例如，i7-**9**750H 是第 9 代，i9-**12**900H 是第 12 代。可前往[英特尔官方支持页面](https://www.intel.cn/content/www/cn/zh/processors/processor-numbers.html)了解详情。

选择匹配的版本下载，得到 `SetupRST.exe`。

在其同级文件夹启动终端（可点击 explorer 地址栏，输入 cmd 后回车，见图示）：

<div style="width: 80%; margin: auto;">{% asset_img 2.png %}</div>

在弹窗中输入

```
SetupRST.exe -extractdrivers SetupRST_extracted
```

> UAC 用户账户控制弹出窗口时，请点击“是”，允许 SetupRST.exe 继续运行

一个背景为蓝色，包含英特尔公司 logo 和 `Intel Rapid Storage Technology` 字样的窗口会弹出，并很快消失。在此之后，你应该在 `SetupRST.exe` 的同级文件夹下得到 `SetupRST_extracted` 文件夹。

将其整个复制到 U 盘或其他可访问到的位置，然后从 PE 正常启动 Windows 安装程序。在`你想将 Windows 安装在哪里？`界面，点击左下角的`加载驱动程序(L)`，在弹出窗口中点击`浏览`，定位并选择先前的 `SetupRST_extracted` 文件夹，全选列表中出现的 `*.inf` 文件，然后点击右下角的`下一步`。此时 Windows 将会安装所选驱动程序，随后便可选择磁盘。
