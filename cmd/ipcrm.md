- ipcrm [OPTIONS]
  ipcrm {shm | msg | sem} ID...
- 功能：ipcrm 命令用于删除指定 ID 的 IPC（Inter-Process Communication，进程间通信）对象，包括消息队列（message queue）、共享内存（shared memory）和信号量（semaphore），同时将与 IPC 对象关联的数据一并删除，只有超级用户或 IPC 对象创建者能够删除。
- 参数：
  - -a, --all [shm | msg | sem]
     删除所有 IPC 资源。当给定选项参数 shm、msg 或 sem，则只删除指定类型的 IPC 资源。注意：慎用该选项，否则可能会导致某些程序出于不确定状态
  - -M, --shmem-key SHMKEY
     当没有进程与共享内存段绑定时，通过 SHMKEY 删除共享内存段
  - -m, --shmem-id SHMID
     当没有进程与共享内存段绑定时，通过 SHMID 删除共享内存段
  - -Q, --queue-key MSGKEY
     通过 MSGKEY 删除消息队列
  - -q, --queue-id MSGID
     通过 MSGID 删除消息队列
  - -S, --semaphore-key SEMKEY
     通过 SEMKEY 删除信号量
  - -s, --semaphore-id SEMID
     通过 SEMID 删除信号量
  - -v, --verbose
     以冗余模式执行 ipcrm，输出 rpcrm 正在做什么
  - 

- 示例：

  - 删除共享内存

    ```bash
    ipcrm -M SHMKEY
    # 或
    ipcrm -m SHMID
    # 或
    ipcrm shm SHMID
    ```

  - 删除消息队列

    ```bash
    ipcrm -Q MSGKEY
    # 或
    ipcrm -q MSGID
    # 或
    rpcrm msg MSGID
    ```

  - 删除信号量

    ```bash
    ipcrm -S SEMKEY
    # 或
    ipcrm -s SEMID
    # 或
    ipcrm sem SEMID
    ```

    