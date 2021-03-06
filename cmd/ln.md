- ln [opt]... 源文件或目录 目标文件或目录

- 功能：为某一个文件在另外一个位置建立一个同步的链接，ln命令会保持每一处链接文件的同步性，不论改动哪一处，其他的文件都会发生相同的变化。

  - 硬链接：

    - 生成一个和源文件大小相同的文件。
    - 只能在同一个文件系统中创建
    - 不能给目录创建硬链接

  - 软连接：

    - 以路径的形式存在，类似windows中的快捷方式
    - 可以跨文件系统
    - 可以对一个不存在的文件名进行链接
    - 可以对目录进行链接

    

- 命令参数：

  - 必选参数
    - -b，删除，覆盖以前建立的链接
    - -d，允许超级用户
    - f，强制执行
    - -i，交互模式，文件存在则提示用户是否覆盖
    - -n，把符号链接视为一般目录
    - -s，软链接
    - -v，显示详细的处理过程

- 实例：

  - 给文件创建软链接：

    ```bash
    ln -s test.txt link_test
    ```

  - 给文件创建硬链接：

    ```bash
    ln test.txt link_test
    ```

    
