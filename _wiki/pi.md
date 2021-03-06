---
layout: wiki
title: raspberryPi
categories: raspberryPi
description: raspberryPi 使用技巧
keywords: raspberryPi，配置
---

## 显示器不能全部铺满

如果你使用 HDMI 端口连接到显示器或电视上，或许你会发现你的画面四周有黑边存在，为了避免黑边可以通过将该值设为 1 来把默认 overscan 选项关闭。

修改`/boot/config.txt`如下:

```
disable_overscan=1
```

## 给 openEulerOS + xfce 添加蓝牙管理

- 安装管理客户端
  `sudo dnf install blueman`

- 进入命令行界面
  `bluetoothctl`

- 打开蓝牙
  `power on`

- 搜索蓝牙设备
  `scan on`

- 配对
  `pair <mac address>`

- 信任蓝牙设备，只有这样才能自动连接
  `trust <mac address>`

- 主动连接蓝牙设备
  `connect <mac address>`

- 设置蓝牙开机启动
  修改 /etc/bluetooth/main.conf 文件：
  `AutoEnable=true`

