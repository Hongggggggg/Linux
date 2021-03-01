- netstat

- 功能：Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships

- 参数

  - -a，显示所有链接中的Socket
  - -A<网络类型>，列出该网络连接中的相关地址
  - -c，持续列出网络状态
  - -e，显示网络其他相关信息
  - -g，显示多重广播功能群组组员名单
  - -i，显示网络界面信息表单
  - -I，显示监控中的服务器的Socket
  - -n，直接使用IP，不通过域名服务器
  - -t，显示TCP连接情况
  - -u，显示UDP连接情况
  - -r，显示Routing Table

- 示例：

  - 无参数使用：

    ```bash
    netstat
    ```

  - 列出所有端口：

    ```bash
    netstat -a
    ```

  - 显示当前UDP连接状况

    ```bash
    netstat -nu
    ```

  - 显示UDP端口号的使用情况

    ```bash
    netstat -apu
    ```

  - 显示网卡列表

    ```bash
    netstat -i
    ```

  - 显示组播组的关系

    ```bash
    netstat -g
    ```

  - 显示网络统计信息

    ```bash
    netstat -s
    ```

  - 显示监听的套接口

    ```bash
    netstat -I
    ```

  - 显示所有已建立的有效连接

    ```bash
    netstat -n
    ```

  - 显示关于以太网的统计数据

    ```bash
    netstat -e
    ```

  - 显示关于路由表的信息

    ```bash
    netstat -r
    ```

  - 列出所有tcp端口

    ```bash
    netstat -at
    ```

    
