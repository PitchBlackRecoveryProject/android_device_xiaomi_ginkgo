# Unified TWRP Device Tree for Redmi Note 8/8T (ginkgo/willow)

The Redmi Note 8 (codenamed "ginkgo") is a mid-range smartphone from Xiaomi. It was announced in August 2019 and released in October 2019.

The Redmi Note 8T (codenamed "willow") is a mid-range smartphone from Xiaomi. Unlike Redmi Note 8, it does not have a notification LED but instead has a NFC communication module by NXP. It was announced and released in November 2019.

## Device specifications

| Feature                 | Specification                                                   |
| :---------------------- | :---------------------------------------------------------------|
| Chipset                 | Qualcomm SM6125 Snapdragon 665 (11 nm)                          |
| CPU                     | Octa-core (4x2.0 GHz Kryo 260 Gold & 4x1.8 GHz Kryo 260 Silver) |
| GPU                     | Adreno 610                                                      |
| Memory                  | 3/4/6 GB                                                        |
| Shipped Android Version | 9.0 (MIUI 11)                                                   |
| Storage                 | 32/64/128 GB eMMC                                               |
| SIM                     | Dual SIM (Nano-SIM, dual stand-by)                              |
| MicroSD                 | Up to 256 GB                                                    |
| Battery                 | 4000 mAh Li-Po (non-removable)                                  |
| Dimensions              | 158.3 x 75.3 x 8.4 mm                                           |
| Display                 | 6.3 inch, 1080 x 2340 (19.5:9 ratio)                            |
| Rear Camera 1           | 48 MP, f/1.8, 26mm (wide), 1/2.0", 0.8µm, PDAF                  |
| Rear Camera 2           | 8 MP, f/2.2, 13mm (ultrawide), 1/4.0", 1.12µm                   |
| Rear Camera 3           | 2 MP, f/2.4, (macro), 1/5.0", 1.75µm                            |
| Rear Camera 4           | 2 MP, f/2.4, (depth)                                            |
| Front Camera            | 13 MP, f/2.0, (wide), 1/3.1", 1.12µm                            |
| Fingerprint             | Rear-mounted                                                    |
| Sensors                 | Accelerometer, Gyro, Proximity, Compass                         |

## Device picture

![Redmi Note 8](https://i01.appmifile.com/webfile/globalimg/products/pc/redmi-note-8/specs1.png)


For building TWRP for Xiaomi Redmi Note 8/8T

TWRP device tree for Xiaomi Redmi Note 8/8T

## Features

Works:

- ADB
- Decryption of /data
- Screen brightness settings
- Correct screenshot color
- MTP
- Flashing (opengapps, roms, images and so on)
- Backup/Restore
- USB OTG

TO-DO:

- Vibration support

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/ginkgo" name="TeamWin/android_device_xiaomi_ginkgo" remote="github" revision="android-9.0" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_ginkgo-eng
export ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
mka recocoveryimage
```

To test it:

```
fastboot boot out/target/product/ginkgo/recovery.img
```

## Thanks

- Thanks to @PeterCxy for the commits and the base: https://github.com/PeterCxy/android_device_xiaomi_violet-twrp
