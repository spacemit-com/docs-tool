# Cross-Compilation Toolchain User Guide

## 1. Download

Visit:
**[https://archive.spacemit.com/toolchain/](https://archive.spacemit.com/toolchain/)**

Download the toolchain version that matches your development environment.

### Toolchain Types

| Toolchain Type    | Description    | Typical Use Case   |
| ------------------- | -------------- | ----------------|
| `spacemit-toolchain-linux-glibc-x86_64-xxx` | Linux toolchain with glibc       | Application development in a Linux environment |
| `spacemit-toolchain-elf-newlib-x86_64-xxx`  | Bare-metal toolchain with newlib | Bare-metal or firmware development             |

### File Size Reference

| File Size | Notes                                                               |
| --------- | ------------------------------------------------------------------- |
| 400 MB+   | Includes both LLVM and GCC compilers. Choose this if you need LLVM. |
| 100 MB+   | Includes only GCC. Use this if GCC alone meets your requirements.   |

## 2. Installation

After extracting the toolchain, add its `bin` directory to your system `PATH`:

```bash
export PATH=<path-to-toolchain>/bin:$PATH
```

## 3. Using the Toolchain

### 3.1 GCC Toolchain

#### Example Compilation Commands

**Linux Toolchain:**

```bash
riscv64-unknown-linux-gnu-gcc -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs spacemit.c -o spacemit.out
```

**Bare-Metal Toolchain:**

```bash
riscv64-unknown-elf-gcc -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs spacemit.c -o spacemit.out
```

#### Parameter Notes

- `-mcpu=spacemit-x60`
  Enables the x60 scheduling model and Fusion optimizations.
- `-march=rv64gc_zba_zbb_zbc_zbs`
  Enables Bitmanip extensions. You may adjust extensions as needed.
- For more details, refer to the **GCC documentation**: [https://gcc.gnu.org/onlinedocs/](https://gcc.gnu.org/onlinedocs/)


### 3.2 LLVM Toolchain

#### Example Compilation Commands

**Linux Toolchain:**

Using `clang`:

```bash
clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs_zicbop \
  -mllvm -cache-line-size=64 -mllvm -prefetch-distance=128 \
  -fuse-ld=lld spacemit.c -o spacemit.out
```

Alternatively, to avoid conflicts with the system x86 `clang`:

```bash
riscv64-unknown-linux-gnu-clang -O2 -mcpu=spacemit-x60 \
  -march=rv64gc_zba_zbb_zbc_zbs_zicbop \
  -mllvm -cache-line-size=64 -mllvm -prefetch-distance=128 \
  -fuse-ld=lld spacemit.c -o spacemit.out
```

**Bare-Metal Toolchain:**

Using `clang` or `riscv64-unknown-elf-clang`:

```bash
clang -O2 -mcpu=spacemit-x60 -march=rv64gc_zba_zbb_zbc_zbs_zicbop \
  -mllvm -cache-line-size=64 -mllvm -prefetch-distance=128 \
  -fuse-ld=lld spacemit.c -o spacemit.out
```

#### Parameter Notes

- `-mcpu=spacemit-x60`
  Uses x60 scheduling and Fusion information.
- `-fuse-ld=lld`
  Uses the LLVM `lld` linker.
- `-march=rv64gc_zba_zbb_zbc_zbs_zicbop`
  Enables Bitmanip and other optional extensions.
- `-mllvm -cache-line-size=64`
  Sets cache line size to 64 bytes.
- `-mllvm -prefetch-distance=128`
  Sets prefetch distance to 128.
- More information is available in the **LLVM documentation**: [https://llvm.org/docs/](https://llvm.org/docs/)


