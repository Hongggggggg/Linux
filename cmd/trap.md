- trap [-lp] [ARG] [SIGSPECS]

- 功能：trap 命令是 Shell 内建命令，用于指定在接收到信号后将要采取的动作。常见的用途是在脚本程序被中断时完成清理工作。

- 参数说明：

  - -l，列出信号名称与对应的数值
  - -p，列出信号与其绑定的命令列表
  - ARG，与指定信号绑定的命令。如果 ARG 为空字符串，表示忽略信号；如果 ARG 不指定（缺省）或为 -，表示执行信号的默认动作
  - SIGSPECS，信号列表，可以是信号名称，也可以是信号对应的数值。可用信号可以使用 trap -l 查看

- 示例：

  - 忽略HUP、INT、QUIT、TSTP信号

    ```bash
    trap "" HUP INT QUIT TSTP
    ```

  - 捕获 HUP、INT、QUIT、TSTP 信号，并执行默认动作

    ```bash
    trap HUP INT QUIT TSTP
    #或
    trap - HUP INT QUIT TSTP
    ```

  - 挂载 Shell 进程结束前需要执行的命令。格式为：trap “commands” EXIT。如脚本 exit.sh：

    ```bash
    #!/bin/bash
    
    echo "start"
    trap "echo 'end'" EXIT
    echo "before exit"
    exit 0
    ```

    执行输出：

    ```bash
    start
    before exit
    end
    ```

    

