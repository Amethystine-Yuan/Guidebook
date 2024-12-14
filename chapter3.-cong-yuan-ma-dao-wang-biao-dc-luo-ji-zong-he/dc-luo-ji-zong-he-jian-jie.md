# DC 逻辑综合简介

DC逻辑综合将Verilog的源码转化为网表（Netlist），具体可分为以下三个阶段：&#x20;

1. 转译：将 HDL 代码转换成 DC 内部的数据库（GTECH 库 ），该数据库和工艺无关；&#x20;
2. 优化：根据设计目标（频率、面积、功耗）对电路进行优化（与工艺无关，运用布尔变换或代数变换技术），包括结构优化（Architectural level synthsis）、逻辑优化（Logic level or GTECH optimization）和门级优化（Gate-level or Mapping optimization）；&#x20;
3. 映射：在目标库中选择合适的逻辑单元（包括组合逻辑和时序逻辑），产生设计的门级电路。&#x20;

其中用到的脚本为dc.tcl、read.tcl和约束文件。本节将对这三部分依次介绍。

DC的命令为 dc\_shell，一般在运行时会通过 linux 命令保存运行日志，请同学们自行实现该功能。

{% hint style="info" %}
提示：使用 tee 命令和管道符
{% endhint %}

