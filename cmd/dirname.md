- dirname [OPTION] Name...

- 功能：dirname 命令从文件路径中获取文件目录。作用与 basename 命令相反，basename 用于获取文件名。如果文件路径中不包含 /，那么输出 . 表示当前目录。如果文件路径最后一个字符是 /，那么剥离倒数第二个 / 及其后的内容。

- 参数选项：

  - -z，用空字符NULL而不是换行符分割

- 示例：

  - 获取目录部分，剥离文件名

    ```bash
    dirname /root/go/src/test.txt
    #输出
    /root/go/src
    ```

  - 获取目录部分，剥掉文件名，后跟多个文件路径

    ```bash
    dirname /root/go/src/main.go /root/go/src/util.go
    #输出
    /root/go/src
    /root/go/src
    ```

  - 获取目录的目录。即如果文件路径最后一个字符是/，那么就剥离倒数第二个/及其之后的内容

    ```bash
    dirname /usr/bin/
    #输出
    /usr
    ```

  -  如果文件路径不包含/，那么输出.表示当前目录

    ```bash
    dirname stdio,h
    #输出
    .
    ```

  -  根目录特殊，不剥除任何内容，直接输出 /

    ```bash
    dirname /
    #输出
    /
    ```

    

