- ipcs [options]

- 功能：ipcs 命令用于查看 Linux 进程间通信设施的状态，包括消息列表、共享内存和信号量的信息。可以帮助开发人员定位进程间通信中出现的问题。

- 参数：

  - -i，--id ID
     详细显示指定资源 ID 的 IPC 信息。使用时需要指定资源类型，资源包括消息队列（-q）、共享内存（-m）和信号量（-s）

  

  IPC 资源类型选项：

  - -q，--queues
     显示活动的消息队列信息
  - -m，--shmems
     显示活动的共享内存信息
  - -s, --semaphores
     显示活动的信号量信息
  - -a，--all
     显示系统内所有的IPC信息。命令的默认选项

  

  输出格式选项：当指定多个时，以最后一个为准。

  - -c，--creator
     查看 IPC 的创建者和所有者

  - -l，--limits
     查看 IPC 资源的限制信息

  - -p，--pid
     查看 IPC 资源的创建者和最后操作者的进程 ID

  - -t，--time
     查看最新调用 IPC 资源的详细时间。包括 msgsnd() 和 msgrcv() 对 message queues 的操作，shmat() 和 shmdt() 对shared memory 的操作，以及 semop() 对 semaphores 的操作

  - -u，--summary
     查看 IPC 资源状态汇总信息

    显示大小单位控制选项：只对选项 -l, --limits 生效

  - -b，--bytes
     以字节为单位显示大小

  - --human
     以可读的格式显示大小

- 示例：

  - 显示所有IPC信息

    ```bash
    ipcs
    ```

  - 显示共享内存指定ID的信息

    ```bash
    ipcs -m -i 32766
    ```

    