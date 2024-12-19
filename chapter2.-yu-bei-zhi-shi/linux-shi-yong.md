# Linux 使用

### **基础教学**

对于不熟悉虚拟机中 Linux 环境的同学，我们复用 [NJU 计算机系统基础课程实验的讲义](https://nju-projectn.github.io/ics-pa-gitbook/ics2021/linux.html)，请这些同学阅读 FAQ 栏下的 “Linux 入门教程” 和 “ man 入门教程”。

{% hint style="info" %}
**学习 Linux 基本使用**

我们给大家墙裂推荐 MIT 的 Linux 工具使用系列课程：  [The Missing Semester of Your CS Education](https://missing-semester-cn.github.io/) 中文版。通过学习这些课程，你将会了解到如何使用 Linux 中的工具来方便地完成各种任务，这将大大提升你的工作效率。这些工具包括

* Shell工具和脚本
* 编辑器 (Vim)
* 数据整理
* 命令行环境
* 版本控制 (Git)

此外， [B站上](https://www.bilibili.com/video/BV1x7411H7wa)有这门公开课的视频供大家参考。
{% endhint %}

### **进阶命令**

本节介绍了一些进阶的命令，在本课程中较为有用。

**后台运行与进程管理**

对于服务器而言，screen 类型的命令可以使程序在后台运行，而不需要前台显示。这避免了由于网络错误导致运行的程序发生意外中断，使长时间的程序运行更为安全。screen 的命令可以创建一个额外的窗口，这一窗口在前台运行时属性为 Attached，在后台运行时属性为 Detached。类似的后台运行方法还有 TMUX，感兴趣的读者可自行了解。

下面是关于该命令的一些使用方法：

```bash
$ screen -ls                     ### 查看当前的 screen 名称
$ screen -S <name>               ### 创建一个新的 screen 界面并进入
$ Ctrl+A+D                       ### 退出当前的界面，后台运行程序
$ Ctrl+A+Esc                     ### 使滚轮控制当前界面的视图，Esc取消
$ screen -r <name>               ### 进入一个指定的 screen 界面
$ quit                           ### 结束当前界面并退出    
$ screen -X -S <name> quit       ### 强制删除目标 screen 界面
$ screen -D -r <name>            ### 登录一个 Attached 的界面 
```

### **查看存储大小**

部分软件使用时会输出巨大体积的文件，这很有可能导致虚拟机上可用存储空间不足。查看磁盘的使用情况和文件夹大小通常使用 df 和 du 命令，具体的例子如下所示，其中 -h 选项增强了可读性（human readable），-s 选项对结果进行了总结。

```bash
$ df -h               ### 查看磁盘使用情况
$ du -sh *            ### 查看当前文件夹大小
```

### **自我检测**

下面是一些基本的 Linux 命令，如果你对部分命令存在疑惑，请通过 man 命令或 --help 选项查看手册。

```bash
$ cd test/              
$ cd ..                   
$ touch <name>.txt        
$ mkdir <dir_name>       
$ rm <name>.txt         
$ ls -a            
$ cp -r <path1> <path2>  
$ mv <path1> <path2>  
$ pwd                  
```
