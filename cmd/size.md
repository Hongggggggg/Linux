- size [option(s)] [file(s)]

- 查看目标文件、库或可执行文件中各段及其总和的大小，是GNU二进制工具集GNU Binutils的一员

- 参数：

  - -t，列出所有文件的总大小
  - -d，-o，-x，以10进制、8进制、16进制输出

- 示例：

  - 查看指定程序各个段的大小：

    ```bash
    size /bin/size
    ```

  - 查看各静态库中的各个目标文件的段大小

    ```bash
    size /usr/lib64/libc.a
    ```

    

