- nc [-46bCDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl] [-m minttl] [-O length] [-P proxy_username] [-p source_port] [-q seconds] [-s source] [-T keyword] [-V rtable] [-W recvlimit] [-w timeout] [-X proxy_protocol] [-x proxy_address[:port]] [destination] [port]

- 功能：nc（netcat）是一个短小精悍、功能实用、简单可靠的网络工具，主要有如下作用：

  - 端口侦听，nc 可以作为 server 以 TCP 或 UDP 方式侦听指定端口；
  - 端口扫描，nc 可以作为 client 发起 TCP 或 UDP 请求；
  - 机器之间传输文件；
  - 机器之间网络测速。

  ​	nc 实际上是 ncat 的软链接。ncat 是为 `Nmap: https://nmap.org/`(Network Mapper) 项目编写的，是 Nmap 套件中的一员，它旨在成为可靠的后端工具，可立即为其他应用程序和用户提供网络连接。ncat 不仅可以使用 IPv4 和 IPv6，还可以为用户提供几乎无限的潜在用途。

- 参数：

  - -4/6，强制只使用IPv4/IPv6地址
  - -D，在套接字上启用调试
  - -d，不从stdin读取
  - -k，强制nc在当前连接完成后继续侦听另一个连接。注意如果不试用-l选项，则使用此选项是错误的
  - -l，指定nc应该侦听传入的连接，而不是启动到远程主机的连接，将此选项与 -p、-s 或 -z 选项结合使用是错误的。此外，使用 -w 选项指定的超时将被忽略。
  - -n，不要在任何指定的地址、主机名或端口上执行任何DNS或服务查找
  - -r，随机选择端口和目标端口，而不是按照系统分配的顺序或范围内的顺序选择它们
  - 启用RFC2385 TCP MD5签名选项
  - -t，使 nc 发送 RFC 854 DON'T 和 WON'T 响应 RFC 854 的 DO 和 WILL 请求。这使得使用 nc 编写 telnet 会话脚本成为可能
  - -u，指定使用unix域套接字
  - -v，显示命令执行过程
  - -z，表示zero，只扫描侦听守护进程，而不向它们发送任何数据，此选项与 -l 选项结合使用是错误的
  - -C，发送CRLF作为换行符
  - -i，interval，指定发送和接收的文本之间的延迟时间间隔。还可指定连接到多个端口之间的延迟时间
  - -p，指定nc应使用的源端口，但须受特权限制和可用性限制。将此选项与 -l 选项结合使用是错误的。
  - -s，设置本地主机送出数据包的 IP 地址。注意将此选项与 -l 选项结合使用是错误的
  - -T，指定连接的 IP 服务类型(TOS)。有效值是标记 ''lowdelay'', ''throughput'', ''reliability''，或以 0x 开头的 8 位十六进制值
  - -w，如果连接和 stdin 空闲超过指定秒数，则连接将被关闭。-w 标志对 -l 选项没有影响。缺省不超时
  - -X proxy_protocol
     请求 nc 在与代理服务器对话时使用指定的协议。支持的协议是 “4”(SOCKsv.4)、“5”(SOCKV.5) 和 “connect”(HTTPS proxy)。如果未指定协议，则使用 SOCKS v.5
  - -x proxy_address[:port]
     使用指定代理服务器地址和端口连接到主机。如果未指定端口，则使用代理协议的已知端口（SOCKS为1080，HTTPS为3128）
  - 控制参数：
    - -l，指定 nc 将处于侦听模式。指定该参数，则意味着 nc 被当作 server，侦听并接受连接，而非向其它地址发起连接
    - -p PORT，指定 nc 使用的源端口
    - -s ，指定发送数据的源 IP 地址，适用于多网卡机器
    - -u，指定 nc 使用 UDP 协议，默认为 TCP
    - -v，输出交互或出错信息
    - -w，超时秒数，后面跟数字 
    - -z，表示 zero，扫描时不发送任何数据

- 示例：

  - 监听本地端口：

    - 假设在当前命令行终端A进行监听:

      ```bash
      nc -vl 8888
      ```

    - 在另外一个命令行终端B，同样使用nc发起连接：

      ```bash
      nc -v 127.0.0.1 8888
      ```

      如果在终端B输入内容，那么终端A将收到终端B发送的内容并打印到标准输出

  - 利用nc之间的连接进行文件传输

    - receiver：

      ```bash
      nc -l 8888 > received.txt
      ```

    - sender:

      ```bash
      nc 127.0.0.1 8888 < file.txt
      ```

      receiver 接收完毕，会自动退出监听。