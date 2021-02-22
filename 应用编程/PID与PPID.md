- PID(Process ID)：进程PID是当操作系统运行进程系统自动为其分配的用于唯一标识此进程的一个整数。

- PPID：进程的父进程的PID

- 示例：

  ```c
  #include <sys/types.h>
  #include <unistd.h>
  #include <stdio.h>
  
  void main(void)
  {
  	printf("Child pid: %d\r\n", getpid());
      printf("Parent pid: %d\r\n", getppid());
  }
  ```

  