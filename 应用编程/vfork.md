- vfork()，创建一个子线程，与fork()具有相同的效果

  不同点：

  - fork的子进程会拷贝父进程的数据段，而vfork的子进程与父进程共享数据段
  - fork子进程创建以后，父子进程执行顺序与系统调度算法有关，不确定，而vfork则是子进程先运行，父进程后运行

- 注意事项：

  - 在Linux下，fork()是使用写时复制页面实现的，因此fork()带来的唯一损失就是时间和内存需要复制父进程的页表，并为子进程创建唯一的任务结构。

  - 然而，以前一次fork()需要对调用者的数据空间做一个完整的副本，这通常是不必要的，为了提高效率引入了vfork()系统调用，该调用没有完全复制地址空间，但借用父进程的内存和控制线程，直到发生execve()调用或退出。

  - 注意不能使用vfork以后在main中使用return，因为函数栈父子进程共享，如果一方直接return了，意味着函数栈释放，从而导致程序运行错误，下面的实验你如果把fork的程序直接修改为vfork会导致程序运行完子进程在运行父进程就会错误，而必须在子进程中调用_exit(0);使得子进程退出，父进程执行。

- 示例：

  ```bash
  static void vfork_test(void)
  {
      pid_t pid;
      int cnt = 1;
      pid = vfork();
      if (pid < 0)
      {
          printf("vfork failed!\r\n");
      }
      else if(pid)
      {
          cnt++;
          printf("Parent pid: %d, cnt: %d\r\n", getpid(), cnt);
          
      }
      else
      {
          cnt++;
          printf("Child pid: %d, cnt: %d\r\n", getpid(), cnt);
          _exit(0);
      }
  }
  ```

  输出：

  ```bash
  Child pid: 215207, cnt: 2
  Parent pid: 215206, cnt: 3
  ```

  

