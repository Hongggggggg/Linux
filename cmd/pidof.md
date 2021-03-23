- pidof [-s] [-c] [-n] [-x] [-z] [-o omitpid[,omitpid...]]  [-o omitpid[,omitpid...]...]  [-d sep] program [program...]

- 功能：pidof 命令用于查找指定名称进程的进程ID，是命令 killall5 的一个软链接。

  找出进程 ID 的目的通常是根据进程 ID 进一步确认进程的运行状态、杀掉进程或者发送一个信号给它。

- 参数选项：

  - -s，只返回一个PID
  - -c，只显示运行在root目录下的进程，这个选项只对root用户有效
  - -x，显示指定脚本名称的进程
  - -o，指定不显示的进程，该选项可以出现多次
  - -m，与 -o 选项一起使用，使得 argv[0] 与 argv[1] 和被忽略进程相同的进程同时被忽略。一般用于忽略由同名 Shell 脚本启动的进程，因为 argv[0] 为 Shell，一般为 /bin/bash，argv[1] 为脚本名称

- 示例：

  - 查看程序名称为sshd的进程ID

    ```bash
    pidof sshd
    ```

  - 查看由Shell脚本启动的进程ID

    ```bash
    pid -x test.sh
    ```

