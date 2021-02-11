- GDB(GUN symbolic debuger) 是GUN 发布的程序调试开发工具

- 对可执行文件进行-g选项的编译处理，可以使可执行文件具有调试信息

  ```bash
gcc -g test.c -o Test_GBD
  ```

  使用-g选项编译后可执行文件会相对大一些，这是因为可执行文件中存在相应的调试信息

- 启动gdb调试

  ```bash
  gdb Test_GBD
  (gdb) b main #在main设置一个断点
  (gdb) run #开始运行
  ```

- 在（gdb）标签后面输入gdb命令来调试可执行文件，常用命令如下:

  - gbd 可执行文件名，启动GDB
  - run/r，开始运行
  - step/s，单步运行(进入子程序)
  - next/n，单步运行(不进入子程序)
  - continue/c，继续运行
  - list/l，查看程序
  - break/b 函数名或行号，设置断点
  - info break/ i b，查看所设置的断点信息
  - delete断点号，删除断点
  - print/p，查看变量值，也可通过print来修改变量值
  - finish，运行程序直到当前函数结束
  - watch 变量名，监控变量
  - quit/q，退出GDB
  - info all-registers，查看寄存器的值
  - bt，显示堆栈信息
  - bt full，显示所有局部变量

  

