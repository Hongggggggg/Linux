- 进程不满足运行条件就会变成阻塞状态进入等待队列，而子进程是由父进程管理的，一旦子进程退出父进程需要回收分配给子进程的资源，同时还要知道其运行的状态，否则容易造成内存泄漏，并且子进程容易成为僵尸进程，这样就需要父进程监控子进程的状态。

- 对于wait系统调用一般是夫i昵称进行调用，父进程调用后阻塞自身，一旦有子进程退出，父进程就会释放或销毁子进程相关资源并返回，否则父进程会一直阻塞在wait系统调用 处

- wait返回与参数

  - 一旦子进程返回，父进程wait会返回相应的子进程的PID，如果父进程没有对应的子进程，调用就返回-1，同时故障类型保存在errno
  - 参数status指针用于保存对应返回子进程退出时的一些状态，表示子进程是否正常结束等
  - 因为该指针指向的是要给整形数据，且返回状态均在所指向的数据的位中，所以linux采用了一些宏来进行提取，比如WIFEXITED（status）返回true表示正常退出

- 示例：

  - 下面通过使用wait在父进程等待子进程退出，而子进程中使得exit(3)异常退出，由于fork以后父子进程无序，所以使用sleep让子进程休眠以后保证父进程运行，当子进程退出，父进程wait返回子进程PID，并且通过WEXITSTATUS宏获得其退出原因。

    ```c
    void main(void)
    {
    	pid_t pid = fork();
        pid_t Waitpid;
        
        int status = -1;
        if(pid < 0)
        {
            printf("fork fail\r\n");
        }
        else if(pid > 0)
        {
        printf("parent pid = %d\r\n", getpid());
            Waitpid = wait(&status);
         	printf("waitpid = %d\r\n", Waitpid);
        }
        else
        {
            printf("child pid = %d\r\n", getpid());
            sleep(5);
            exit(3);
        }
        printf("child exit status is %d\r\n", WEXITSTATUS(status));
        printf("return pid = %d\r\n", getpid());
        return 1;
    }
    ```
    
    
  
  

