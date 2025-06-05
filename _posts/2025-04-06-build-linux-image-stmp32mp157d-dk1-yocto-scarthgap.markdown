---
layout: post
title:  "Building a Linux Image for STM32MP157D-DK1 with Yocto Scarthgap"
date:   2025-06-04 16:50:07 -0500
categories: yocto stm32mp1 linux
---
1. **Configure Build Layers**:
    
    Edit `build-stm32mp1/conf/bblayers.conf` to include the following layers:

    ```bash
    BBLAYERS = " \
      ${TOPDIR}/../poky/meta \
      ${TOPDIR}/../poky/meta-poky \
      ${TOPDIR}/../poky/meta-yocto-bsp \
      ${TOPDIR}/../meta-openembedded/meta-oe \
      ${TOPDIR}/../meta-openembedded/meta-python \
      ${TOPDIR}/../meta-st-stm32mp \
    "
   ```

    Working versions with `scarthgap` release:

    - poky: `git://git.yoctoproject.org/poky`, tag: `scarthgap-5.0.9`
    - meta-openembedded: `git://git.openembedded.org/meta-openembedded`, hash: `e92d0173a8`
    - meta-st-stm32mp: `https://github.com/STMicroelectronics/meta-st-stm32mp.git`, tag: `openstlinux-6.6-yocto-scarthgap-mpu-v24.11.06`

2. **Configure Machine**:

   Edit `build/conf/local.conf` to set:

   ```bash
   MACHINE = "stm32mp1"
   ```

3. **Build image**:

    ```bash
    bitbake core-image-full-cmdline
    ```
