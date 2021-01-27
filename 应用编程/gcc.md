- 编译的基本流程![编译流程](.\image\编译流程.jpg)

1. 预处理阶段：主要对源文件进行文件包含和预处理语句的分析处理；
2. 编译阶段：把预处理完的.i文件进行一系列词法分析、语法分析、语义分析以及优化后生成相应的汇编代码文件；
3. 汇编阶段：使用汇编器将汇编代码转换成机器可以执行的指令并生成.o文件；
4. 链接阶段：使用链接器把所有的目标文件和库文件链接起来放在合适的位置生成.out可执行文件。



- gcc简单体验：

  ```bash
  sudo apt install gcc   安装gcc
  ```

  创建test.c，内容如下：

  ```c
  #include <stdio.h>
  
  void main(void)
  {
      printf("Hello World\r\n");
  }
  ```

  编译test.c:

  ```bash
  gcc test.c -o test
  ```

  运行可执行文件test:

  ```bash
  ./test
  ```

  运行结果：

  ```bash
  Hello World
  ```

  

- 预编译  -E 选项：

  ​	GCC的 -E 选项实现源文件到 **.i** 文件的预编译处理过程 : 
  
  ​	主要用于处理一些带有\#的代码等，比如宏\#define、条件编译\#if，\#endif、\#pragma；同时也包括注释的剔除，以及include展开和系统预定义宏的替换(如 \_\_LINE\_\_, \_\_FILE\_\_)等处理
  
  ```bash
  gcc -E test.c -o test.i
  ```
  
  

- 编译  -S 选项：

  ​	生成对应平台的 **.S** 汇编文件

  ```bash
  gcc -S test.c -o test.s
  ```
  



- 汇编  -c 选项：

  ​	生成 .o 目标文件

  ​	最终生成的.o文件是一种中间文件，在Linux中其格式也是ELF，仅仅只是没有进行链接，所以其内容与最终的目标文件几乎是一样的。

  ​	可执行文件就是我们常说的由.bss段、.text段、.data段等组成的文件了，当然该文件就不能用常规的文本打开阅读了，而要借助一些命令行分析，如objdump、readelf等。

  ​	可通过objdump -h来简单的打印各个段的信息

  ```bash
  gcc -c test.c -o test.o
  ```

  ```bash
  objdump -h test.o
  ```

  

- 链接过程：

  创建add.c，代码如下:

  ```c
  int add(int a, int b)
  {
      return (a + b);
  }
  ```

  修改test.c代码如下：

  ```c
  #include <stdio.h>
  
  #define STRING  "Hello World\r\n"
  
  int add(int a, int b);
  
  void main(void)
  {
      printf(STRING);//打印Hello World
  
      printf("%d\r\n", add(1, 2));
  }
  ```

  分别生成 .o 文件：

  ```bash
  gcc -c add.c test.c
  ```

  链接：

  ```bash
  gcc test.o add.o -o HelloWorld
  ```

  