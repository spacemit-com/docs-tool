---
sidebar_position: 1
---

# Flash Tools

## DFU Flash

Writes a system image directly to the device's onboard storage in USB DFU mode. Suitable for installing or updating the system on a single device.

### Prerequisites

- The SpacemiT Studio driver for the target platform is installed. See [Quick Start](../../quick_start.md).
- The device is connected to the computer via a USB cable.
- The device has entered flashing mode.

The procedure for entering flashing mode differs by model. Refer to the applicable user guide:

| Series | Model | User Guide |
| ---- | ----------- | -------------------- |
| K1 | MUSE Pi Pro | [User Guide](https://www.spacemit.com/community/document/info?lang=en&nodepath=hardware/eco/k1_muse_pi_pro/pi_pro_user_guide.md) |
| K1 | MUSE Pi | [User Guide](https://www.spacemit.com/community/document/info?lang=en&nodepath=hardware/eco/k1_muse_pi/pi_user_guide.md) |
| K1 | MUSE Book | [User Guide](https://www.spacemit.com/community/document/info?lang=en&nodepath=hardware/eco/k1_muse_book/book_user_guide.md) |
| K1 | MUSE Paper | [User Guide](https://www.spacemit.com/community/document/info?lang=en&nodepath=hardware/eco/k1_muse_paper/paper_user_guide.md) |
| K3 | CoM260 Kit | [User Guide](https://www.spacemit.com/community/document/info?lang=en&nodepath=hardware/eco/k3_com260/com260_user_guide.md) |
| K3 | Pico-ITX | [User Guide](https://www.spacemit.com/community/document/info?lang=en&nodepath=hardware/eco/k3_pico/root_overview.md) |

### Procedure

1. Go to **Development Tools → DFU Flash**.

   ![DFU Flash entry](../../static/flash.png)

2. The tool automatically detects connected devices in flashing mode. If the device is not detected, verify that it meets the [prerequisites](#prerequisites).

   ![Device detection](../../static/flash_0.png)

   If multiple devices are connected, use the **Select Device** drop-down to choose the target device.

   ![Multiple device selection](../../static/flash_1.png)

3. Select and download a system image.

   Click **More** to open the image library.

   ![More Images](../../static/flash_2.png)

   In the image library, select the target image:

   ![Image library](../../static/flash_3.png)

   (1) Select the board series (K1 or K3).  
   (2) Select the target OS (Bianbu, Buildroot, ROS2, or OpenHarmony).  
   (3) Select the OS version.  
   (4) Select a specific image and click **Download**.

   Image download in progress:

   ![Downloading](../../static/flash_3_1.png)

   Image download complete:

   ![Download complete](../../static/flash_3_2.png)

   Click **Local** to view previously downloaded images. To use an image file already on the computer, click **Upload Local Image**:

   ![Local image management](../../static/flash_3_4.png)

   Return to the DFU Flash screen and select the downloaded image from the **Select Image** drop-down:

   ![Select image](../../static/flash_3_3.png)

4. Click **Start Flash**.

   Confirm the settings (**Reboot after flashing** is selected by default), then click **Start Flash**.

   ![Start Flashing](../../static/flash_4.png)

   Flashing begins and progress is displayed:

   ![Flashing in progress](../../static/flash_7.png)

5. Wait for flashing to complete.

   If flashing succeeds and **Reboot after flashing** is selected, the device restarts automatically.

   ![Flashing complete](../../static/flash_8.png)

   If flashing fails, an error message is displayed:

   ![Flashing failed](../../static/flash_12.png)

### Advanced Options: Configure Partitions

To use custom partition configuration files, select **Partitions Config**:

![Configure Partitions](../../static/flash_parti_1.png)

Click **Edit Files** to open **Partition Files**:

![Edit Partition File List](../../static/flash_parti_2.png)

In **Partition Files**, add, remove, or modify partition configuration files. Click **Confirm** to return to the DFU Flash screen.

## SD Card Boot

Writes a system image to an SD card, allowing the device to boot from the card. Suitable for debugging a single device or evaluating a new OS without modifying the device's onboard storage.

### SD Card Boot Prerequisites

- The SD card is inserted into a card reader connected to the computer.
- The SD card capacity is greater than or equal to the image size.

### SD Card Boot Procedure

1. Go to **Development Tools → SD Card Boot**.

   ![SD Card Boot entry](../../static/sdcard_0.png)

2. Select the target SD card from the **Select Device** drop-down.

   ![Select SD card](../../static/sdcard_1.png)

   > If the list is empty, confirm the SD card is inserted and click the refresh button to re-detect.

3. **Flash Boot Card** is selected by default under **Select Operation**.

   > **Optional:** Select **Format SD** to format the SD card only, without writing an image.
   >
   > ![Select Format](../../static/sdcard_format_0.png)
   >
   > ![Confirm Format](../../static/sdcard_format_1.png)
   >
   > ![Format complete](../../static/sdcard_format_2.png)

4. Select the target image.

   - If no image has been downloaded, click **More** to browse and download one.
   - If an image is already available, select it from the **Select Image** drop-down.

5. Click **Execute** and wait for the image write to complete.

   Writing the boot card:

   ![Writing in progress](../../static/sdcard_6.png)

   Boot card creation complete:

   ![Boot card complete](../../static/sdcard_7.png)

6. After writing is complete, insert the SD card into the device and power on to boot from the SD card.

## SD Card Mass Production

Creates SD cards for mass production. After a production image is written to an SD card and the card is inserted into a target device, powering on the device automatically installs the system to onboard storage without manual intervention.

### SD Card Mass Production Prerequisites

- The SD card is inserted into a card reader connected to the computer.
- The SD card capacity is greater than or equal to the image size.

### SD Card Mass Production Procedure

The procedure is the same as [SD Card Boot](#sd-card-boot), with the following differences:

- In step 1, go to **Development Tools → SD Card Mass Production**.
  ![SD Card Mass Production entry](../../static/sdcard_mass_0.png)
- In step 3 under **Select Operation**, select **Flash Mass Production Card**.
  ![SD Card Mass Production](../../static/sdcard_mass_1.png)
- After step 6, insert the SD card into a target device. On power-up, the device automatically writes the system from the SD card to onboard storage.

### Comparison: SD Card Boot vs. Mass Production

| | SD Card Boot | SD Card Mass Production |
| ------ | --------- | --------- |
| System storage location | SD card | Device onboard storage |
| Behavior after SD card removal | Cannot boot | Operates normally |
| Typical use case | Debugging, evaluation | Mass production |
