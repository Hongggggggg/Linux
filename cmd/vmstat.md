- vmstat [options] [delay [count]]

- 功能：显示虚拟内存的信息

- 命令参数：

  - -a, --active				active/inactive memory
  - -f, --forks                  number of forks since boot
  - -m, --slabs                slabinfo
  - -n, --one-header     do not redisplay header
  - -s, --stats                  event counter statistics
  - -d, --disk                   disk statistics
  - -D, --disk-sum          summarize disk statistics
  - -p, --partition \<dev>  partition specific statistics
  - -S, --unit \<char>      define display unit
  - -w, --wide                 wide output
  - -t, --timestamp       show timestamp

- 示例：

  - 显示虚拟内存使用情况

    ```bash
    vmstat
    ```

  - 显示活跃和非活跃内存

    ```bash
    vmstat -a 2 5
    ```

  - 查看系统已经fork了多少次

    ```bash
    vmstat -f
    ```

  - 查看内存使用的详细信息

    ```bash
    vmstat -s
    ```

  - 查看磁盘的读/写

    ```bash
    vmstat -d
    ```

  - 查看系统的slab信息

    ```bash
    vmstat -m
    ```

    

