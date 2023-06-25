## ch1
- 在计算机的多级层次结构中，级别最高的是**应用语言虚拟机**
- 对于机器语言程序设计员来说，()是透明的
  - 数据表示
  - 寻址方式
  - **乘法器**
  - 乘法指令
- 冯·诺依曼结构计算机是以(**运算器**)为中心
- 计算机系统结构*不*包括()
  - **主存速度**
  - 机器工作状态
  - 信息保护
  - 数据表示
- 计算机系统结构始址机器语言程序员所看到的机器属性，即()
  - **编程所要了解的硬件组织**
  - 计算机硬件的全部组成
  - 计算机各部件的硬件实现
  - 计算机软件所要完成的功能
- 摩尔定律**18**个月翻一番
- 同构型多处理机**资源重复**
- 程序局部性包括**空间局部性**和**时间局部性**
- 虚拟机是由软件实现的机器
## ch2
- 不需要编制的数据存储空间是()
  - CPU中的通用寄存器
  - **堆栈**
  - 主存储器
  - I/O接口中的寄存器
- *不*是设计RISC机器时应当遵循的原则
  - 采用load-store结构
  - 大多数指令都采用硬连逻辑
  - 采用简单而又统一的指令格式
  - **采用多种复杂的寻址方式**
- ()不是MIPS的寻址方式
  - 偏移量寻址
  - **变址寻址**
  - **寄存器间接寻址**
  - 立即数寻址
- CPU中用来存储操作数的存储单元主要有()
  - **堆栈**
  - **寄存器**
  - 主存
  - **累加器**
- 常用的数据表示有()
  - 数组
  - 堆栈
  - **定点数**
  - **浮点数**
- 指令中表示寻址方式的方法有()
  - 由专用的寄存器描述
  - **设置专门的地址描述符**
  - 由操作数描述
  - **编码在操作码中**
- 寄存器访问速度比存储器*快*
- 控制指令时有条件改变控制流时，称之为分支指令，无条件->跳转
- 规整性包括对称性、均匀性
- 采用多种寻址方式可以减少程序的指令条数，但可能增加计算机的实现复杂度和指令CPI
## ch3
- 非线性流水线的特征
  - 流水线的个功能段在不同运算中可以由不同连接
  - **一次运算中要重复使用流水线中的某些功能段**
  - 流水线中某些功能段在各次运算中的作用不同
  - 一次运算中使用流水线中的多个段
- MIPS的指令流水线中，可能发送的冲突：**写后读**
- 写后写冲突是由**输出相关**引起的
- ```
    ADD.D F6, F0, F12
    SUB.D F8, F6, F14
    ```
  - **数据相关**
- 在WB段，RR型的ALU指令的操作为()
  - `Regs[MEM/WB.IR[rd]] <- MEM/WB.ALUo`
- 可以采用**换名技术**和**指令调度技术**解决名相关
- 任务流入流出顺序是否相同，流水线可以划分为**顺序流水线**和**乱序/异步流水线**
- 流水技术适合于大量重复的时序过程
- 如果流水线中各段时间相等，则各段的效率等于整条流水线的效率(错)
- 存在相关一定产生冲突(错)
## ch4
- 可以通过寄存器重命名来消除的冲突由**WAW/WAR**
- 在基于硬件的前瞻执行中，指令流出时，正确的()
  - **必须有空闲的保留站&空闲的ROB项**
  - **把该ROB项的编号放入保留站r**
  - **把保留站和该ROB项置为“忙”**
  - **如果该指令需要的操作数已经就绪，九八他们送入保留站**
- 动态分支预测技术要解决好以下问题
  - **如何根据历史信息来预测分支去向**
  - 如何实现流水处理
  - **预测错误时如何恢复原来的现场**
  - **如何记录分支的历史信息**
- r是分配给当前指令的保留站或缓冲器单元，当前流出的指令是浮点运算指令，RS为保留站，且$Q_i[rs] \neq 0$，则要进行的操作为
  - $RS[r].Q_j$ <- 0
  - <b>$RS[r].Q_j$ <- $Q_i[rs]$</b>
  - <b>$RS[r].Op$ <- $Op$</b>
  - $RS[r].V_j$ <- $Regs[rs]$
- 静态调度是在程序的执行过程中依靠专门的硬件对代码进行调度(X)
- Tomasulo算法中，只要指令队列头部的指令要求的保留站有空闲，该指令就可以流出(对)
- 保持正确的异常行为就是要保证精确异常(错)
- 基于硬件的前瞻执行所增加的硬件不是太多(错)
- BTB的方法也是在ID段获得分支目标地址(错)
## ch5
- CPU访问存储系统时，在最靠近CPU的存储器中找到所需信息的概率为**命中率**
- Cache大小为8块、主存大小为16块，直接映像，块号为10的主存块可以放**2**
- Cache-主存是为了弥补主存的**速度**不足
- 与全相联映像相比，组相联优点？？
  - 命中率高
  - 主存利用率高
  - **目录表小**
  - 块冲突概率低
