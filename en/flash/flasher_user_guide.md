# Flashing Tool User Manual

## 1. Download

Select the appropriate version based on your operating system:

| Resource                                     | Platform | Architecture | Download |
| -------------------------------------------- | -------- | ------------ | -------- |
| TITANTOOLS FOR WINDOWS (X86|X64) (Installer) | Windows  | X86|X64      | Download |
| TITANTOOLS FOR LINUX X64 (64-bit) (AppImage) | Linux    | X64          | Download |

## 2. Installation

### 2.1 PC Requirements

- **Operating System:** Windows or Linux
- **Storage:** At least **10 GB** free space on the C: drive (Windows) or in the **Home** directory (Linux)

### 2.2 Installing on Windows

The following steps use **Windows 11** as an example.

1. Download the latest flashing tool: **titantools_for_windows.exe**.
2. Double-click the downloaded file **titantools_for_windows_last** to start the installer.
3. If Windows asks **“Do you want to allow this app from an unknown publisher to make changes to your device?”**, click **Yes**.
4. If Windows shows **“Windows can’t verify the publisher of this driver software”**, choose **Always install this driver software**.

The following images show the installation flow.

Choose the installation directory:

![](static/locate.png)

Click **Install**, Installer running:

![](static/install.png)

Once the installation is complete, Titan Flasher can be launched by double-clicking its desktop icon.

### 2.3 Installing on Linux

The following steps use **Ubuntu** as an example.

1. Download the latest AppImage package: **titantools_for_linux.AppImage**.
2. Grant the file executable permission.
3. Double-click the AppImage to run it — no installation is required.

**Note:**
If the tool fails to start with the message
```
dlopen(): error loading libfuse.so.2
```

install the `libfuse2` package using:

```
sudo apt install libfuse2
```

## 3. Entering Flashing Mode

The following uses the JDT Space product **MUSE Pi** as an example.

**Device not powered on** (powered off):

  1. Press and hold the **Download (FDL)** button.
  2. Plug in the power cable.
  3. Release the **Download (FDL)** button.
  4. Connect a USB data cable to the flashing USB connector. The device should now be detected.

**Device already powered on** (already connected to power):

  1. Press and hold the FDL button.
  2. Short-press the Reset button.
  3. Release the FDL button.
  4. Connect a USB data cable to the flashing USB connector. The device should now be detected.

The following uses **MUSE Book** as an example.

- **Activate Fastboot mode**
  Use a SIM-eject pin to press and hold the Fastboot button hidden in the small hole on the right side of MUSE Book, then press the power button to start the device.

> *Note: Make sure the pin is fully inserted and held for more than 3 seconds.*

- **Device connection**
  Use the Type-C port near the screen (the dedicated OTG port) to connect the MUSE Book to the host computer.

## 4. Flashing Process

### 4.1 Tool Home Page

1. Open the flashing tool. If the system prompts **“Allow this app from an unknown publisher to make changes to your device?”**, choose **Yes**.
2. As shown below, the tool displays four main function modules on the right:

   - **Development Tools**: single-device flashing, SD-card boot
   - **Mass Production Tools**: multi-device flashing, create production SD card, serial number writer
   - **Online Cloud Devices**: remote device management
   - **Settings**: tool update and language selection

Click any module to enter the respective interface.

![](static/home.png)

### 4.2 Development Tools

From the home page, click **Development Tools** to enter the Development Tools interface.

![](static/dev_tool.png)

#### Single-Device Flashing

On the Development Tools page, there are two options: Single-Device Flashing and SD-Card Boot. Select **USB Download**.

![](static/usb_download.png)

Single-Device Flashing process:

1. Ensure the device has entered **Flashing Mode**.

> Note: The device must enter flashing mode before scanning, otherwise it cannot be detected.

2. Click **Scan Device** and select the target device, as shown.

![](static/scan.png)

When the device is successfully detected, the flashing serial number will appear.

![](static/detect.png)

> Note: If multiple devices exist, use the dropdown to select one.

![](static/detect2.png)

3. Select the flashing package (firmware or extracted directory).

After selecting the device, use the dropdown to choose the file source: **local file**, **local dir**, or **Network**.

![](static/file.png)

4. Click **Start Flashing** and wait.

After selecting the flashing package, the tool will show **Extracting files…**. Please wait.

![](static/start.png)

After extraction, the firmware package name appears.

![](static/packagename.png)

