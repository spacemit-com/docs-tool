sidebar_position: 3

# JTAG 调试工具使用手册

## 1. 下载

- **OpenOCD 下载路径**：<u>[https://archive.spacemit.com/tools/openocd](https://archive.spacemit.com/tools/openocd)</u>
- **GDB**：包含在交叉编译工具链中，请参考[《交叉编译工具链使用手册》](https://developer.spacemit.com/documentation?token=S66mw1ouRio4dUkqGvkcw7LEnJh)

## 2. 配置 JTAG 接口

K1 系列板子都内置了 JTAG 调试功能，要使其正常工作，需要 **设置硬件** 和 **配置 USB 驱动**。

以 J-Link 为例，具体步骤如下。

### 2.1 配置硬件

- **步骤一**：打开 J-Link 的外壳，将其中的跳线帽拔下，使得 J-Link 不对外供电。
- **步骤二**：连接 JTAG 信号，检查引脚是否被使用，参考文档 [MUSE Pi 用户使用指南](https://developer.spacemit.com/documentation?token=ZugWwIVmkiGNAik55hzc4C3Ln6d) 中 **JTAG 调试接口** 信息。

### 2.2 配置 USB 驱动

#### Windows

- **步骤一**：从 [Zadig 官网](https://zadig.akeo.ie/) 下载 Zadig 工具并运行
- **步骤二**：在 Zadig 工具中，进入 **Options** 菜单中选中 **List All Devices**。
- **步骤三**：检查设备列表，选择 J-Link 设备，更新成 WinUSB 驱动。

<img src="static/KWz4bKN0eoVbAJxsjeMcVQmonSc.png" alt="" width="600">

- **步骤四**：安装成功后，在设备管理器的通用串行总线设备中能看到 J-Link 设备。

> 注：如果存在多个驱动（例如 SEGGER 原生驱动），再次插入 J-Link 后可能会自动选择了别的驱动，则需要从计算机的可用驱动程序列表中选择回 WinUSB 驱动以更新驱动程序。

#### Linux

- **步骤一**：设置 OpenOCD 所支持 USB 设备的访问权限，将 [udev 规则文件](https://github.com/riscv-collab/riscv-openocd/blob/riscv/contrib/60-openocd.rules) 复制到 `/etc/udev/rules.d` 目录中。
- **步骤二**：执行以下命令刷新 udev 规则：

```bash
udevadm control --reload
```

- **步骤三**：重新插拔 J-Link 使之前的改动生效。

## 3. 运行 OpenOCD

- **步骤一**：解压缩下载的 OpenOCD 文件。
- **步骤二**：双击运行 `bin` 目录下的 `spacemit_k1_2x4` 脚本启动 OpenOCD。
- **步骤三**：如需修改运行参数，可编辑对应的脚本，以 Linux 版本为例：

```bash
#!/bin/bash

SCRIPT_DIR="../share/openocd/scripts"

./openocd -c "set CORES 8" -f $SCRIPT_DIR/interface/jlink.cfg -f $SCRIPT_DIR/target/spacemit-k1.cfg -c "gdb_port 1024"
```

- `-f` 选项后跟的是 J-Link 适配器和 K1 的配置文件。
- `-c` 选项是 OpenOCD 的配置项目，如配置了 GDB 的调试端口号为 1024，以及通过修改 `CORES` 变量设置调试核心数。

## 4. 使用 GDB 调试

使用 `riscv64-unknown-linux-gnu-gdb`，输入以下命令建立 GDB 与 OpenOCD 的连接：

```bash
target remote <ip>:<port>
```

### 4.1 使用 GDB 命令调试

- 输入 `info threads` 查看 8 个线程是否已进入调试模式，每个线程代表一个 CPU 核。随后正常使用标准 GDB 命令调试即可。

<img src="static/WHchbmCwVoh4j0xtY4bczMt0nNb.png" alt="" width="600">

- 例如，查看 CPU 核 `k1.cpu.3` 的 RISC-V 寄存器信息，可输入 `thread 4` 切换到 CPU 核 `k1.cpu.3`，然后输入 `info all-registers`。
  ```bash
  thread 4
  info all-registers
  ```

<img src="static/Cuj8bNpw1oDk4IxGxN8c9TO5nAh.png" alt="" width="500">

### 4.2 使用 OpenOCD 命令调试

- 在 GDB 中通过 `monitor` 命令调用 OpenOCD 命令，输入以下命令查看 8 个 CPU 核是否已进入 halted 状态：

  ```bash
  monitor targets
  ```
- 随后正常使用 OpenOCD 命令调试即可。。
- 例如，查看 CPU 核 `k1.cpu.3` 的 RISC-V 寄存器信息，可输入 `monitor targets 3` 切换到 CPU 核 `k1.cpu.3`，然后输入 `monitor reg` 。

```bash
monitor targets 3
monitor reg
```

<img src="static/ZCRUbDKaTokD4RxRvtFcuItynMh.png" alt="" width="400">
