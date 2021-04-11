- sort [OPTION]... [FILE]...
  sort [OPTION]... --files0-from=F

- 功能：以行为单位对文本文件的内容进行排序，将结果显示在标准输出，比较原则是从行首字符向后，依次按 ASCII 码值进行比较，最后按升序输出。如果 file 参数指定多个文件，那么 sort 命令将这些文件纵向连接起来，当作一个文件进行排序。

  不加任何选项时，将对整行从第一个字符开始依次向后直到行尾按照 ASCII 码值做升序排序。

- 参数选项：

  - -b, --ignore-leading-blanks
     忽略每行前面的空格字符
  - -c, --check, --check=diagnose-first
     只检查文件是否已排序，不进行排序
  - -C, --check=quiet, --check=silent
     类似于 -c，但不报告第一个乱序的行
  - -d, --dictionary-order
     按照字典序，只考虑字母、数字及空格字符，忽略其他字符
  - --files0-from=F
     从文件 F 中以 NUL 字符结尾的字符串作为输入文件名；如果 F 是 -，则从标准输入中读取文件名
  - -f, --ignore-case
     排序时，将小写字母视为大写字母
  - -i, --ignore-nonprinting
     排序时，只考虑可打印字符，忽略不可打印字符
  - -m, --merge
     合并多个已排序的文件
  - -n, --numeric-sort
     按数值大小排序
  - -o, --output=FILE
     将排序结果输出到指定文件
  - -r,--reverse
     逆向输出排序结果（降序排序）
  - -t, --field-separator=SEP
     指定排序时使用的分隔字符，sort命令默认字段分隔符为空格和Tab
  - -u, --unique
     相同的数据中，仅输出一行
  - -k,--key=POS1[,POS2]
     以第 POS1 栏到 POS2 栏排序，默认到最后一栏
  - --help
     显示帮助信息并退出
  - --version
     显示版本信息并退出

- 示例：

  - 对 /etc/passwd 进行排序。

    ```bash
    cat /etc/passwd | sort
    ```

  - /etc/passwd 内容以冒号:来分隔，以第三栏至行末尾栏来排序。

    ```bash
    cat /etc/passwd | sort -t ':' -k 3
    ```

  - 对 /etc/passwd，以第六个域的第 2 个字符到第 4 个字符进行升序排序，再基于第一个域进行反向排序。

    ```bash
    cat /etc/passwd | sort -t ':' -k 6.2,6.4 -k 1,1r
    ```

    

