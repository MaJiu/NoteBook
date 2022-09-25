[toc]

# 汇编语言

## 汇编程序的构成

Label

Directives 伪指令 没有对应的机器码 和 汇编编译器 有关

Assembly instructions 和 CPU 架构有关

Comments 

## 编译与构建

### 交叉编译 Cross Compiler

在 A 平台上编译运行在 B 平台的代码

### 编译工具链

按架构区分   LLVM 和 GNU 工具链

按执行或目标平台区分  Linux Windows Mac Android    x86 ARM

| 工具    | 功能                                                         |
| ------- | ------------------------------------------------------------ |
| as      | 汇编编译器                                                   |
| ld      | linker 链接器                                                |
| gcc     | C/C++ 编译器(驱动)                                           |
| objcopy | convert ELF executable into IMG format                       |
| objdump | utility to disassemble executables (for debugging)           |
| readelf | an useful utility to dump sections and segments in executables (for debugging) |
| gdb     | debug tool                                                   |
| make    | 构建工具                                                     |

```shell
gcc -g <...> # 带上 -g 选项
gdb program # 进入 gdb 交互界面 (gdb)
# 忘了调试命令时 使用 info 查看
```



### 编写 link script

### 编写 Makefile



# x86

## 8086



## x64

AT&T Intel

# ARM

## ARM64

GNU Assembler 

ARM v8

### ARMv8 寄存器

#### General purpose registers

x0 - x30 共计31个

#### Special registers

Zero register

Program counter

Stack pointer * 4 SP_EL0 - SP_EL3

Program Status Register SPSR_EL1 - SPSR_EL3

Exception Link Register  ELR_EL1 - ELR_EL3

#### System registers

### ARMv8 Exception levels

运行模式/工作模式/权限级别

ARM v8 的 Exception levels 类似于 ARM v7 的 processor mode

一个 Exception level 对应一个 Privilege level

每个 level 可以访问的 寄存器 也不同

| Exception level | Note                                                      |
| --------------- | --------------------------------------------------------- |
| EL0             | Normal user applications                                  |
| EL1             | Operating system kernel typically described as privileged |
| EL2             | Hypervisor                                                |
| EL3             | Low-level firmware, including the Secure Monitor.         |

Execution state  AArch64 和 AArch32

### 指令集

T32 A32 A64

mnemonics 助记符

# 参考资料

1. CSAPP 深入理解计算机系统 第三章 程序的机器级表示 第七章 链接

2. 汇编语言 王爽
3. ARM 64Bit Assembly Language   Larry D.Pyeatt
4. [bztsrc/raspi3-tutorial: Bare metal Raspberry Pi 3 tutorials (github.com)](https://github.com/bztsrc/raspi3-tutorial/)
5. [isometimes/rpi4-osdev: Tutorial: Writing a "bare metal" operating system for Raspberry Pi 4 (github.com)](https://github.com/isometimes/rpi4-osdev)

