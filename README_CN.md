### TWRP 设备树 | 小米 Civi 3 (yuechu)
[English Version](README.md)

## 设备参数信息

基本参数   | 规格
-------:|:-------------------------
CPU     | 八核1+3+4架构 Cortex-A78主频最高可达3.1GHz
处理器   | 联发科 天玑 8200-Ultra
GPU     | Mali-G610 MC6
运行内存 | 8/12 GB RAM (LPDDR5 6400Mbps)
出厂系统 |  基于安卓13的MIUI 14
存储规格 | 256G/512G/1TB (UFS 3.1)
电池容量 | 4500 mAh不可拆卸式
屏幕规格 | 分辨率：1080 x 2400, 6.5 英寸
支持的刷新率 | 60/90/120 Hz
屏幕类型 | AMOLED屏幕

![Xiaomi Civi 3](https://cdn.cnbj1.fds.api.mi-img.com/product-images/xiaomicivi3tbjfwq/specs/4282.png?x-fds-process=image/resize,q_90,f_webp)

正常工作的:
- [X] ADB调试
- [X] data解密 (Android 15)
- [X] 屏幕显示
- [X] Fasbootd模式
- [X] 卡刷模式
- [X] MTP文件传输
- [X] Sideload侧载刷入
- [X] USB OTG功能
- [X] 震动
- [X] 触摸

## 我该如何编译它？

首先使用以下命令同步最小版本的TWRP

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

然后将这些项目添加到.repo/manifest.xml：

```xml
<project path="device/xiaomi/pearl" name="haitian8181/android_device_xiaomi_yuechu" remote="github" revision="a15" />
```

最后执行以下命令

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_yuechu-eng
mka vendorbootimage -j$(nproc --all)
```
## 我该如何刷入？

使用以下命令刷入编译好的rec
```
fastboot flash vendor_boot out/target/product/yuechu/vendor_boot.img
```
