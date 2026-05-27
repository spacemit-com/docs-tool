sidebar_position: 2

# Flashing Tool User Manual

## 1. Download

Select the appropriate version based on your operating system:

| Resource   | Platform | Architecture | Download |
|------------|----------|------------|-----------|
| TITANTOOLS FOR WINDOWS (X86\|X64) (INSTALLER) | WINDOWS  | X86\|X64   | [Download](https://cloud.spacemit.com/prod-api/release/download/tools?token=titantools_for_windows_X86_X64)  |
| TITANTOOLS FOR LINUX X64 (64-BIT) (APPIMAGE)  | LINUX    | X64        | [Download](https://cloud.spacemit.com/prod-api/release/download/tools?token=titantools_for_linux_64BIT_APPIMAGE)  |

## 2. Installation

### 2.1 PC Requirements

- **Operating System:** Windows or Linux
- **Storage:** At least **10 GB** free space on the C: drive (Windows) or in the **Home** directory (Linux)

### 2.2 Installing on Windows

The following steps use **Windows 11** as an example.

1. Download the latest flashing tool: **titantools_for_windows.exe**.
2. Double-click the downloaded file **titantools_for_windows_last** to start the installer.
3. If Windows shows **SmartScreen can't be reached right now**, click **Run**.
    <img src="static/flasher-en-1.png" style="width: 600px;">

4. Choose install location:
    <img src="static/locate.png" alt="" width="600">  
   
    <img src="static/flasher-en-2.png" style="width: 600px;">

    Click **Install**, Installer running:  
    <img src="static/install.png" alt="" width="600">

Once the installation is complete, Titanflasher can be launched by double-clicking its desktop icon.

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
2. As shown below, the tool displays four main functional modules on the right:

   - **Development Tools**: single-device flashing and SD-card boot
   - **Mass Production Tools**: multi-device flashing, production SD card creation, and serial number writing
   - **Online Cloud Devices**: remote device management
   - **Settings**: tool updates and language selection

Click any module to enter the respective interface.

<img src="static/home.png" alt="" width="600">

### 4.2 Development Tools

From the home page, click **Development Tools** to open the Development Tools page.

<img src="static/dev_tool.png" alt="" width="600">

#### Single-Device Flashing

On the Development Tools page, two options are available: Single-Device Flashing and SD-Card Boot. Select **USB Download**.

<img src="static/usb_download.png" alt="" width="600">

The single-device flashing process is as follows:

1. Ensure the device has entered **Flashing Mode**.

    > Note: The device must enter flashing mode before scanning, otherwise it cannot be detected.

2. Click **Scan Device** and select the target device, as shown below.

    <img src="static/scan.png" alt="" width="600">

    When the device is successfully detected, the device serial number appears.

    <img src="static/detect.png" alt="" width="600">

    > Note: If multiple devices are detected, use the drop-down list to select the target device.

    <img src="static/detect2.png" alt="" width="600">

3. Select the flashing package (firmware file or extracted directory).

    After selecting the device, choose the package source from the available options: 
    - **local file**
    - **local dir**
    - **Network**

    <img src="static/file.png" alt="" width="600">

4. Click **Start Flashing** and wait for the process to complete.

    After the flashing package is selected, the tool displays **Extracting files...**. Wait for the extraction to finish.

    <img src="static/start.png" alt="" width="600">

    After extraction is complete, the firmware package name appears.

    <img src="static/packagename.png" alt="" width="600">

5. **Reboot the device after flashing completes.**

    <img src="static/flashing.png" alt="" width="600">

    After flashing is complete, power on the device again to enter the system.

    <img src="static/complete.jpg" alt="" width="600">

#### SD-Card Boot

Select **SD-Card Boot** under the Development Tools interface.

> Note: Linux systems (e.g., Ubuntu) do not support the SD-Card Boot feature.

The SD-card boot process is as follows:

1. Insert an SD card and click Select **SDCard Boot Disk**

    <img src="static/sdcard.png" alt="" width="600">

    - A selection window appears. Select the target SD card.

    <img src="static/sdselect.png" alt="" width="600">

    - After selection, the SD card name is displayed.

    <img src="static/sdselect2.png" alt="" width="600">

2. Select the flashing package path.

    <img src="static/sdselect3.png" alt="" width="600">

    The selected package path is displayed as shown below:
    <img src="static/sdselect4.png" alt="" width="600">

3. Select the operation type (default: **Boot Card**).

    > Note: Creating a boot card requires formatting the SD card. Back up important data in advance.

    <img src="static/bootcard.png" alt="" width="600">

4. Click **Start** and wait for the process to finish.

    <img src="static/start2.png" alt="" width="600">

    <img src="static/runing.png" alt="" width="600">

#### Partition Configuration

1. Once the device and flashing firmware are selected, you may configure partition files if needed.

2. Enable partition configuration to open the selection window.

3. After selecting the partition files, the configuration appears as shown below.

> Note: Partition names vary depending on the file. Ensure there are no conflicts.

## 5. Mass Production Tools

### 5.1 Multi-Device Flashing

Click **Multi-USB Download** under Mass Production Tools.

> Note: Multi-USB Download only supports **zip files**.

<img src="static/multi-usb.png" alt="" width="600">

1. Click **Select Zip File**.

   <img src="static/zip.png" alt="" width="600">

   After extraction is complete, the file path appears as shown below:

   <img src="static/zip2.png" alt="" width="600">

2. Enable USB calibration mode and bind the USB ports.

   <img src="static/cali0.png" alt="" width="600">

   After binding is complete, the USB port number appears:

   <img src="static/cali1.png" alt="" width="600">

   Disable USB calibration mode and wait for the device to be detected.

   <img src="static/cali2.png" alt="" width="600">

   To unbind a port, re-enable calibration mode and click the corresponding button:

   <img src="static/cali3.png" alt="" width="600">

3. Choose automatic or manual flashing mode.

   <img src="static/cali4.png" alt="" width="600">

4. Once flashing completes, close the window.

   <img src="static/cali5.png" alt="" width="600">

5. If debugging information is enabled, the following window appears.

   <img src="static/done.png" alt="" width="600">

### 5.2 Multi-SD Card Flashing

> **Note.** Currently, this option is not supported on Linux systems, such as Ubuntu.

### 5.3 Serial Number Writer

1. Under Mass Production Tools, select **Key Programming**.

   <img src="static/key.png" alt="" width="600">

2. Click **Scan Device** to detect the device and display its serial number.
   <img src="static/key1.png" alt="" width="600">

3. Click **Configure fields**.
   <img src="static/key2.png" alt="" width="600">

4. Enable the fields that need to be written; disable those not needed.
   <img src="static/key3.png" alt="" width="600">

5. Choose **Random** or **Custom**.
   <img src="static/key4.png" alt="" width="600">

6. After configuration, click **Start Write** and wait for success.

   <img src="static/key-start.png" alt="" width="600">
   <img src="static/done2.png" alt="" width="600">

## 6. Online Cloud Devices

This feature enables remote device management.

Click this option to open the login page:

<img src="static/online.png" alt="" width="600">

> Note: This feature is under maintenance.

## 7. Settings

### 7.1 Basic Settings

#### Current Workspace

The highlighted area below shows the current workspace:

<img src="static/setting.png" alt="" width="600">

- To change the workspace, click **Modify** and select a new location.
   <img src="static/setting2.png" alt="" width="600">

#### Cleaning Workspace Storage

1. The highlighted area below displays the current storage usage of the workspace.
   <img src="static/clean.png" alt="" width="600">

2. When you click **Clean**, a confirmation dialog appears. Click **Yes** to remove all files stored in the current workspace.
   <img src="static/clean2.png" alt="" width="600">

3. After cleaning, the workspace usage will show **0 GB**.
   <img src="static/clean3.png" alt="" width="600">

#### Automatic Cleaning

The **Automatic Cleaning** feature removes cached flashing files **when the tool is closed**.

- If this option is disabled, extracted flashing packages will remain in the workspace and may accumulate over time, consuming large amounts of disk space.
- When enabled, the tool automatically clears cached files on exit, preventing unnecessary disk usage.

<img src="static/autoclean.png" alt="" width="600">

#### Language Switching

Click **English** or **中文** to switch the tool’s display language.

### 7.2 About – Version Update

Click **About** to view the current version of the flashing tool suite.

<img src="static/about.png" alt="" width="600">

Click **Check Update** to verify whether the current version is up to date.

- If an update is available, a message will appear: **A new version is available. Please download the latest version!**

    <img src="static/update.png" alt="" width="600">

    <img src="static/update1.png" alt="" width="600">

    Click **OK** to start the update process.
    <img src="static/update2.png" alt="" width="600">

- If you are already using the latest version, the tool displays **The current version is already the latest version**.

    <img src="static/flasher-en-update.png" style="width: 600px">

## 8. Command-Line Flashing Tool (flashserver)

If the Titanflasher GUI is unavailable, or if users prefer a command-line-based flashing workflow, the **flashserver** tool can be used to perform firmware flashing operations.

flashserver provides a CLI-based flashing solution suitable for automated environments, remote terminals, and headless systems.

### 8.1 Obtaining flashserver

#### Method 1: Direct Download

Select the appropriate version for your operating system:

- [Windows version](https://cdn-resource.spacemit.com/file/flash/flashserver.exe)
- [macOS version](https://cdn-resource.spacemit.com/file/flash/flashserver.pkg)
- [Linux version](https://cdn-resource.spacemit.com/file/flash/flashserver)

#### Method 2: Export from Titanflasher

As shown below, open **Settings** in Titanflasher and click **Export Command-Line Tool** to obtain flashserver.

<img src="static/flashserver_download.png" alt="" width="800">

### 8.2 flashserver Flashing Procedure (Windows)

The flashserver workflow on macOS and Linux is generally the same as on Windows. You can follow the steps below as a reference.

1. Place the downloaded flashserver executable in the flashing package directory, as shown below.

   <img src="static/flashserver-cn-titanflasher-2.png" width="600px">

2. Connect the target development board or device.

   For instructions on entering flashing mode, refer to the section [Entering Flashing Mode](#3-entering-flashing-mode).

   Double-click the **flashserver** executable to launch the tool. Once the device is successfully detected, the following command-line window appears.

   <img src="static/flashserver-en-4.png" style="width: 600px;">

3. At the prompt `--- Enter port index or full name:`, enter the corresponding device number, for example `1`, to start flashing automatically.

   <img src="static/flashserver-en-5.png" style="width: 600px;">
