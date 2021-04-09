- col [OPTIONS]

- 功能：col（control）命令是一个标准输入文本过滤器，它从标准输入读取内容，过滤掉控制字符反向换行符（RLF-Reverse Line Feed）和半反向换行符（HRLF-Halt RLF）后输出到标准输出。还可以将空白符用等价制表符（Tab）或空格（Space）来替换。

  在许多 Linux 说明文件里，包含控制字符。当我们运用 Shell 特殊字符 > 和 >> 把说明文件的内容输出成纯文本文件时，控制字符会变成乱码，col 命令则能有效滤除这些控制字符。

- 参数选项：

  - -b, --no-backspaces
     不输出任何退格符，只打印写入每个列位置的最后一个字符
  - -f, --fine
     允许正向半换行符（half-forward line feeds）。通常，处于半行分界线上的字符打印在下一行
  - -h, --tabs
     将多个空格转换为Tab，一般 4 个 空格转为 1 个 Tab
  - -l, --lines NUMBER
     设置缓冲行为 NUMBER，默认为 128
  - -p, --pass
     不转换未识别的控制符
  - -x, --spaces
     将 Tab 转为多个空格，一般 1 一个 Tab 转为 4 个空格

- 示例：

  - 将 Tab 替换为空格，一般 1 个 Tab 转为 4 个空格。

    ```bash
    echo -e "123\t456" | col -x
    ```

  - 将空格替换为 Tab，一般 4 个 空格转为 1 个 Tab。

    ```bash
    echo -e "123    456" | col -h
    ```

  - 将帮助文档内的控制符删除。以 col 命令的 manual 为例。

    ```bash
    man col | col -b > newFile
    ```

    