- lsof [options] [file]

- 功能：用于查看进程打开的文件，打开文件的进程，进程打开的端口(TCP、UDP)。找回/恢复删除的文件

  lsof可以打开的文件有：

  - 普通文件
  - 目录
  - 网络文件，系统的文件
  - 字符或设备文件
  - 共享库
  - 管道
  - 链接
  - 其他类型的文件

- 命令参数：

  - -a，列出打开文件存在的进程
  - -c<进程名>，列出指定进程所打开的文件
  - -g，列出GID号进程详情
  - -d<文件号>，列出占用该文件号的进程
  - +d<目录>，列出目录下被打开的文件
  - +D<目录>，递归列出目录下被打开的文件
  - -n<目录>，列出使用NFS的文件
  - -i<条件>，列出符合条件的进程
  - -p<进程号>，列出指定进程号所打开的文件
  - -u，列出UID号进程详情

- 示例：

  - 查看谁正在使用/bin/bash

    ```bash
    lsof /bin/bash
    ```

  - 递归查看某个目录的文件信息

    ```bash
    lsof test/test1
    ```

  - 列出某个用户打开的文件信息

    ```bash
    lsof -u username
    ```

  - 列出某个进程所打开的文件信息

    ```bash
    lsof -c mysql
    ```

  - 列出多个进程多个打开的文件信息

    ```bash
    lsof -c mysql -c apache
    ```

  - 列出某个用户以及某个进程所打开的文件信息

    ```bash
    lsof -u test -c mysql
    ```

  - 列出某个用户外的被打开的文件信息

    ```bash
    lsof -u ^root #不显示root用户的信息
    ```

  - 显示某个进程打开的文件

    ```bash
    lsof -p 1
    lsof -p 1,2,3 #多个进程
    lsof -p ^1 #除了1进程
    ```

  - 列出所有网络连接

    ```bash
    lsof -i
    ```

  - 列出所有tcp/udp网络连接信息

    ```bash
    lsof -i udp
    lsof -i tcp
    ```

  - 列出谁在使用某个端口

    ```bash
    lsof -i:1234
    lsof -i udp:55
    lsof -i tcp:80
    ```

  - 列出某个用户所有活跃的网络端口

    ```bash
    lsof -a -u hammer -i
    ```

  - 列出所有网络文件系统

    ```bash
    lsof -N
    ```