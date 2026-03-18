NAME = ametest
SRCS = $(shell find -L ./ -name "*.c" -o -name "*.cpp")

override ARCH := riscv64-xs
override TOOLCHAIN := LLVM
override RVV_ENABLE := yes
override OBJDUMP_FLAGS := --mattr=+matrix-xuantie-0.6
MARCH ?= rv64gc_zba_zbb_zbc_zbs_zbkb_zbkc_zbkx_zknd_zkne_zknh_zkr_zksed_zksh_zkt_zame
CFLAGS += -Wno-unused-function -Wno-unknown-pragmas -Wno-unused-variable -Wno-implicit-function-declaration -Wno-int-conversion
CFLAGS += -Xclang -target-feature -Xclang +matrix-xuantie-0.6
# CFLAGS += -D_FORTIFY_SOURCE=0 -fno-builtin -mcmodel=medany

ifeq ($(TOOLCHAIN), LLVM)
	CFLAGS += --target=riscv64-unknown-linux-gnu
# 	CFLAGS += -mllvm --riscv-v-vector-bits-min=128
	ifeq ($(RVV_ENABLE), yes)
		MARCH := rv64gcv_zvl128b_zba_zbb_zbc_zbs_zbkb_zbkc_zbkx_zknd_zkne_zknh_zkr_zksed_zksh_zkt_zame
	else
		CFLAGS += -fno-vectorize
	endif
else
	ifeq ($(RVV_ENABLE), yes)
		MARCH := rv64gcv_zvl128b_zba_zbb_zbc_zbs_zbkb_zbkc_zbkx_zknd_zkne_zknh_zkr_zksed_zksh_zkt_zame
		CFLAGS += -ftree-vectorize
	endif
endif
include $(AM_HOME)/Makefile.app
