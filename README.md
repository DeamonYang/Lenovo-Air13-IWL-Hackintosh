# Lenovo-Air13-IWL黑苹果全套hotpatch施工，EFI适配10.13/10.14

## 电脑配置

| 规格     | 详细信息                                                     |
| -------- | ------------------------------------------------------------ |
| 电脑型号 | 联想Lenovo Air 13 IWL笔记本电脑                              |
| 操作系统 | macOS Mojave 10.14.1 18B75/macOS High Sierra 10.13.6 17G2208 |
| 处理器   | Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz                     |
| 内存     | 16 GB  1867MHz                                               |
| 硬盘     | Crucial_CT500MX200SSD1 (500G固态)                            |
| 显卡     | 英特尔 HD Graphics 500 8086:3EA0(Whiskey Lake) (显卡仿冒：注入platform-id:0x3e9b0009) |
| 显示器   | FHD 1920x1080 (13.3 英寸)                                    |
| 声卡     | ALC236 (layout-id:99)                                        |
| 网卡     | REALTEK 10EC:B822 已更换为`DW1820A`(14E4:43A3)               |

## 安装镜像

直接使用博客中的镜像进行安装：[【黑果小兵】macOS Mojave 10.14(18A389) with Clover 4670原版镜像](https://blog.daliansky.net/macOS-Mojave-10.14-18A389-Release-with-Clover-4670-original-mirror.html)

## 完善驱动

1. 声卡：型号为ALC236，注入ID：99，使用AppleALC仿冒，顺利加载；修正HDMI Audio输出信息；安装完系统后请安装[ALCPlugFix_for_ALC_node12_19](https://github.com/daliansky/Lenovo-Air13-IWL/tree/master/ALCPlugFix_for_ALC_node12_19)声卡守护进程，耳麦工作正常；
2. 网卡：REALTEK `10EC:B822`的无线网卡截止到目前还是无解，可更换为`DW1820A`；
3. 显卡：Intel UHD Graphics 620，Whiskey Lake平台目前还没有驱动程序，使用Coffee Lake仿冒驱动，Platform-id为：`0x3e9b0009`，添加DVMT补丁；采用Devices-Properties方法注入；外接HDMI显示器工作正常；睡眠唤醒正常；
4. 蓝牙工作正常；睡眠唤醒工作正常；
5. 电池信息正常；
6. 触摸板：使用`VoodooI2C`驱动，多手势全功能正常工作；
7. 显示器亮度调节正常；亮度调节快捷键：`F11`和`F12`
8. USB端口识别，已订制；摄像头、无线网卡已内建，避免睡眠问题；

## 系统截图

![0About](ScreenShot/0About.png)

![0Disk](ScreenShot/0Disk.png)

![0Display](ScreenShot/0Display.png)

![0Hardware](ScreenShot/0Hardware.png)

![0Monitor](ScreenShot/0Monitor.png)

![1Memory](ScreenShot/1Memory.png)

![1NVMe](ScreenShot/1NVMe.png)

![1USB-Port](ScreenShot/1USB-Port.png)

![1USB-Wifi_and_Other](ScreenShot/1USB-Wifi_and_Other.png)

![1USB](ScreenShot/1USB.png)

![2AppleALC236](ScreenShot/ALC236_ID99.png)

![2AppleHDA](ScreenShot/2AppleHDA.png)

![6Light](ScreenShot/6Light.png)

![6Volume](ScreenShot/6Volume.png)

![8Ext](ScreenShot/8Ext.png)

![9Mojave18B75](ScreenShot/9Mojave18B75.png)

![0Clover](ScreenShot/0Clover.png)

## DW1820A截图及系统信息

![0DW1820A_0VW3T3](./ScreenShot/0DW1820A_0VW3T3.png)

![1DW1820A_Air13IWL](./ScreenShot/1DW1820A_Air13IWL.png)

![2DW1820A_Air13IWL2](./ScreenShot/2DW1820A_Air13IWL2.png)

![2DW1820A_Air13IWL3](./ScreenShot/2DW1820A_Air13IWL3.png)

![2DW1820A_Air13IWL4](./ScreenShot/2DW1820A_Air13IWL4.png)

![DW1820A_bluetooth1](./ScreenShot/DW1820A_bluetooth1.png)

![DW1820A_bluetooth2](./ScreenShot/DW1820A_bluetooth2.png)

![DW1820A_bluetooth3](./ScreenShot/DW1820A_bluetooth3.png)

![DW1820A_bluetooth4](./ScreenShot/DW1820A_bluetooth4.png)

![DW1820A_DELL7000](./ScreenShot/DW1820A_DELL7000.png)

![DW1820A_Ext](./ScreenShot/DW1820A_Ext.png)

![DW1820A_WIFI](./ScreenShot/DW1820A_WIFI.png)

![DW1820A_WIFI1](./ScreenShot/DW1820A_WIFI1.png)

![DW1820A_WIFI2](./ScreenShot/DW1820A_WIFI2.png)



## 更新日志：

- 8-7-2019
  - 修复蓝牙驱动，`DW1820A` 可以正常使用了
- 5-22-2019
  - **添加对`DW1820A`无线网卡的支持**
  - 测试环境：macOS Mojave 10.14.5 18F132，截屏见上方
- 5-16-2019
  - 更新`CLOVER`版本到4928
  - 其它的常规更新
- 12-17-2018
  - 修改了声卡的驱动方式，移除`FakePCIID`+`FakePCIID_Intel_HDMI_Audio`
  - VirtualSMC更新到v1.0.2，包括传感器插件
  - SSDT更新，触摸板可通过连续按5次`F6`或者`WIN`键关闭或者开启
- 12-4-2018
  - 更新`AppleALC` v1.3.4，已提交到`vit9696`合并完毕
  - 全新仿冒了小新AIR的声卡id：99
- 11-25-2018
  - 修改显卡驱动方式：
    - Whiskey lake仿冒Coffee lake
    - platform-id注入id:`3e9b0006`
    - 可完美睡眠唤醒，可调节屏幕亮度
  - 声卡驱动方式：
    - 采用`AppleALC`仿冒原生驱动`AppleHDA`
    - ALC236注入id:2
    - 驱动方式：`FakePCI-ID`+`FakePCIID_Intel_HDMI_Audio`
  - 添加`ALCPlugFix`守护进程，解决耳机/耳麦自动切换，解决睡眠唤醒



## EFI下载链接：

Https://github.com/daliansky/Lenovo-Air13-IWL



## 特别鸣谢：@宪武，整理出联想所有机型的hotpatch

## 鸣谢：

- [RehabMan](https://github.com/RehabMan) 提供 [AppleBacklightInjector](https://github.com/RehabMan/HP-ProBook-4x30s-DSDT-Patch/tree/master/kexts/AppleBacklightInjector.kext) 和 [EAPD-Codec-Commander](https://github.com/RehabMan/EAPD-Codec-Commander) 和 [OS-X-ACPI-Battery-Driver](https://github.com/RehabMan/OS-X-ACPI-Battery-Driver) 和 [OS-X-Clover-Laptop-Config](https://github.com/RehabMan/OS-X-Clover-Laptop-Config) 和 [OS-X-FakeSMC-kozlek](https://github.com/RehabMan/OS-X-FakeSMC-kozlek) 和 [OS-X-Null-Ethernet](https://github.com/RehabMan/OS-X-Null-Ethernet) 和 [OS-X-USB-Inject-All](https://github.com/RehabMan/OS-X-USB-Inject-All) 和 [OS-X-Voodoo-PS2-Controller](https://github.com/RehabMan/OS-X-Voodoo-PS2-Controller) 的维护
- [vit9696](https://github.com/vit9696) 提供 [Lilu](https://github.com/acidanthera/Lilu) 和 [AppleALC](https://github.com/acidanthera/AppleALC) 和 [WhateverGreen](https://github.com/acidanthera/WhateverGreen) 的维护
- [PMheart](https://github.com/PMheart) 提供 [CPUFriend](https://github.com/PMheart/CPUFriend) 的维护
- [alexandred](https://github.com/alexandred) 和 [hieplpvip](https://github.com/hieplpvip) 提供 [VoodooI2C](https://github.com/alexandred/VoodooI2C) 的维护
- [PavelLJ](https://github.com/PavelLJ) 和 [Javmain](https://github.com/javmain) 和 [johnnync13](https://github.com/johnnync13) 的宝贵建议

## 关于打赏

如果您认可我的工作，请通过打赏支持我后续的更新

| 微信                                                       | 支付宝                                               |
| ---------------------------------------------------------- | ---------------------------------------------------- |
| ![wechatpay_160](http://7.daliansky.net/wechatpay_160.jpg) | ![alipay_160](http://7.daliansky.net/alipay_160.jpg) |

## QQ群:

331686786 [一起吃苹果](http://shang.qq.com/wpa/qunwpa?idkey=db511a29e856f37cbb871108ffa77a6e79dde47e491b8f2c8d8fe4d3c310de91)

688324116[一起黑苹果](https://shang.qq.com/wpa/qunwpa?idkey=6bf69a6f4b983dce94ab42e439f02195dfd19a1601522c10ad41f4df97e0da82)

128630866[ThinkPad黑苹果交流群](https://jq.qq.com/?_wv=1027&k=5aKxc6n)




