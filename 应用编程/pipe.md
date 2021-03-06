- 管道(pipe)是一种单向且先进先出形式的通信方式，一个进程向管道的尾部写入数据，而另一个进程从管道的头部读出数据。

  - 无名管道：从名字上可以知道无名管道是没有标识的管道，其仅仅只能用于父子进程等具有血缘关系的进程通信，管道可以看成特定的文件，对于无名管道而言在文件系统中不可见，只存于内存中。

  - 有名管道：有名管道算是无名管道的改进，由于无名管道通信限制较大，因此有名管道可以在任意两个进程中进行通信，该管道可以通过路径名来指出，且在文件系统中是可见的即管道文件，所以可以通过文件名或者路径来访问。

  - **注意点：**

    - 管道是固定大小的缓存区，在Linux中一般为1页，即4K内存空间，所以当管道满了使用write就会堵塞，等待读进程读取，以腾出空间写入。同理，read也是类似的，当管道为空的时候，使用read的进程也会堵塞，等待有进程写入。

    - Linux内核不保证管道读写的原子性，所以需要一些同步互斥机制进行灵活处理。

- 示例：

  - 创建无名管道

    ```c
    static void pipe_test(void)
    {
        int pipe_fd[2];
        char rcv_buf[50] = {0};
        if (pipe(pipe_fd) < 0)
        {
            printf("create pipe failed\r\n");
            return;
        }
        else
        {
            printf("create pipe success\r\n");
        }
        char str[] = {"hello world"};
        write(pipe_fd[1], &str, sizeof(str));
        read(pipe_fd[0], rcv_buf, 50);
        printf("read: %s\r\n", rcv_buf);
    
        close(pipe_fd[0]);
        close(pipe_fd[1]);
    }
/*创建两个文件描述符pipe_fd[0]和pipe_fd[1]，分别对应读管道和写管道*/
    ```
    
  - 无名管道进程通信：
  
    ```c
    static void pipe_test(void)
    {
        int pipe_fd[2];
        char buf[100] = {0};
        pid_t pid;
        int readNum = 0, writeNum = 0;
        if (pipe(pipe_fd) < 0)
        {
            printf("create pipe failed\r\n");
            exit(1);
        }
        else
        {
            printf("create pipe success\r\n");
        }
        const char str[] = {"hello world"};
        write(pipe_fd[1], &str, sizeof(str));
        read(pipe_fd[0], buf, 100);
        printf("read: %s\r\n", buf);
    
        if((pid = fork()) == 0)/*子进程*/
        {
            sleep(3);
            if((readNum = read(pipe_fd[0], buf, 100)) > 0)
            {
                printf("%d bytes read: %s\r\n", readNum, buf);
            }
            close(pipe_fd[0]);
            exit(0);
        }
        else if(pid > 0)
        {
            if((writeNum = write(pipe_fd[1], str, strlen(str))) != -1)
            {
                printf("write %d bytes: %s\r\n", writeNum, str);
            }
            close(pipe_fd[1]);
            waitpid(pid, NULL, 0);
            exit(0);
        }
    }
    ```
  
    进程一旦fork以后，相应的用户空间会复制一份，同样对于文件描述符也是一样的，我们可以关闭父进程读和子进程的写即可实现从父进程到子进程的通信，同理我们可以关闭父进程写和子进程的读即可实现从子进程到父进程的通信。
    
  - 写有名管道：
  
    ```c
    static void pipe_write(int argc, char** argv)
    {
    	int fd;
    	char buf[50];
    	fd = open("./myfifo", O_WRONLY|O_NONBLOCK, 0);
    
    	strcpy(buf ,argv[1]);
    	if(write(fd, buf, 50) == -1)
    	{
    		if(errno == EAGAIN)
    			printf("ERROR\r\n");
    	}
    	else
    	{
    		printf("write %s\r\n", buf);
    	}
    }
    ```
  
  - 读有名管道：
  
    ```c
    static void pipe_read(int argc, char** argv)
    {
    	char buf[50];
    	int fd;
    	int nread;
    
    	if((mkfifo("./myfifo", O_CREAT|O_EXCL) < 0) && (errno != EEXIST))
    	{
    		printf("cannot create fifo\r\n");
    	}	
    	memset(buf, 0, sizeof(buf));
    	fd = open("./myfifo", O_RDONLY|O_NONBLOCK, 0);
    
    	while(1)
    	{
    		memset(buf, 0, sizeof(buf));
    		if(read(fd, buf, 100) == -1)
    		{
    			if(errno == EAGAIN)
    				printf("error\r\n");
    		}
    		printf("read %s from FIFO\n", buf);
    		sleep(1);
    	}
    }
    ```
  
    
