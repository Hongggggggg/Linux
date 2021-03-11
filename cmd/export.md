- export [-fn] [name[=value] ...] or export -p

- 功能：export 命令为 Shell 内建命令，用于设置或显示环境变量，环境变量包含变量与函数。在 Shell 中执行程序时，Shell 会提供一组环境变量。export 可新增、删除或修改环境变量，供后续被执行的程序使用。export 的作用效果仅限于当前登录。

- 参数：

  - -f，表示name为函数名称
  - -n，删除指定的变量。实际上并未删除，只是不会输出到后续指令的执行环境中
  - -p，列出所有的Shell环境变量

- 示例：

  - 定义环境变量并赋值

    ```bash
    export MYNEWV=8
    ```

  - 修改指明shell命令搜索路径的环境变量PATH

    ```bash
    export PATH=&PATH:/usr/local/mysql/bin
    ```

  - 查看环境变量是否已经设置好：

    ```bash
    export -p | grep PATH
    #或echo $PATH
    ```

    

