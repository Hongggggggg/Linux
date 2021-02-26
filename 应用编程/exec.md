- 功能：对当前进程进行‘替换’，即用新的进程映像替换进程映像，原来的代码段，data、堆栈等都被新的所指定的映像所取代，但是会保留PID等少量信息，一旦调用成功就会执行新的映像程序，相当于用新的进程骨架来运行老的进程内容。

- 示例：

  - 执行类似命令行 ls -al ./，显示当前路径内文件的详细信息

    ```bash
    #include <unistd.h>
    #include <stdio.h>
    
    void main(void)
    {
    	if(execl("/bin/ls", "ls", "-al", "./", NULL) == -1)
    	{
    		printf("execl errorr\r\n");
    	}
    	printf("hello execl\r\n");
    }
    ```

    

  
