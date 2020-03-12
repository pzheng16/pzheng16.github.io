---
layout:     post
title:      Parallel Computing
subtitle:   C++/C
date:       2020-03-11
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Parallel
---

## CPU cache 对程序的影响 （Matrix)

```c++
/*square1.cpp*/
/*未经优化的矩阵乘法程序*/
#include 
using namespace std;
#define N 1000
int a[N][N] = {0}, b[N][N] = {0}, c[N][N] = {0};
int main() {
    int i, j, k;
    for (i = 0; i < N; i++) {
        for (j = 0; j < N; j++) {
            a[i][j] = i+j;
            b[i][j] = i+j;
        }
    }
    for (i = 0; i < N; i++) {
        for (j = 0; j < N; j++) {
            for (k = 0; k < N; k++) {
                c[i][j] += a[i][k] * b[k][j];
            }
 
        }
    }
}
```
```c++
/*square2.cpp*/  
/*优化过的矩阵乘法程序*/  
#include   
using namespace std;  
#define N 1000  
int a[N][N] = {0}, b[N][N] = {0}, c[N][N] = {0};  
int main() {  
    int i, j, k;  
    for (i = 0; i < N; i++) {  
        for (j = 0; j < N; j++) {  
            a[i][j] = i+j;  
            b[i][j] = i+j;  
        }  
    }  
    for (i = 0; i < N; i++) {  
        for (k = 0; k < N; k++) { // 先固定k
            for (j = 0; j < N; j++) {  
                c[i][j] += a[i][k] * b[k][j];  
            }  
  
        }  
    }  
}
```

square1.cpp中因为第三层循环（最内层循环）是对k进行循环，因此b[k][j]是对b逐列进行访问。我们知道内存中**二维数组是以行为单位连续存储的**，逐列访问将会每次跳1000*4(bytes)。**根据cpu cache的替换策略**，将会有大量的cache失效。

因此square2.cpp将j循环和k循环交换位置，这样就保证了
```c++
c[i][j] += a[i][k] * b[k][j];
```
这条语句中k和i是固定的，这样对j的访问就是某一行的，
对内存的访问是连续的，**增加了cache的命中率，**大大提升了程序执行速度。

平时写程序时，**也应当尽量使cpu对内存的访问，是尽可能连续的。**

## PC IR

PC: program counter --> points to next instruction address 用来指出下一条指令在主存储器中的地址。

IR: instruction register
当执行一条指令时，首先把该指令从主存读取到数据寄存器中，然后再传送至指令寄存器。


地址寄存器（Address Register，AR）用来保存CPU当前所访问的主存单元的地址。

累加寄存器通常简称累加器（Accumulator，AC），是一个通用寄存器。为ALU提供一个工作区，可以为ALU暂时保存一个操作数或运算结果。

Condition Codes: s a collection of status flag bits for a processor.
Zero Flag: Indicates that the result of an arithmetic or logical operation (or, sometimes, a load) was zero.

C:
CPSR的第29位是C，进位标志位。一般情况下,进行无符号数的运算。
加法运算：当运算结果产生了进位时（无符号数溢出），C=1，否则C=0。
减法运算（包括CMP）：当运算时产生了借位时（无符号数溢出），C=0，否则C=1

我们知道，当两个数据相加的时候，有可能产生从最高有效位向更高位的进位。由于这个进位值在32位中无法保存，我们就只是简单的说这个进位值丢失了。其实CPU在运算的时候，并不丢弃这个进位制，而是记录在一个特殊的寄存器的某一位上。ARM下就用C位来记录这个进位值

V:
overflow 正数 + 正数 为负数 溢出
负数 + 负数 为正数 溢出
正数 + 负数 不可能溢出 

## Cache: Introduction

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/parallel/2.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/parallel/3.png)

Cache holds **fixed sized blocks**(e.g., 64 bytes)

当没有在cache中找到的时候，**就从memory读入到cache**，这时候cache需要make room, delete other data (LRU, least recently used)

#### Cache 有用的原因，即使很小 256 KB

**Locality of Reference:**

- **Spatial Locality:**
If a memory address is referenced, chances are good a location near that one will be referenced soon 

- **Temporal locality:**
If a memory location is referenced now, chances are good it will be referenced again soon in the near future

#### Things that tend to yield poor locality
Large arrays where elements accessed “randomly”
Large dynamically allocated data structures (malloc)
Excessive use of function calls (e.g., system calls)

#### Content Addressable Memory (hashing)

**key-value**

**key:** MM address; Data: contents M[A]

**Cache:** 16 bits address + 16 bits Data

**HashFunction:** map a memory address to a cache memory address

**one Block:** 16 bits = one word

**Direct Mapped Cache:** one to one
**Fully Associative Cache:** ont to all
**K-way Set Associate Cache:** one to k possible locations in the cache

**associativity 提高**，missing更少，但是访问速度减慢，因为可能存在多个位置，这是个balancing的问题。一般使用 1， 2， 4， 8

#### Replacement Policy

**Cache Block:** atomic unit of data stored in cache

LC-3 example: block = 1 word = 2 bytes

##### LRU replacement

Least Recently Used 
Special Case: 2 Way set associative
- LRU implement by remembering the most recently used (MRU) block (1 bit)

#### 虚拟内存 virtual memory
use main memory as a "cache" for storage on disk

