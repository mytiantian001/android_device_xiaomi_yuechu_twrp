### TWRP device tree for Xiaomi Civi 3 (yuechu)
=========================================

[简体中文](README_CN.md)

The Xiaomi Civi 3 (codenamed _"yuechu"_) is a high-end, mid-range smartphone from Xiaomi.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Octa-core CPU with 4x Arm Cortex-A78 up to 3.1GHz
Chipset | Mediatek Dimensity 8200-Ultra
GPU     | Mali-G610 MC6
Memory  | 8/12 GB RAM (LPDDR5 6400Mbps)
Shipped Android Version | 13 with MIUI 14
Storage | 256G/512G/1TB (UFS 3.1)
Battery | Non-removable Li-Po 4500 mAh battery
Display | 1080 x 2400 pixels, 6.5 inches, 60/90/120 Hz, AMOLED

![Xiaomi Civi 3](https://cdn.cnbj1.fds.api.mi-img.com/product-images/xiaomicivi3tbjfwq/specs/4282.png?x-fds-process=image/resize,q_90,f_webp)

## Features

Works:

- [X] ADB
- [X] Decryption (Android 15)
- [X] Display
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG
- [X] Vibrator
- [X] Touch

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/pearl" name="mytiantian001/android_device_xiaomi_yuechu" remote="github" revision="a15" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_yuechu-eng
mka vendorbootimage -j$(nproc --all)
```
## To use it:

```
fastboot flash vendor_boot out/target/product/yuechu/vendor_boot.img
```
