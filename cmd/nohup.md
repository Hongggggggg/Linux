- nohup COMMAND [ARG]...
  nohup OPTION

- 功能：将程序以忽略挂起信号（SIGHUP）的方式运行。常见的用法是和&命令一同使用，将命令放置到后台运行，即使终端挂掉，进程会忽略挂起信号，继续运行。

- 示例：

  - 使用nohup命令提交作业，那么在缺省情况下该作业所有的输出都被重定向到一个名为nohup.out的文件中，除非另外制定了输出文件。

    ```bash
    nohup ./test.sh &
    ```

  - 标准输出与标准错误输出重定向

    ```bash
    nohup ./test.sh > test.log 2>&1 &
    ```

  - 指定输出文件，输出被重定向到output.txt文件中

    ```bash
     nohup bash a.sh &> touput.txt
    ```

    **注意：**
    （1）2>&1 标识标准错误输出重定向等同于标准输出重定向，即标准错误输出也重定向到文件test.log；
    （2）& 命令是命令放在后台执行，需要放在命令的最后面。

  

