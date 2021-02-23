- fork()，创建当前进程的子进程，当前进程称为父进程

- 特点：

  - 子进程和父进程在不同的内存空间中运行
  - 子进程和父进程具有相同的特性内容，使用相同的CPU寄存器值，都将执行fork()后的下一条指令
  - 其中一个进程执行的内存写、文件映射和反映射不会影响到另一个进程
  - fork失败返回-1，在子进程返回0，在父进程返回子进程的PID

- 示例：

  ```c
  static void fork_test(void)
  {
      pid_t pid;
      pid = fork();
      if(pid < 0)
      {
          printf("fork failed!\r\n");
      }
      else if(pid) /*两个分支都会执行，一个是父进程执行，一个是子进程执行*/
      {
          printf("Parent pid: %d\r\n", getpid());
      }
      else
      {
          printf("Child pid: %d\r\n", getpid());
      }
  }
  ```

  