# HornbillOS
<!-- 
![HornbillBanner](https://raw.githubusercontent.com/HornbillOS/docs/master/src/hornbillbanner.png) -->

Credits
-------
 * [**AOSP**](https://android.googlesource.com)
 * [**LineageOS**](https://github.com/LineageOS)
 * [**ArrowOS**](https://github.com/ArrowOS)

# twelve-release

### Ingredients
- Around 75G disk space
- 20G or more usable internet
- A computer with at least 8G RAM running Linux or MacOS
- A brain

### Instructions
- Preparing the sauce
    1. Make sure you have a build environment setup.
    2. Make a new directory, cd to it and run
        ```
        mkdir -p ~/hornbill
        repo init -u https://github.com/HornbillOS/manifest -b twelve;
        repo sync --force-sync;
        ```
    3. The ROM sauce is ready! Get ready to prepare your device-specific sauce.

- Preparing device sauce
    1. Define all relevant device repositories in `.repo/local_manifests/local_manifests.xml`
    2. Run `repo sync;`
    3. Move/copy your `<ROM>.mk` (Example: `lineage.mk`) file to `arrow.mk`.
    4. Open this file and
        - Set PRODUCT_NAME to `arrow_<device>` (Example: `arrow_beryllium`)
        - For a Phone or tablet with a SIM Card, add
            ```
            # Inherit from HornbillOS vendor
            $(call inherit-product, vendor/arrow/config/common_full_phone.mk)
            ```
        - For a WiFi-only tablet, add
            ```
            # Inherit from HornbillOS vendor
            $(call inherit-product, vendor/arrow/config/common_full_tablet_wifionly.mk)
            ```
    5. Save and exit

- Cooking
    1. Run
        ```
        source build/envsetup.sh;
        lunch arrow_<device>-userdebug
        make -j$(nproc --all) bacon
        ```
        Example:
        ```
        source build/envsetup.sh;
        lunch arrow_beryllium-userdebug
        make -j$(nproc --all) bacon
        ```
    2. This will start compiling the build. Now you can go for walk, play or do whatever you want until this completes.
    3. Resolve errors if any and continue building.

### Reporting compilation issues
- You can reach us at [**Telegram**](https://t.me/hornbillos)
- For common porting related errors, visit [**Rom development**](https://t.me/alaskalinuxuser_romdevelopment)
- Make sure you provide relevant logs, screenshots and details with all sources you used.

### Adding Support
- For adding your device to the list of supported devices, please reach us at [**Telegram**](https://t.me/hornbillos) with your device tree and previous works.
