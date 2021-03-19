- basename NAME [SUFFIX]
  basename OPTION... NAME...

- 功能：从文件路径中剥离目录和后缀，以获取文件的基本名称。与 dirname 命令作用相反，dirname 用于获取目录部分。

- 选项：

  - -a，支持多个文件名称参数，将每一个参数当作文件名对待
  - -s，移除后缀
  - -z，以空字符NULL分割输出而不是换行符

- 常用示例：

  - 获取文件名，不包含目录：

    ```bash
    basename /root/go/src/main.go
    #输出
    main.go
    ```

  - 获取文件名，不包含目录与后缀：

    ```bash
    basename /root/go/src/main.go .go
    #或
    basename -s .go /root/go/src/main.go
    #输出：
    main
    ```

  - 同时获取多个文件名，不包含目录与后缀

    ```bash
    basename -a -s .go /root/go/src/main.go /root/go/src/util.go
    #输出
    main
    util
    ```

  - 如果路径最后是一个目录，那么即匹配最后一个目录的名字

    ```bash
    basename /root/go/src/
    #输出
    src
    ```

    

