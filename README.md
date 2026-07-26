# InfinityX 3.12 Local Manifest — Infinix Hot 60 Pro Plus (X6886)

Local manifest for building **InfinityX 3.12** for the **Infinix Hot 60 Pro Plus (X6886 / MT6789)**.

## Repos

| Repo | Source | Branch |
| :--- | :--- | :--- |
| device/infinix/x6886 | Il103/android_device_infinix_x6886 | Device.InfinityX.3.12 |
| vendor/infinix/x6886 | Il103/vendor_infinix_x6886 | Vendor.InfinityX.3.12 |
| kernel/infinix/x6886 | Il103/kernel_infinix_x6886 | Kernel.InfinityX.3.12 |
| hardware/mediatek | LineageOS/android_hardware_mediatek | lineage-23.2 |
| device/mediatek/sepolicy_vndr | LineageOS/android_device_mediatek_sepolicy_vndr | lineage-23.2 |
| hardware/transsion | mt6789-transsion/hardware_transsion | lineage-23.0 |
| vendor/mediatek/ims | xiaomi-mediatek-devs/android_vendor_mediatek_ims | android-16 |

## Usage

```bash
# 1. Initialize LineageOS 23.2 source
repo init -u https://github.com/LineageOS/android -b lineage-23.2

# 2. Sync AOSP + LOS repos
repo sync

# 3. Add local manifest
cp x6886.xml .repo/local_manifests/

# 4. Re-sync to pull device-specific repos
repo sync

# 5. Build
source build/envsetup.sh
lunch lineage_x6886-ap4a-userdebug
mka bacon -j$(nproc)
```

## Maintainer

B E R U (@Il103)