- FIFO选择**最早调入的块**作为被替换的块
- 在存储层次中，平均访问时间与()有关
  - 每位价格
  - **命中率**
  - **不命中开销**
  - **命中时间**
- 降低Cache不命中率的方法包括
  - **提高相联度**
  - **编译器预取**
  - **伪相联**
  - 虚拟Cache
- 给定Cache容量，增加块大小总能降低Cache不命中率(错)
- 在存储层次中，越靠近CPU的存储器速度越快(对)
- 高位交叉编址，$A=i \times m + j$，其中j和i分别是该单元的体号和体内地址(错)
## ch6
- **RAID3**是位交叉奇偶校验磁盘阵列
- 用户程序通过**访管指令**调用通道
- 通道的功能不包括
  - 在数据传输过程中完成必要的格式变换
  - **进行中断处理**
  - 执行通道程序
  - 给出外设中要进行的读/写操作的数据所在的地址
- 选择通道的最大流量$\frac{1}{\frac{T_s}{n} + 1}$
- 反应存储外设可靠性的参数有
  - 可靠性
  - 可用性
  - 可信性
- 实现RAID的方式有
  - **软件方式**
  - **子系统方式**
  - **阵列卡方式**
  - 排列方式
- RAID5是块交叉分布奇偶校验磁盘阵列(对)
- 数据传送完成后，通道不需要向CPU发I/O中断请求(错)
- RAID01是线进行条带存放，再进行镜像(对)
- 选择通道每次连接一台外设，是一次把所有数据都传送完(对)
## ch8
- 监听协议中，若Cache块的当前状态Shared，写访问，状态变为**独占**
- 目录协议中，包含所访问的存储单元及其目录项的节点**宿主结点**
- 有一个采用目录协议的多处理机，a/c/d分别读访问Cache11，该块的目录项中的共享集为<b>{a, c, d}</b>
- 本地结点发给宿主结点的消息包括
  - **Invalidate(K)**
  - **RdMiss(P, K)**
  - DReply(D)
  - **WtMiss(P, K)**
- 消息传递通信机制的主要优点
  - **通信是显式的**
  - **硬件更简单**
  - 采用大家所熟悉的共享存储器模型开发应用程序
  - **同步很自然地与发送消息相关联**
- 分布式存储多处理机中，每个结点由()组成
  - **I/O**
  - **CPU**
  - **互联网络接口**
  - **存储器**
- 写更新式目前最常用(错)
- 细粒度多线程的主要缺点式减慢了单个线程的执行(对)
- 在采用DSM的多处理机系统中，是采用消息传递通讯机制(错)
- 分布式存储器多处理机中，存储器在物理上是分布的。它只支持构建规模较小的多处理机系统(错)
## 考试
- RISC是复杂指令集(错)
- 在分支目标缓冲器方法中，是拿当前的指令地址与分支目标缓冲器中的所有地址标识进行比较(对)
- 把流水线技术应用于运算的执行过程，就形成了宏流水线(错)
- 全并行：同时对许多字的全部位或部分位进行处理(对)
- 延迟分支能否带来好处完全取决于编译器能否把有用的指令调度到延迟槽中(对)
- DMA是在外设与存储器之间建立数据通路，使它们可以直接传送数据，而不必经过运算器(对)
- 多核是通过在单个芯片上实现多个处理器来提高性能(对)
- 指令流是指机器执行的指令序列(对)
- 如果指令j与指令i之间存在名相关，则这两条指令之间一定有数据流动(错)
- 通道程序是由管理程序来编制的(对)
- DSM把物理上分离的所有存储器作为一个统一的共享逻辑空间进行编址(对)
- 多流出技术是指每个时钟周期流出多条指令(对)
- 具体的一次相关是否会导致实际冲突以及该冲突会带来多长的停顿，是流水线的属性(对)
- 在实现上，“Cache—主存”主要由专用硬件实现，“主存—辅存”主要由软件实现(错)
- 指令调度有两种方法：静态调度，动态调度(对)
- 在基于目录的协议中，本地结点把请求发给宿主结点中的目录，再由目录控制器有选择地向远程结点发出相应的消息，使远程结点进行相应的操作，并进行目录中状态信息等的更新(对)
- 汇编语言程序员不透明的是
  - 条件码寄存器
  - 指令寄存器
  - 主存地址寄存器
  - 程序计数器
- 发出访问请求的结点成为**本地结点**
- 磁盘设备适宜于连接到数组多路通道或字节多路通道
- ROB的每一项由()字段组成
- 导致结构冲突的原因
  - 功能部件不是完全流水
  - 资源份数不够