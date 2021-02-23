- watch [options] command

- 功能：将命令的结果输出到标准输出设备，多用于周期性执行命令/定时执行命令

- 参数：

  - -n，指定间隔时间，默认2s一次
  - -d，高亮显示变化的区域。
  - -t，关闭watch命令在顶部的时间间隔、命令以及当前时间的显示

- 示例：

  - 每隔1s高亮显示网络链接数的变化情况

    ```bash
    watch -n 1 -d netstat -ant
    ```

  - 每隔一秒高亮显示http连接数的变化情况

    ```bash
    watch -n 1 -d 'pstree|grep http' #后面接的命令若带有管道符，需要加''将命令区域归整
    ```

  - 检测当前目录中test文件的变化

    ```bash
    watch -d 'ls -l|grep test'
    ```

  - 10s输出一次系统的平均负载

    ```bash
    watch -n 10 'cat /proc/loadavg'
    ```

    