5. **Reboot the device after flashing completes.**

![](static/flashing.png)

Flashing completes, then reboot to enter the system.

![](static/complete.jpg)

#### SD-Card Boot

Select **SD-Card Boot** under the Development Tools interface.

> Note: Linux systems (e.g., Ubuntu) do not support the SD-Card Boot feature.

![](static/CDljby5xno6KqlxHfoJcowXsn4f.png)

SD-Card Boot process:

1. Insert an SD card and click Select **SDCard Boot Disk**

![](static/sdcard.png)

- A selection window will pop up. Choose the SD card.

  ![](static/sdselect.png)

- After selection, the SD card name will be shown.

  ![](static/sdselect2.png)

2. Select the flashing package path.

![](static/sdselect3.png)

The selected package appears as shown:

![](static/sdselect4.png)

3. Select operation type (default: Boot Card)

> Note: Burning requires formatting the SD card. Back up important data first.

![](static/bootcard.png)

4. Click **Start** and wait until finished.

![](static/start2.png)

![](static/runing.png)

#### Partition Configuration

1. Once the device and flashing firmware are selected, you may configure partition files if needed.

2. Enable partition configuration to open the selection window.

3. After selecting partition files, the following appears:

> Note: Partition names vary depending on the file. Ensure there are no conflicts.

## 5. Mass Production Tools

### 5.1 Multi-Device Flashing

Click **Multi-USB Download** under Mass Production Tools.

> Note: Multi-USB Download only supports **zip files**.

![](static/multi-usb.png)

1. Click **Select Zip File**.

![](static/zip.png)

After extraction, the file path appears here:

![](static/zip2.png)

2. Enable USB calibration mode and bind USB ports.

![](static/cali0.png)

After binding, the USB number appears:

![](static/cali1.png)

Disable USB calibration mode and wait for device detection.

![](static/cali2.png)

To unbind, re-enable calibration mode and click the button:

![](static/cali3.png)

3. Choose auto or manual flashing mode.

![](static/cali4.png)

4. Once flashing completes, close the window.

![](static/cali5.png)

5. If debugging info is enabled, the window below appears.

![](static/done.png)

### 5.2 Multi-SD Card Flashing

Note. Currently, this option is not supported on Linux systems, such as Ubuntu.

### 5.3 Serial Number Writer

1. Under Mass Production Tools, select **Key Programming**.

![](static/key.png)

2. Click **Scan Device** to detect the device serial number.

![](static/key1.png)

3. Click **Configure Custom Fields**.

![](static/key2.png)

4. Enable the fields that need to be written; disable those not needed.

![](static/key3.png)

5. Choose **Random** or **Custom**.

![](static/key4.png)

6. After configuration, click **Start Write** and wait for success.

![](static/key-start.png)

![](static/done2.png)

## 6. Online Cloud Devices

Users can manage devices remotely through this feature.

Click the option to enter the login page:

![](static/online.png)

> Note: This feature is under maintenance.

## 7. Settings

The Settings interface is shown below:

![](static/OMlubfPTToPJqlxDyjRcuRS1ncb.png)

### 7.1 Basic Settings

#### Current Workspace

The highlighted area below shows the current workspace:

![](static/setting.png)

- To change the workspace, click **Modify** and select a new location.

![](static/setting2.png)

### Cleaning Workspace Storage

1. The highlighted area below displays the current storage usage of the workspace.
   ![](static/clean.png)

2. When you click **Clean**, a confirmation dialog appears. Click **Yes** to remove all files stored in the current workspace.
   ![](static/clean2.png)

3. After cleaning, the workspace usage will show **0 GB**.
   ![](static/clean3.png)

### Automatic Cleaning

The **Automatic Cleaning** feature removes cached flashing files **when the tool is closed**.

- If this option is disabled, extracted flashing packages will remain in the workspace and may accumulate over time, consuming large amounts of disk space.
- When enabled, the tool automatically clears cached files on exit, preventing unnecessary disk usage.

![](static/autoclean.png)

### Language Switching

Click **English** or **中文** to switch the tool’s display language.

### 7.2 About – Version Update

Click **About** to view the current version of the flashing tool suite.

![](static/about.png)

Click **Check Update** to verify whether you are using the latest version.
If an update is available, a message will appear: **A new version is available. Please download the latest version!**

![](static/update.png)

![](static/update1.png)

Click **OK** to start the update process.
![](static/update2.png)
