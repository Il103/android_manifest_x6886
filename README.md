# X6886 Local Manifest for LineageOS 23.2

Local manifest for building **LineageOS 23.2** for **Infinix Hot 60 Pro Plus (X6886 / MT6789)**.

## Repos

| Repo | Source | Branch |
| :--- | :--- | :--- |
| device/infinix/x6886 | Il103/android_device_infinix_x6886 | Device.Lineage.23.2 |
| vendor/infinix/x6886 | Il103/vendor_infinix_x6886 | Vendor.Lineage.23.2 |
| kernel/infinix/x6886 | Il103/kernel_infinix_x6886 | Kernel.Lineage.23.2 |
| hardware/mediatek | LineageOS/android_hardware_mediatek | lineage-23.2 |
| device/mediatek/sepolicy_vndr | LineageOS/android_device_mediatek_sepolicy_vndr | lineage-23.2 |
| hardware/transsion | mt6789-transsion/hardware_transsion | lineage-23.0 |
| vendor/mediatek/ims | xiaomi-mediatek-devs/android_vendor_mediatek_ims | android-16 |

## Usage

```bash
# 1. Initialize LineageOS 23.2 source
repo init -u https://github.com/LineageOS/android.git -b lineage-23.2 --depth=1

# 2. Add X6886 local manifest
mkdir -p .repo/local_manifests
curl -o .repo/local_manifests/x6886.xml \
  https://raw.githubusercontent.com/Il103/android_manifest_x6886/Manifest.Lineage.23.2/x6886.xml

# 3. Sync all sources
repo sync -c --no-tags -j6

# 4. Pull LFS blobs (vendor only)
cd vendor/infinix/x6886 && git lfs pull && cd ../../..

# 5. Build
source build/envsetup.sh
lunch lineage_x6886-userdebug
mka bacon -j24
```

## Included packages

| # | Repo | Path | Description |
|---|------|------|-------------|
| 1 | Il103/android_device_infinix_x6886 | device/infinix/x6886 | Device tree (BoardConfig, init, configs, overlays, sepolicy) |
| 2 | Il103/vendor_infinix_x6886 | vendor/infinix/x6886 | 5010 proprietary blobs from stock (LFS) |
| 3 | Il103/kernel_infinix_x6886 | kernel/infinix/x6886 | Kernel source 5.10.198 (MT6789) |
| 4 | LineageOS/android_hardware_mediatek | hardware/mediatek | MTK hardware HALs and libraries |
| 5 | LineageOS/android_device_mediatek_sepolicy_vndr | device/mediatek/sepolicy_vndr | MTK vendor SELinux policies |
| 6 | mt6789-transsion/hardware_transsion | hardware/transsion | Transsion-specific HALs (lights, vibrator, etc.) |
| 7 | xiaomi-mediatek-devs/android_vendor_mediatek_ims | vendor/mediatek/ims | MTK IMS for VoLTE/VoWiFi |

## Stock ROM details

- **Firmware version:** X6886-H668L-G2954 (Hot 60 Pro Plus)
- **Android version:** 15 (API 35)
- **Kernel:** Linux 5.10.198
- **Platform:** MT6789 (Helio G200)
- **Security patch:** February 2026

## Notes

- Only `vendor/infinix/x6886` uses Git LFS. Run `git lfs pull` there before building.
- The kernel tree contains the full kernel source (not prebuilt).
- VNDK compatibility shims (v31-v34) are included in the device tree.
- Blobs extracted from full firmware dump (system, vendor, product, system_ext, vendor_boot, vendor_dlkm).

## Credits

- Stock ROM dump by [Il103](https://github.com/Il103)
- Device/vendor/kernel trees by [Il103](https://github.com/Il103)
