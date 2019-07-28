# Device Tree for Google Pixel 3A/XL (bonito/sargo)

This device tree was forked from lineageOS with some changes/proprietary files from the Dirty Unicorns/statixOS sargo build.


## Current status

The sargo image seems to be working, but the bonito image does not boot.


## Adding this to your build

You can add this repo to your build by adding the following to your .repo/local_manifests/roomservice.xml file:

```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>

  <remote  name="gee-one"
           fetch="https://github.com/gee-one/"    

  <project name="gee-one/android_device_google_bonito" path="device/google/bonito" remote="gee-one" revision="aosp-vendor-los" />
  <project name="LineageOS/android_kernel_google_bonito" path="kernel/google/bonito" remote="github" />
  <project name="LineageOS/android_device_google_sargo" path="device/google/sargo" remote="github" />

</manifest>

```

## AOSP vendor image

This uses the aosp vendor.img, which are provided as part of AOSP.

https://developers.google.com/android/drivers#sargo

https://developers.google.com/android/drivers#bonito

The aosp vendor.img can be extracted from google driver binaries and should live in vendor/google_devices/{sargo|bonito}/proprietary/vendor.img.  The other (make) files from the google_devices folder aren't needed.

A better developer would probably actually build the vendor image, especially since there are some files that in the make files that are installed to the vendor partition.  I guess they end up with the missing socks in the dryer.



## Extracting the proprietary files

The proprietary files can be extracted from the stock images.

https://developers.google.com/android/images#sargo

https://developers.google.com/android/images#bonito

The extraction scripts are split (not common) and are located in the respective bonito or sargo folders.

The common extraction scripts are still in place and this might cause some confusion.

The proprietary files list are created from the lineage repos and any files I could find in the DU/statix builds for sargo.


## Returning vendor to google stock

If switching back to other roms that don't include a vendor image, you can flash the stock vendor.img from google.

https://developers.google.com/android/images#sargo

https://developers.google.com/android/images#bonito

Extract the vendor.img and flash in fastboot mode.

```
fastboot flash vendor_a vendor.img
fastboot flash vendor_b vendor.img
```
