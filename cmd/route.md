- route [-CFvnNee] [-A family |-4|-6]

- 功能：显示或设置IP路由表

- 命令参数：

  - -v，显示详细操作信息
  - -n，不解析名字
  - -C，显示路由缓存
  - add，添加新路由
  - del，删除一条路由
  - netmask，添加一个网络路由时，需要使用子网掩码
  - gw，路由数据包通过网关
  - metric，设置路由跳数
  - Command，指定运行命令
  - Destination，指定该路由的网络目标
  - mask Netmask指定与网络目标相关的子网掩码

- 示例：

  - 显示当前路由

    ```bash
    route
    route -n
    ```

  - 添加/设置网关

    ```bash
    route add -net 224.0.0.0 netmask 240.0.0.0 dev eht0 #增加一条244.0.0.0的路由
    ```

  - 屏蔽一条路由：

    ```bash
    route add -net 224.0.0.0 netmask 240.0.0.0 reject #增加一条屏蔽的路由，目的地址为224.x.x.x将被拒绝
    ```

  - 删除路由记录：

    ```bash
    route del -net 224.0.0.0 netmask 240.0.0.0
    route del -net 224.0.0.0 netmask 240.0.0.0 reject
    ```

  - 添加和删除默认网关

    ```bash
    route del default gw 192.168.120.240
    route add default gw 192.168.120.240
    ```

    

  