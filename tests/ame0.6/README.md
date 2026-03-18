# ame0.6 Test

Bare-metal functional test for the AME 0.6 matrix extension ISA, compiled with the LLVM toolchain targeting `riscv64-xs`.

## Build

```bash
make
```

> `ARCH=riscv64-xs`, `TOOLCHAIN=LLVM`, and `RVV_ENABLE=yes` are all forced in the Makefile and do not need to be specified manually.

Build artifacts are placed under `build/riscv64-xs/`:

- `ametest.elf` — ELF executable
- `ametest.bin` — raw binary for loading into a simulator or FPGA
- `ametest.txt` — disassembly output

## Run

Set `XS_PROJECT_ROOT` to the project root directory (`xsai-env-316/`) before running:

```bash
export XS_PROJECT_ROOT=/path/to/xsai-env-316
```

### Run on NEMU

```bash
make run-nemu
```

### Run on EMU (RTL simulation)

```bash
make run-emu
```

### Run on QEMU

```bash
make run-qemu
```

Each target delegates to the corresponding goal in `XS_PROJECT_ROOT`, passing the compiled `.bin` as the payload.