each "block" is called a 'page' (4KB or 8 KB typical)

In principle, programs that use more memory than the amount of physical main memory on the machine!!

Virtual memory used to keep programs executing on the same machine from interfering with each other

虚拟内存不只是“用磁盘空间来扩展物理内存”的意思——这只是扩充内存级别以使其包含硬盘驱动器而已。把内存扩展到磁盘只是使用虚拟内存技术的一个结果，它的作用也可以通过覆盖或者把处于不活动状态的程序以及它们的数据全部交换到磁盘上等方式来实现

虚拟内存是计算机系统内存管理的一种技术。它使得应用程序认为它拥有连续可用的内存（一个连续完整的地址空间），而实际上，它通常是被分隔成多个物理内存碎片，还有部分暂时存储在外部磁盘存储器上，在需要时进行数据交换.

虚拟内存将主存看成是一个磁盘的高速缓存，主存中只保存活动区域，并根据需要在磁盘和主存之间来回传送数据。

从概念上来说，虚拟内存被组织成为一个由存放在**磁盘上的 N 个连续的字节大小的单元组成的数组，**也就是字节数组。每个字节都有一个唯一的虚拟地址作为数组的索引

![img](https://images2017.cnblogs.com/blog/918357/201711/918357-20171108184518059-1211588113.png)


![img](https://images2017.cnblogs.com/blog/918357/201711/918357-20171108184841731-1270993019.png)

虚拟内存可以用来：
1. 隔离开不同程序，防止修改到其他程序
2. 程序运行地址不确定，不同次加载位置不确定
3. 内存使用率低下

分页这个技术仍然是一种虚拟地址空间到物理地址空间映射的机制。但是，粒度更加的小了。单位不是整个程序，而是某个“页”，一段虚拟地址空间组成的某一页映射到一段物理地址空间组成的某一页。

正是因为有了分页的概念，**程序的换入换出就可以以页为单位了**。那么，为什么就可以只换出某一页呢？实际上，不是为什么可以换出某一页，而是可以换出CPU还用不到的那些程序代码、数据。但是，把这些都换出到磁盘，万一下次CPU就要使用这些代码和数据怎么办？又得把这些代码、数据装载进内存。性能有影响对吧。所以，**我们把换入换出的单位变小，变成了“页”** 这样对性能影响减少。

### 总结：分页好处

1. **分页是为了解决RAM利用率不高的问题。有了分页，就可以把RAM看成Disk的Cache，LRU的代码（页）就可以加载到disk上，从而可以在RAM上执行更经常的页**
2. **为了不影响性能，把页变小，这样就可以每次加载一小部分。**

### Cache Read

If the processor finds that the memory location is in the cache, a cache hit has occurred. However, if the processor does not find the memory location in the cache, a cache miss has occurred. In the case of a cache hit, the processor immediately reads or writes the data in the cache line. For a cache miss, the cache allocates a new entry and copies data from main memory, then the request is fulfilled from the contents of the cache.

## Multiprocessor (Uniform Memory Access Architecture)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/parallel/5.png)

### Cache Coherence

- **Write Invalidate:** on write, **delete the block** in other caches holding that block of memory; 即使只修改了一部分，整个block还是会被delete.十分的不高效

- **Write update:** on write, update other caches that hold that block of memory

##### How to know which has a copy


- broadcast cache operations (bus)
**Bus-based systems:** monitor operations on the global bus

- **Directory-based system**
Directory indicates which other caches hold a copy

##### False Sharing

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/parallel/6.png)

Each Read/Write sequence on C[i] will results in a cache miss and an invalidation operation, resulting in performance

different shared variable map to the same block.--> false sharing

**同一个block里面variable的访问是没有区别的。writeInvalidate 肯定是不能用的。update的方法不高效，因为要copy。**

**要保证shared variables 被不同thread访问的时候，要放在不同的block里面**。

**去除false sharing,用 private variable, 来替代 C[i] 共享 variable**


## Cache: L1, L2, L3

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/parallel/1.png)

![img](https://pic3.zhimg.com/80/v2-67d45432d4c2a0e85c9376b27a038a7c_1440w.jpg)

三级缓存（包括L1一级缓存、L2二级缓存、L3三级缓存）都是集成在CPU内的缓存，它们的作用都是作为CPU与主内存之间的高速数据缓冲区，L1最靠近CPU核心；L2其次；L3再次。运行速度方面：L1最快、L2次快、L3最慢；容量大小方面：L1最小、L2较大、L3最大。CPU会先在最快的L1中寻找需要的数据，找不到再去找次快的L2，还找不到再去找L3，L3都没有那就只能去内存找了

### Cache 不能做的太大
太大的话访问也就变慢了，即使本身访问很快，物理方面。另外成本也很高，尤其对于CPU的一级缓存

### L1 Cache

一级缓存其实还分为一级数据缓存（Data Cache，D-Cache，L1d）和一级指令缓存(Instruction Cache，I-Cache，L1i)，分别用于存放数据及执行数据的指令解码，两者可同时被CPU访问，减少了CPU多核心、多线程争用缓存造成的冲突，提高了处理器的效能。

### L2 Cache
L2 比 L1 慢，因为 L1物理上离CPU核心更近。而且L2容量更大。

### L3 Cache 多核共享

#### DRAM vs SRAM

DRAM 所占硅面积大，但是速度快。