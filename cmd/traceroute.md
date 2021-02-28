- traceroute  [option] [host]

- 功能：追踪网络数据包的路由途径

- 命令参数：

  - -d，使用Socket层级的排错功能
  - -f，设置第一个检测数据包的存活值TTL的大小
  - -F，设置物理段位
  - -g，设置来源路由网关，最多可设置8个
  - -i，使用指定的网络界面送出数据包
  - -I，使用ICMP回应取代UDP资料消息
  - -m，设置检测数据包的最大存活数值TTL的大小
  - -n，直接使用IP地址而非主机名称
  - -p，设置UDP传输协议的通信端口
  - -r，忽略普通的Routing Table，直接将数据包送到远端主机上
  - -t，设置检测数据包的TOS数值
  - -v，详细显示指令的执行过程
  - -w，设置等待远端主机回复的时间
  - -x，开启或关闭数据包的正确性检验

- 示例：

  - 正常用法：

    ```bash
    traceroute www.baidu.com
    ```

  - 跳数设置

    ```bash
    traceroute -m 10 www.baidu.com
    ```

  - 显示IP地址，不查主机名

    ```bash
    traceroute -n www.baidu.com
    ```

  - 设置6888为探测包使用的UDP端口

    ```
    traceroute -p 6888 www.baidu.com
    ```

  - 设置探测包的个数

    ```bash
    traceroute -q 4 www.baidu.com
    ```

  - 绕过正常的路由表，直接发送到主机

    ```bash
    traceroute -r www.baidu.com
    ```

  - 设置等待相应时间：

    ```bash
    traceroute -w 3 www.baidu.com
    ```

    