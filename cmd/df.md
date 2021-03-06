- df [OPTION]... [FILE]...

- 功能：显示指定磁盘文件可用的空间。若未指定，则显示当前所有被挂载的文件系统的可用空间。

- 命令参数：

  - 必选参数
    - -a，全部文件系统列表
    - -h，按照k或者M或者G的方式显示，方便阅读
    - -i，显示inode信息
    - -I，只显示本地文件系统
    - --sync，在取得信息前先执行sync命令
    - -P，输出格式为POSIX
  - 可选参数
    - --block-size=<区块大小> 指定区块大小
    - -t <文件系统类型> 只显示选定文件系统的磁盘信息
    - -x <文件系统类型> 不显示选定文件系统的磁盘信息

- 实例：

  - 显示磁盘使用情况

    ```bash
    df -h
    ```

  - 显示指定类型磁盘使用情况

    ```bash
    df -t ext3
    ```

  - 列出文件系统的类型：

    ```bash
    df -T
    ```

    

  

