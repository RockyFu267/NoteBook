# linux是如何工作的
## 计算机系统层次
+ 用户程序
+ 第三方库
+ OS库
+ 内核
+ 硬件设备

## 程序
### 什么是程序
+ 通过输入设备或者网络适配器向计算机发起请求
+ 读取内存中的指令，CPU负责运算
+ 返回输出设备或网络适配器向其他计算机返回
+ 返回第一步

### 本质是调用设备
+ 进程调用的是设备驱动程序

### cpu运行模式
#### 用户模式
+ 进程在用户模式下运行
+ 第三方库
+ OS库

#### 内核模式
+ 只有处在内核模式时，才被允许访问设备
##### 进程管理系统
##### 进程调度器
##### 内存管理系统

### 内核
+ 把核心处理整合在一起的程序就是内核
+ 管理cpu和内存各种资源，按需分配给进程
+ 内核与用户模式下运行的程序共同构成OS

### 数据交换
+ 已内存为中心，在cpu寄存器或外部存储器等各种存储之间交换

#### 文件系统
+ 为了简化--程序通过设备驱动程序访问外部存储器中的数据这一过程

### 