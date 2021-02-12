- 基本格式：目标：依赖

  ​						命令

  - 示例：

    ```makefile
    Test_Make: test.o add.o max.o
    	@gcc test.o add.o max.o -o Test_Make
    test.o:test.c
    	gcc -c test.c -o test.o
    add.o:add.c
    	gcc -c add.c -o add.o
    max.o:max.c
    	gcc -c max.c -o max.o
    #。。。。
    ```

    #号代表注释，@取消相关回显信息

- 伪目标：在makefile文件中有时候执行一些不需要有依赖命令的目标称为伪目标

  ```makefile
  .PHONY:clean
  clean:
  	rm *.o Test
  ```

  通过.PHONY修饰后，可直接使用make clean来执行对应的命令

- 变量：

  - $^，所有的依赖文件
  - $@，生成的目标文件
  - $<，第一个依赖文件