---
sidebar_position: 1
---

# Device Management

## Overview

The Device Management panel centrally manages all connected development boards. It supports simultaneous connection of multiple devices, status monitoring, and quick switching.

## Supported Devices

| Series | Models |
|------|------|
| K1 | MUSE Pi Pro、MUSE Pi、MUSE Book、MUSE Paper |
| K3 | CoM260 Kit、Pico-ITX |

## Device Connection

The following connection methods are supported:

| Connection Method | Use Case | Description |
|---------|---------|------|
| USB | Flashing and local debugging | Direct USB cable connection; no configuration required |
| SSH | Daily development and file synchronization | Remote network connection; the device must be connected to a network |

### Before Connection

When no device is connected, the home page displays an empty state:

![No device connected](../static/device.png)

Alternatively, a device that was previously connected may be displayed as offline:

![Device offline](../static/device_04.png)

### Successful Connection

After a device is connected successfully, the home page displays detailed information about the current device:

![Device connected](../static/initial_01.png)

## Device Operations

![Device operations panel](../static/device_00.png)

### Device Information

After a device is connected successfully, the following information is available:

- Device series and serial number
- Currently installed operating system, such as Bianbu
- Device connection method, such as ADB
- Online/offline status
- CPU utilization, in real time
- Used memory / total memory
- Used storage / total storage

### Quick Actions

The bottom of the device panel provides shortcut buttons for common operations:

- **[Terminal](./terminal.md#terminal-sessions)**: Opens a terminal session for the device
- **[Files](./terminal.md#file-management)**: Opens device file management
- **[Serial Connection](./dev_tools/system_tools.md#serial-connection)**: Communicates with the device over a serial connection for low-level debugging and log viewing
- **Remote Desktop**: Accesses the device graphical interface through VNC/RDP
  ![](../static/remote.png) 
- **IDE**: Opens the device integrated development environment in Studio
  ![IDE](../static/ide.png) 

### Rename Device

Connected devices can be assigned custom names to distinguish them when managing multiple devices:

![Rename device](../static/device_01.png)

### New Device

To add a device, click **+ New Device** and follow the steps in the **Connect Your Device** dialog to connect a local device.
At the bottom of the dialog, select either USB or SSH as the connection method.

![New device](../static/device_03.png)

## Activity

The Activity page consolidates two types of information:

![Activity page](../static/device_02.png)

- **Operation Log**: Historical operation logs for the current device, including package name, operation method, execution time, and success/failure status. Click **View All** in the upper-right corner to expand the complete history.
- **Latest News**: Platform-provided update information
