sidebar_position: 1

# Cross-Compilation Toolchain User Guide

## 1. Download

Visit the [Resource Download Center](https://www.spacemit.com/community/resources-download).

In the left navigation panel, select **Tools → Cross Compilation Toolchain**, pick the appropriate version to download.

| Toolchain Type | Description | Use Case |
|----------------|-------------|----------|
| `spacemit-toolchain-linux-glibc-x86_64-xxx` | Toolchain for Linux environments, including the glibc library | Used for Linux-based development environments with an operating system, such as Bianbu, Buildroot, or similar systems |
| `spacemit-toolchain-elf-newlib-x86_64-xxx` | Bare-metal toolchain including the newlib library | Used for bare-metal development, such as firmware for microcontroller cores or management firmware without an OS |

Most released toolchains include both LLVM and GCC, sharing the same C library. While the special releases that contain GCC only will be clearly indicated on the download page.

## 2. Installation

After extracting the toolchain package, add the `bin` directory to your system `PATH`:

```bash
export PATH=<path-to-toolchain>/bin:$PATH
```

## 3. Using the Toolchain

### 3.1 GCC Toolchain

#### Example Compilation Commands

- **Linux Toolchain:**

   ```bash
   riscv64-unknown-linux-gnu-gcc -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs spacemit.c -o spacemit.out
   ```

- **Bare-Metal Toolchain:**

   ```bash
   riscv64-unknown-elf-gcc -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs spacemit.c -o spacemit.out
   ```

#### Compilation Parameter Notes

- `-mcpu=spacemit-x60`
  Uses the X60 CPU scheduling and instruction fusion model.

- `-mcpu=spacemit-x100`
  Uses the X100 CPU scheduling and instruction fusion model.

- `-mcpu=spacemit-a100`
  Uses the A100 CPU scheduling and instruction fusion model.

- `-march=rv64gc_zba_zbb_zbc_zbs`
  Enables the GC base ISA with Bitmanip extensions.
  > Note: The `-march` option can be customized by combining extensions as needed.If not specified, the default configuration of the CPU or toolchain will be used.

- For more details, refer to the [GCC official documentation](https://gcc.gnu.org/onlinedocs/)

### 3.2 LLVM Toolchain

#### Example Compilation Commands

- **Linux Toolchain:**

  - Using `clang`:

    ```bash
    clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs -fuse-ld=lld spacemit.c -o spacemit.out
    ```

  - Alternatively, use `riscv64-unknown-linux-gnu-clang` to avoid conflicts with host system's x86 `clang`:

    ```bash
    riscv64-unknown-linux-gnu-clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs -fuse-ld=lld spacemit.c -o spacemit.out
    ```

- **Bare-Metal Toolchain:**

- Using `clang` or `riscv64-unknown-elf-clang`:

  ```bash
  clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs -fuse-ld=lld spacemit.c -o spacemit.out
  ```

#### Compilation Parameter Notes

- `-mcpu=spacemit-x60`
  Uses the X60 CPU scheduling and instruction fusion model.

- `-mcpu=spacemit-x100`
  Uses the X100 CPU scheduling and instruction fusion model.

- `-mcpu=spacemit-a100`
  Uses the A100 CPU scheduling and instruction fusion model.

- `-fuse-ld=lld`
  Uses the LLVM `lld` linker.

- `-march=rv64gc_zba_zbb_zbc_zbs`
  Enables the *GC base ISA with Bitmanip extensions.
  > Note: The `-march` option can be customized as needed. If not specified, the default CPU or toolchain configuration will be used.

- For more information, refer to the [LLVM official documentation](https://llvm.org/docs/).
