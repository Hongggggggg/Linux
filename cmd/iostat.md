- iostat  [参数]  [时间]  [次数]

- 功能：查看CPU、网卡、tty设备、磁盘等设备的活动情况和负载信息

- 命令参数：

  -  -C，显示 CPU使用情况
  -  -d，显示磁盘使用情况
  -  -k，以kb为单位
  -  -m，以M为单位
  -  -N，显示LVM磁盘阵列信息
  -  -n，显示NFS使用情况
  -  -p[磁盘] 显示磁盘和分区的情况
  -  -t，显示终端和CPU的信息
  -  -x，显示详细信息
  -  -V，显示版本信息

- 示例：

  - 显示所有设备负载情况：

    ```bash
    iostat
    ```

  - 定时显示所有信息

    ```bash
    iostat 2 3 #每2s刷新，显示3次
    ```

  - 显示指定磁盘信息

    ```bash
    iostat -d sda1
    ```

  - 显示tty和CPU信息

    ```bash
    iostat -t
    ```

  - 查看TPS和吞吐量信息

    ```bash
    iostat -d -k 1 1
    ```

  - 查看设备的使用率(%util)、响应时间(await)

    ```bash
    iostat -d -x -k 1 1
    ```

  - 查看cpu状态

    ```bash
    iostat -c 1 3
    ```

    

