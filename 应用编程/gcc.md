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

  

