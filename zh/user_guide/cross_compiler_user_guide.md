sidebar_position: 1

# 交叉编译工具链使用手册

## 1. 下载

访问 [资源下载中心](https://www.spacemit.com/community/resources-download)

左侧导航中选择 `工具` - `交叉编译工具链`，再选择适合的版本进行下载。

<table>
<tbody>
<tr>
<td><strong>工具链类型</strong></td>
<td><strong>描述</strong></td>
<td><strong>适用场景</strong></td>
</tr>
<tr>
<td>`spacemit-toolchain-linux-glibc-x86_64-xxx`</td>
<td>Linux 环境工具链，包含 glibc 库</td>
<td>适用于 Linux 环境开发。带操作系统的，如基于Bianbu, Buildroot等开发，一般均选择此工具链</td>
</tr>
<tr>
<td>`spacemit-toolchain-elf-newlib-x86_64-xxx`</td>
<td>裸环境工具链，包含 newlibc 库</td>
<td>适用于裸机环境开发，如开发小核固件，开发无OS的管理固件</td>
</tr>
</tbody>
</table>

一般发布的工具链版本会同时带LLVM和GCC，共用C库。特殊版本只带GCC的，会在下载页面标注。


## 2. 安装

将工具链解压后，将 `bin` 目录添加到系统的 `PATH` 环境变量中：

```bash
export PATH=<工具链解压路径>/bin:$PATH
```

## 3. 工具链使用

### 3.1 GCC 工具链

#### 编译命令参考

- **Linux 环境工具链**：

  ```bash
  riscv64-unknown-linux-gnu-gcc -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs spacemit.c -o spacemit.out
  ```
- **裸环境工具链**：

  ```bash
  riscv64-unknown-elf-gcc -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs spacemit.c -o spacemit.out
  ```

#### 编译参数说明

- `-mcpu=spacemit-x60`：使用 x60 调度和 Fusion 信息。
- `-mcpu=spacemit-x100`：使用 x100 调度和 Fusion 信息。
- `-mcpu=spacemit-a100`：使用 a100 调度和 Fusion 信息。
- `-march=rv64gc_zba_zbb_zbc_zbs`：启用 gc 和 bitmanip 扩展指令。注意 march 参数可按实际需要启用的扩展进行组合。不指定则使用cpu默认或工具链默认配置。
- 更多信息可参考 [GCC 官方文档](https://gcc.gnu.org/onlinedocs/)。

### 3.2 LLVM 工具链

#### 编译命令参考

- **Linux 环境工具链**：

  - 使用 `clang` 命令

  ```bash
  clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs -fuse-ld=lld spacemit.c -o spacemit.out
  ```

  - 如果与本机的 x86 `clang` 冲突，可以使用 `riscv64-unknown-linux-gnu-clang`

  ```bash
  riscv64-unknown-linux-gnu-clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs -fuse-ld=lld spacemit.c -o spacemit.out
  ```
- **裸环境工具链**：

  - 使用 `clang` 或 `riscv64-unknown-elf-clang` 命令

  ```bash
  clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs -fuse-ld=lld spacemit.c -o spacemit.out
  ```

#### 编译参数说明

- `-mcpu=spacemit-x60`：使用 x60 调度和 Fusion 信息。
- `-mcpu=spacemit-x100`：使用 x100 调度和 Fusion 信息。
- `-mcpu=spacemit-a100`：使用 a100 调度和 Fusion 信息。
- `-fuse-ld=lld`：使用 `lld` 链接器。
- `-march=rv64gc_zba_zbb_zbc_zbs`：启用 gc 和 bitmanip 扩展指令。注意 march 参数可按实际需要启用的扩展进行组合。不指定则使用cpu默认或工具链默认配置。
- 更多信息可参考 [LLVM 官方文档](https://llvm.org/docs/)。

