# proj7-terminus
### 项目描述
当前大学本科学生做OS实验的一个问题是对底层硬件不够了解，如果能够通过实践实现一个能运行OS的CPU模拟器，那在后续对CPU与OS的交互会理解更加清晰和透彻。如果这个模拟器还能提供相应的调试分析功能，那么会大大简化对OS学习和实验的难度。

为此，我们采用了如下的规划思路：
- 我们选择了能帮助OS设计实现的RISC-V硬件模拟平台
- 在软件编程语言方面，我们选择了Rust编程语言
- 尽量比较全面地支持与OS相关的硬件模块

当前项目实现源码：
- https://github.com/shady831213/terminus
- https://github.com/shady831213/trantor

### 所属赛道

2021全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求
- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生（2021年春季学期或之后本科毕业的大一~大四的学生）
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2021全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

李旸
- github https://github.com/shady831213/
- email shady831213@126.com

### 难度

初等~中等

### 特征（已经完成）
- [x] RV32/64I
- [x] MADFC
- [x] M/S/U priviledge
- [x] Pass all riscv_tests
- [x] CLINT and Timer
- [x] HTIF console
- [x] FDT generation
- [x] Multi Cores
- [x] Boot Linux(up)
- [x] Emu mode binary
- [x] Boot Linux(smp)
- [x] PLIC
- [x] VirtIO console
- [x] VirtIO disk
- [x] VirtIO network
- [x] framebuffer
- [x] VirtIO keyboard
- [x] VirtIO mouse
- [x] Cosimulation with HDL

### 文档


### License

- MIT license

## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

在现有terminus的基础上，进一步完成如下目标：

### 第一题：分阶段重新实现terminus

- 该题目请参考[trantor](https://github.com/shady831213/trantor), 帮你一步一步实现自己的模拟器
- 与导师协商，形成一系列的小步骤，参考目前的代码，重新按小步骤实现RISC-V模拟器
- 在每个步骤完成后，能够有测试用例，并尽量与OS课程中涉及的内容相关
- 撰写实验设计与分析文档

### 第二题：支持调试能力

- 对terminus增加基于OPENOCD+GDB的调试功能
- 能够使用cargo的测试框架通过[riscv-test/debug](https://github.com/riscv/riscv-tests/tree/master/debug) 的所有test
- 能够通过GDB/LLDB来在terminus上对APP(U态)、OS(S态)、SBI（M态）进行源码级调试
- 能够跨U/S/M态综合调试APP/OS/SBI
- 撰写实验设计与分析文档

### 第三题：支持动态分析
- 在SMP/多核模式下，能分析死锁情况
- 能记录并分析系统出现crash时，模拟器保存的最近的N条指令的机器执行状态，帮助定位出错原因
- 在SMP/多核模式下，能快速重现并分析同步互斥异常的情况

### 第四题：支持对新硬件的模拟

- 支持对Kendryte K210开发板的模拟
- 支持对SFIVE开发板的模拟

### 第五题：支持任意一种sbi实现
- 移植一种sbi实现，例如[opensbi](https://github.com/riscv/opensbi)，到terminus仿真器
- 可以通过该sib实现 boot linux
- 可参考[terminus_bl](https://github.com/shady831213/terminus_bl)

### 第六题：支持其他操作系统
- 任选其它操作系统，例如[rcore](https://github.com/rcore-os/rCore)、[zephyr](https://github.com/zephyrproject-rtos/zephyr), 可以在terminus仿真器上运行

### 第七题：支持riscv vector extension
- 在terminus上增加RVV
- 能够使用cargo的测试框架通过[riscv-test](https://github.com/riscv/riscv-tests) 中的vector测试 

### 第八题: 支持和verilog/systemverilog模型协同仿真
- 通过ffi+dpi，使terminus可以运行在verilog/systemverilog环境中
- 可以在verilog/systemverilog环境中，控制terminus，指定特定core执行特定步长，可以出发terminus的中断，可以获取terminus的状态等
- 任选rtl simulator, 如verilator, vcs, xrun等
- 可以尝试实现verilog/systemverilog的device + terminus的协同仿真
- 可参考[terminus_cosim](https://github.com/shady831213/terminus_cosim), [vfw_rs](https://github.com/shady831213/vfw_rs), [mailbox_rs](https://github.com/shady831213/mailbox_rs)
