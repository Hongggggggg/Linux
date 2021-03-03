- read  [OPTIONS]  [VARNAMES]

- 功能：用于标准输入或 -u 选项指定的文件描述符中读取单行，并将读取的单行根据IFS变量分割成多个字段，并将分割后的字段分别赋值给指定的变量列表

- 参数：

  - -a ANAME，将分割后的字段依次存储到指定的数组中，存储的起始位置从数组的下标 0 开始
  - -d DELIM，后跟一个分隔符，只有第一个字符有用，用以取代换行符作为行的结束标志
  - -e，在输入的时候可以使用命令补全功能，使用 Tab 键可自动补全当前目录下文件
  - -i  TEXT，如果使用 readline 命令读取行，则在开始编辑之前将文本放入编辑缓冲区
  - -n NCHARS，后跟一个数字，定义输入文本的长度，而不是读取整行
  - -N NCHARS，后跟一个数字，定义输入文本的长度，而不是读取整行。但是如果一行不足 nchars 个字符，则忽略行分隔符继续读取下一行
  - -p PROMPT，从终端读取输入时，在输入前打印提示信息
  - -r，屏蔽反斜杠 \。如果没有该选项，则 \ 作为一个转义字符，有的话 \ 就是个正常的字符了
  - -s，静默模式，输入字符不显示到屏幕，例如 login 时输入密码
  - -t TIMEOUT，后面跟秒数，定义输入字符的等待时间
  - -u FD，后面跟文件描述符 fd，从文件描述符中读取

- 示例：

  - 如果没有指定变量，read 会把传入的值传给 REPLY，只要调用 REPLY就可以引用 read 读取的内容。

    ```bash
    read; 
    dablelv
    echo "\$REPLY:$REPLY"
    $REPLY:dablelv
    ```

  - read 从终端读取时指定一个提示语

    ```bash
    [root@AAA]:read -p"input u password:";echo "\$REPLY:$REPLY"
    input u password:123456
    $REPLY:123456
    ```

  - 读取文件。每次调用 read 命令都会读取文件中的一行文本。当文件没有可读的行时，read 命令将以非零状态码退出。

    ```bash
    while read var1 var2
    do
       echo $var1 $var2
    done < file.txt
    ```

    

