---
sidebar_position: 1
---

# 烧录工具

## 单机烧录

通过 USB 刷机模式将系统镜像直接写入设备的内置存储，适用于单台设备的系统安装或更新。

### 前置条件

- 已安装对应平台的 SpacemiT Studio 驱动（参考[快速入门](../../quick_start.md)）
- 设备已通过 USB 线连接至电脑
- 设备已进入刷机模式

各设备进入刷机模式的方式有所不同，请参考对应的用户使用指南：

| 系列 | 型号 | 进入刷机模式参考 |
| ---- | ----------- | -------------------- |
| K1 | MUSE Pi Pro | [用户使用指南](https://www.spacemit.com/community/document/info?lang=zh&nodepath=hardware/eco/k1_muse_pi_pro/pi_pro_user_guide.md) |
| K1 | MUSE Pi | [用户使用指南](https://www.spacemit.com/community/document/info?lang=zh&nodepath=hardware/eco/k1_muse_pi/pi_user_guide.md) |
| K1 | MUSE Book | [用户使用指南](https://www.spacemit.com/community/document/info?lang=zh&nodepath=hardware/eco/k1_muse_book/book_user_guide.md) |
| K1 | MUSE Paper | [用户使用指南](https://www.spacemit.com/community/document/info?lang=zh&nodepath=hardware/eco/k1_muse_paper/paper_user_guide.md) |
| K3 | CoM260 Kit | [用户使用指南](https://www.spacemit.com/community/document/info?lang=zh&nodepath=hardware/eco/k3_com260/com260_user_guide.md) |
| K3 | Pico-ITX | [用户使用指南](https://www.spacemit.com/community/document/info?lang=zh&nodepath=hardware/eco/k3_pico/root_overview.md) |

### 操作步骤

1. 进入 **开发工具 → 单机烧录**

   ![单机烧录入口](../../static/flash.png)

2. 工具自动检测已连接的设备（设备已进入刷机模式参考[前置条件](#前置条件)章节）

   ![设备检测](../../static/flash_0.png)

   若同时连接了多台设备，可通过下拉菜单选择需要烧录的目标设备。

   ![多设备选择](../../static/flash_1.png)

3. 选择并下载目标镜像

   点击 **更多镜像**，进入镜像库

   ![更多镜像](../../static/flash_2.png)

   在镜像库中选择目标镜像：

   ![镜像库](../../static/flash_3.png)

   (1) 选择开发板系列（如 K1 或 K3）  
   (2) 选择目标系统（如 Bianbu、Buildroot、ROS2、OpenHarmony）  
   (3) 选择系统版本  
   (4) 选择具体镜像，点击 **下载** 开始下载

   镜像下载中：

   ![下载中](../../static/flash_3_1.png)

   下载完成后，关闭镜像库窗口：

   ![下载完成](../../static/flash_3_2.png)

   点击**本地**可查看已下载的本地镜像列表。若需使用电脑中已有的镜像文件,可点击**本地上传**按钮进行上传:

   ![本地镜像管理](../../static/flash_3_4.png)

   返回烧录界面，从下拉列表中选择已下载的镜像：

   ![选择镜像](../../static/flash_3_3.png)

4. 点击 **开始刷机**

   确认设置后（默认勾选 **完成后重启设备**），点击 **开始刷机**

   ![开始刷机](../../static/flash_4.png)

   系统开始烧录，显示烧录进度：

   ![烧录进度](../../static/flash_7.png)

5. 等待烧录完成

   烧录成功后，若已勾选 **完成后重启设备**，设备将自动重启并进入系统。

   ![烧录完成](../../static/flash_8.png)

   若烧录失败，将显示错误信息：

   ![烧录失败](../../static/flash_12.png)

### 高级选项：配置分区

若需自定义分区文件，可勾选 **配置分区**：

![配置分区](../../static/flash_parti_1.png)

点击 **编辑文件列表**，进入 **分区文件列表** 进行编辑：

![编辑分区文件列表](../../static/flash_parti_2.png)

在分区文件列表中，可以添加、删除或修改分区配置文件。配置完成后，点击 **确定** 返回烧录界面。

## SD 卡启动

将系统镜像写入 SD 卡，设备从 SD 卡启动。适用于单台设备调试或试用新系统，不影响设备内置存储的内容。

### SD 卡启动 — 前置条件

- SD 卡已插入电脑读卡器
- SD 卡容量 ≥ 镜像大小

### SD 卡启动 — 操作步骤

1. 进入 **开发工具 → SD 卡启动**

   ![SD 卡启动入口](../../static/sdcard_0.png)

2. 在 **选择设备** 下拉菜单中选择目标 SD 卡

   ![选择 SD 卡设备](../../static/sdcard_1.png)

   > 若列表为空，请确认 SD 卡已插入读卡器，并点击右侧刷新按钮重新检测。

3. 在 **选择操作** 中已默认选择 **烧录启动卡**

   > **可选：** 选择 **格式化** 可仅对 SD 卡进行格式化，不写入镜像。
   >
   > ![选择格式化](../../static/sdcard_format_0.png)
   >
   > ![确认格式化](../../static/sdcard_format_1.png)
   >
   > ![格式化完成](../../static/sdcard_format_2.png)

4. 选择目标镜像

   - 若未下载镜像，点击 **更多镜像**，浏览并下载目标镜像
   - 若已有下载镜像，可以下拉选择目标镜像

5. 点击 **执行**，等待写入完成

   系统开始制作启动卡：

   ![制卡中](../../static/sdcard_6.png)

   制卡完成：

   ![制卡成功](../../static/sdcard_7.png)

6. 写入完成后，将 SD 卡插入设备，上电后即可从 SD 卡启动

## SD 卡量产

批量制作量产用 SD 卡，适用于生产线场景。将量产镜像写入 SD 卡后，插入目标设备上电即可自动完成系统安装，无需手动操作。

### SD 卡量产 — 前置条件

- SD 卡已插入电脑读卡器
- SD 卡容量 ≥ 镜像大小

### SD 卡量产 — 操作步骤

操作步骤与 [SD 卡启动](#sd-卡启动) 基本一致，区别在于：

- 第 1 步进入 **开发工具 → SD 卡量产**
  ![SD 卡量产入口](../../static/sdcard_mass_0.png)
- 第 3 步**选择操作**时选择 **烧录量产卡**
  ![SD 卡量产](../../static/sdcard_mass_1.png)
- 第 6 步完成后，将 SD 卡插入待量产设备，上电后设备自动将系统从 SD 卡烧录至内置存储

### 量产与启动的区别

| 对比项 | SD 卡启动 | SD 卡量产 |
| ------ | --------- | --------- |
| 系统运行位置 | SD 卡 | 设备内置存储 |
| 拔卡后 | 无法启动 | 正常运行 |
| 适用场景 | 调试、试用 | 批量生产 |
