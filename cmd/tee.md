- tee [OPTION]... [FILE]...

- 功能：tee 命令从标准输入读取数据后，将数据重定向到给定的文件和标准输出。给定的文件可以有多个。

- 参数选项

  - -a，--append

    像文件中重定向时使用追加模式

  - -i，--ignore-interrupts

    忽略中断（interrupt）信号

- 示例：

  - 标准错误输出和标准输出同事输出到屏幕和指定文件file1和file2

    ```bash
    make 2>&1 | tee file1 file2
    ```

    

