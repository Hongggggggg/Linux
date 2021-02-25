- ifconfig [intervice] [options]

- 功能：查看和配置网络设备，当网络环境发生改变时可通过此命令对网络进行相应的配置

- 命令参数：

  - up，启动指定的网络设备/网卡
  - down，关闭指定的网络设备/网卡。
  - arp，设置指定网卡是否支持ARP协议。
  - -promisc，设置是否支持网卡的promiscuous模式，如果选择此参数，网卡将接收网络中发给它所有的数据包
  - -allmulti，设置是否支持多播模式，如果选择此参数，网卡将接收网络中所有的多播数据包
  - -a，显示全部接口信息
  - -s，显示摘要信息（类似netstat -i）
  - add，给指定的网卡配置IPv6地址
  - del，删除指定网卡的IPv6地址
  - <硬件地址>，设置网卡的最大传输单元（bytes）
  - mtu<字节数>，设置网卡的最大传输单元（bytes）
  - netmask<子网掩码>，设置网卡的子网掩码
  - tunel，建立隧道
  - dstaddr，设定一个远端地址，建立点对点通信
  - -broadcast<地址>，为网卡设置广播协议
  - -pointtopoint<地址>，为网卡设置点对点通讯协议
  - multicast，为网卡设置组播标志
  - address，为网卡设置IPv4地址
  - txqueuelen<长度>，为网卡设置传输队列的长度

- 示例：

  - 显示网络设备信息

    ```bash
    ifconfig
    ```

  - 启动关闭指定网卡

    ```bash
    ifconfig ens33 up/down
    ```

  - 修改MAC地址

    ```bash
    ifconfig ens33 hw ether 00:11:22:33:44:55
    ```

  - 配置IP地址

    ```bash
    ifconfig ens33 192.168.1.1
    ```

  - 启用和关闭ARP协议

    ```bash
    ifconfig eth0 arp
    ifconfig eth0 -arp
    ```

  - 设置最大传输单元

    ```bash
    ifconfig eth0 mtu 1500
    ```

    