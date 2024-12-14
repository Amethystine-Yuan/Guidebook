# 主脚本

主脚本中首先设置了search path和不同的library，包括target library、symbol library、link lirary等。

&#x20;       search path即说明了搜索的路径，当后续输入仅为文件名称时，DC将优先从search path的路径中进行寻找。

target library 为逻辑库，是将设计映射到特定工艺所使用的库，即使用目标库中的元件综合得到所设计的门级网表。库中包含了了standard cells或macro的功能、时间和电源信息。库中的文件格式为.lib或.db格式，两者所记录的内容是一样的。.lib格式是文本文件，可由Cadence家工具读取，直接打开文件阅读。而.db是Synopsys家读取的文件格式，Synopsys为了加快文件读取的速度，会把.lib转化为.db格式，.db是一个二进制不可读的文件，文件加载速度会快于.lib。在文件的命名中也可以看出一些信息，例如命名中的tt代表典型的工艺角（还可能是ff、ss），1p0v表示工作电压为1.0V，125c表示温度为125摄氏度，hvt代表高阈值电压（还可能是lvt、svt等）。

symbol library 提供 Design Vision GUI 中设计实现的图形符号，如果使用脚本模式而不使用 GUI,此库可不指定 Symbol library。

link library 为提供了门级网表实例化的基本单元，也就是门级网表实例化的元件或单元都来自该库。简单地讲，所有用到的库都要放到link library，而只用于综合的库放在target library,如ROM,PAD等不用综合的就不放在target library中。此外，link library中一般会有“_”，表示Synopsys当前已经读入的library。例如，如果存在两个文件，一个是sub.v，另一个是top.v,其中调用了sub这个模块。先将sub.v读入，然后读入top.v,这样执行link操作后，Synopsys就会找到top模块中的sub,如果link library中没有“_”，那么将会把sub当作black box,报告错误。

此外，还有非必须的synthetic library，即 Designware library ,名字上翻译是综合库，但却常称之为IP库，而不是直译。特殊的 Designware library 是需要授权的（比如使用多级流水线的乘法器），默认的标准 Designware 由 DC 软件商提供，无需指定。例如dw\_foundation.sldb 是Synopsys提供的名为Design Ware的综合库，它包含了基本的算术运算逻辑、控制逻辑、可综合存储器等IP，在综合是调用这些IP有助于提高电路性能和减少综合时间。
