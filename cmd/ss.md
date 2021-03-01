- ss [options] [filter]

- 命令功能：ss(Socket Statistics的缩写)命令可以用来获取 socket统计信息，此命令输出的结果类似于 netstat输出的内容，但它能显示更多更详细的 TCP连接状态的信息，且比 netstat 更快速高效。它使用了 TCP协议栈中 tcp_diag（是一个用于分析统计的模块），能直接从获得第一手内核信息，这就使得 ss命令快捷高效。在没有 tcp_diag，ss也可以正常运行。

- 命令参数：

  - -n，不解析服务名称
  - -r，解析主机名
  - -a，显示所有套接字
  - -l，显示监听状态的套接字
  - -o，显示计时器信息
  - -e，显示详细的套接字信息
  - -m，显示套接字的内存使用情况
  - -p，显示使用套接字的内存使用情况
  - -i，显示TCP内部信息
  - -s，显示套接字使用概况
  - -4，仅显示IPv4的套接字
  - -6，仅显示IPv6的套接字
  - -0，显示Packet套接字
  - -t，仅显示TCP套接字
  - -u，仅显示UDP套接字
  - -d，仅显示DCCP套接字
  - -w，仅显示RAW套接字
  - -x，仅显示Unix套接字

- 示例：

  - 显示TCP连接：

    ```bash
    ss -t -a
    ```

  - 显示socket摘要

    ```bash
    ss -s
    ```

  - 列出所有打开的网络连接端口

    ```bash
    ss -l
    ```

  - 查看进程使用的socket

    ```bash
    ss -pl
    ```

  - 找出打开套接字/端口应用程序

    ```bash
    ss -lp|grep 3306
    ```

  - 显示所有UDP套接字

    ```bash
    ss -u -a
    ```

    

