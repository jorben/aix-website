---
date: '2025-11-07T01:03:42+08:00'
draft: false
title: 'u盘安装linux系统的时候，有时候会遇到找不到盘'
authors:
  - name: Jorben
    link: https://github.com/jorben
    image: https://github.com/jorben.png
tags:
  - linux
---

u盘安装linux系统的时候，有时候会遇到找不到盘
{{% steps %}}

### 第一步

要先确定u盘的资源符，比如我的是 /dev/sdd4

### 第二步

在进入安装界面选择install的时候根据系统提示（有的是按tab键有的是按e）修改引导指令

### 第三步

将`linuxefi /images/pxeboot/ymlinuz inst.stage2=hd:LABEL=Rocky-Linux-9-3-X86 quiet`修改为`linuxefi /images/pxeboot/ymlinuz inst.stage2=hd:/dev/sdd4 quiet`

{{% /steps %}}