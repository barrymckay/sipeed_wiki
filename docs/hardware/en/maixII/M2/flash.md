---
title: Burning MaixII-Dock OS
keywords: MaixII, MaixPy3, Python, Python3, M2dock
desc: maixpy  Burning MaixII-Dock OS
---

> Edit on 2024.09.23 (English clarification/spelling/grammar adjustments)

## Get system image file

Download the newest V831 system image from the Download page at this website [SDK_MaixII/release](https://dl.sipeed.com/shareURL/MaixII/MaixII-Dock/SDK/release), unpack the downloaded file to get the .img file, which is the system image file. 

> If it is slow to download, you can use MEGA: https://mega.nz/folder/5dJSWJDD#nQmiOeJsX6pEl2Q0cBrj2A

## Image name rules

For V831 there are naming rules for all files.

For example, `v831-m2dock-maixhub-0.5.1-20220701.zip` and ` v831-m2dock-maixpy3-0.5.1-20220701.zip` are the same version with different contents.

| Name          | Meaning                                                                                              |
| ------------- | ---------------------------------------------------------------------------------------------------- |
| maixpy3-0.5.1 | For [MaixPy3](https://wiki.sipeed.com/maixpy3) and its version is `0.5.1` , no maixhub app inside    |
| maixhub-0.5.1 | For [MaixPy3](https://wiki.sipeed.com/maixpy3) and its version is `0.5.1` , incorporates maixhub app |
| m2dock        | Image for MaixII-Dock                                                                                |
| 20220701      | Update date                                                                                          |

> These images is not the business edition, only can be burned into TF card.

## Burning the system image using Windows

We use `PhoenixCard` and `PhoenixSuit` to burn images using Windows. The first one is used for burning an image file onto a MicroSD or TransFlash (TF) card, and PhoenixSuit is used for burning the image file onto the onboard flash ROM via USB.

Only the business edition M2 model contains the flash ROM, so you will likely need the MicroSD/TransFlash card to start the system on the OpenSource edition M2.

### Preparation

- Get the image-burning tool: [PhoenixCard](https://dl.sipeed.com/shareURL/MaixII/MaixII-Dock/SDK/tools)
- Get the image file: [image file](https://dl.sipeed.com/shareURL/MaixII/MaixII-Dock/SDK/release)
- Get the SD card Formatter Tool: [SD Card Formatter](https://www.sdcard.org/downloads/formatter/eula_windows/SDCardFormatterv5_WinEN.zip)

### Burning the system image

1. Insert your MicroSD card into the reader in your computer, if the following message appears, click `Cancel`
   ![windows_format_tf](./assets/windows_format_tf.png)

2. Run `SD Card Formatter` to format your MicroSD card (aka TF card): Click `Refresh` then choose your target `card`, click `Format`

![Format SD card](./../../../assets/maixII/V831/image-20210802102810041.png)

3. Follow the steps below to complete burning the image

![burn image](./../../lichee/assets/RV/flash.png)

- Run PhoenixCard
- Click `Image` marked with ① to choose your target firmware
- Choose `Start up` marked with ② 
- Click `Burn` marked with ③ to burn the system firmware image onto your MicroSD / TF card
- Watch the `Status bar` marked with ④ to see your progress；If it's red when finished then it failed burning so you should rerun `SD Card Formatter` to format the MicroSD card (TF card) again and retry the steps above.
- Click `Close` to close PhoenixCard

## Burning the system image using Windows

### Preparation

- Install Livesuit

1. Install dkms

    ```bash
    sudo apt install dkms
    ```

2. Install libpng1.2 (It must be this version)

     ```shell
     wget http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng_1.2.54.orig.tar.xz
     tar xvf  libpng_1.2.54.orig.tar.xz
     ```

     ```shell
     cd libpng-1.2.54
     ./autogen.sh
     ./configure
     make -j8
     sudo make install
     ```

     update link binary:

     ```shell
     sudo ldconfig
     ```

3. Install **livesuit**

     ```shell
     git clone https://github.com/linux-sunxi/sunxi-livesuite.git
     cd sunxi-livesuite
     chmod +x LiveSuit.sh
     sudo ./LiveSuit.sh
     ```

### Burning the system image

- Run command `sudo livesuit` to run livesuit software, then click the red box marked in the picture below to choose your image file.

![choose firmware](./../../../zh/maixII/M2/asserts/flash_15.png)

- Connect your computer with **OTG** interface on MaixII-Dock without SD card in it, this software will show a dialog, then insert SD card into MaixII-Dock and click yes to format SD card and burning system.

![format SD card](./../../../zh/maixII/M2/asserts/flash_17.png)

- Wait until the burning is finished, then we can begin to use it.

![progress](./../../../zh/maixII/M2/asserts/flash_19.png)

![Finish](./../../../zh/maixII/M2/asserts/flash_21.png)
