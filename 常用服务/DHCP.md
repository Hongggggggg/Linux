- 文章：[DHCP](https://www.zutuanxue.com/home/4/5_257)

- DHCP介绍：

  ​	DHCP(Dynamic Host Configuration Protocol，动态主机配置协议)，通常被应用在局域网络环境中，主要作用是集中的管理、分配IP地址，使网络环境中的主机动态的获得IP地址、Gateway地址、DNS服务器地址等信息，并能够提升地址的使用率。由于DHCP是一个UDP协议，所以运行起来更加高效。

  ​	DHCP协议采用客户端/服务器模型(C/S模型)，服务端可以为客户端提供IP、掩码、网关、主机名、DNS等信息。客户端只需将IP获得方式设置为自动获取即可。

  目前可以提供DHCP服务的设备有很多，比如:

  - DHCP服务器(windows server、linux)
  - 硬件路由器
  - 家用宽带路由

- DHCP工作原理

  - 工作方式：

    ​	IP获得需要通过发广播来实现客户端和服务器的通信，所以DHCP只能工作在局域网。

  - 工作原理解析：

    ​	1、Client：向网络中发送广播，通过自己的UDP协议的68号端口向网络中发送DHCP Discover包，用来寻找网络中的DHCP Server.类似于你在你的公司大喊一声:"谁是公司老板"一样的道理。

    ​	2、Server：局域网中的所有DHCP服务器都能收到该Client发送的广播包，然后DHCP Server会检查自己的IP池中(也叫做作用域)是否还有可用IP可以分发。如果有的话，会直接将这个IP地址从池中拿出来，避免在发给别的客户端，并且通过自己的UDP协议的67号端口给Client发一个响应包DHCP Offer,同样通信是采用广播的方式，明确告诉其可以提供哪个IP给Client使用。类似于公司的几个老板都在公司喊了一声：“我是X老板，我有时间在哪个办公室接待你”。

    ​	3、Client：Client会收到局域网中的所有DHCP服务器发给自己的DHCP Offer包，默认选一个最优的DHCP Server进行IP获取（在这里就是第一个发送给他DHCP Offer的服务器算作最优）。然后继续向网络中通过UDP的68号端口发广播DHCP Resquest，明确指定DHCP Server IP地址和需要租用的IP地址,告诉它要从他这里获得IP信息。自然其他DHCP Server也能收到广播，确认不从自己这里拿IP信息后，会将上步从IP池中拿出来的IP在释放到池中，以便别人使用。类似于你在公司大喊一声：“李老板，我找你接待”，那么其他老板刚才计划接待你的时间就会被释放出来，用于接待别的客户。

    ​	4、Server：被确认的DHCP Server就会通过其UDP协议的67号端口发送DHCP ACK确认包，采用广播将IP、掩码、网关、DNS等信息还有IP租约一起发送给DHCP Client，Client确认IP可用后，根据IP租约开始计算使用时间。类似于李老板把你请进他的办公室，开始和你聊天，并计算聊天时间为30分钟，开始倒计时。

  - 计算机获得IP的时间点：

    ​	a、计算机开机

    ​	b、网卡接通网络

    ​	c、重启网卡服务

  - 租约更新阶段：

    ​	a、租约完成1/2

    ​	b、租约完成7/8

    ​	c、租约到期

  

- DHCP服务器安装（ubuntu）：

  ```bash
  sudo apt install isc-dhcp-server
  ```

  - 相关配置文件：

    ​	dhcp配置文件：/etc/dhcp/dhcpd.conf 

  - DHCP启动：

    ```bash
    systemctl enable dhcpd
    systemctl start dhcpd
    #注意：可能发现无法启动DHCP服务，原因是DHCP在启动的时候检查配置文件，发现并没有有效作用域（和服务器同网段的作用域）。
    ```

    
  
- 保留地址：

  ​	将某些IP保留并与MAC地址绑定，当有设备申请IP时，根据MAC地址匹配，将对应的IP分给它，以此来保证每次向DHCP服务器请求IP地址的时候不会改变IP。可以通过修改DHCP服务器中的租约文件，来设置保留地址。

  实现方式：

  ​	在配置文件/etc/dhcp/dhcpd.conf末尾添加以下内容
  ​		host print {         
  ​			hardware ethernet 00:0C:29:1A:F8:C7;
  ​			fixed-address 192.168.11.252;
  ​		}

  host print    host为指令，print是个随意设置的名字。
  hardware ethernet 指定以太网网卡MAC地址。
  fixed-address 指定要绑定的IP。
  当MAC地址为00:0C:29:1A:F8:C7的设备来获取IP地址的时候,就会将192.168.11.252这个IP地址分配给它

  

- 超级作用域

  将两个或两个以上的不同网段的作用域合成的一个作用域就叫做超级作用域。

  