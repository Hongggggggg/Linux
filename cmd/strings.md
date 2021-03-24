- strings [-afovV] [-min-len]
                 [-n min-len] [--bytes=min-len]
                 [-t radix] [--radix=radix]
                 [-e encoding] [--encoding=encoding]
                 [-] [--all] [--print-file-name]
                 [-T bfdname] [--target=bfdname]
                 [-w] [--include-all-whitespace]
                 [-s] [--output-separatorsep_string]
                 [--help] [--version] file...

- 功能：strings 命令是二进制工具集 GNU Binutils 的一员，用于打印文件中可打印字符串，文件可以是文本文件（test.c），但一般用于打印二进制目标文件、库或可执行文件中的可打印字符。字符串默认至少是 4 个或更多可打印字符的任意序列，可使用选项改变字符串最小长度。

- 参数选项：

  - -a，-all，扫描整个文件而不只是扫描目标文件初始化的装载段

  - -d，--data，仅打印文件中已初始化、加载的数据段中的字符串，这可能会减少输出的垃圾量

  - -e, --encoding=ENCODING

    选择字符编码与字节序。encoding可取值s=7bits的ASCII, S=8bits的Latin1, {b,l}=16bits宽字符大小端编码, {B,L}=32bits宽字符大小端编码。其中b，B代表bigendian，l，L代表littleendian

  - -f,–-print-file-name

  - -, -n, --bytes=MIN_LEN，指定可打印字符序列的最小长度，而不是默认的4个字符

  - -o，类似 --radix=o

  - -t, --radix=RADIX，输出字符串在文件中的偏移位置，RADIX 可取值 o（octal，八进制）、d（decimal，十进制）或者 x（hexadecimal，十六进制）

  - -T, --target=BFD_NAME，指定二进制文件格式

  - -w, --include-all-whitespace，默认情况下，Tab 和空格字符包含在字符串中，但其他空白字符除外，比如换行符和回车符等字符不是。-w 使所有的空白字符被认为是字符串的一部分

  - @FILE，从指定的文件 FILE 中读取命令行选项

- 示例：

  - 打印可执行文件中的所有可读字符串

    ```bash
    strings /bin/ls
    ```

  - 查看某一个字符串属于哪个文件

    ```bash
    strings -f * | grep "xxx"
    ```

  - 查看glibc支持的版本

    ```bash
    strings /lib64/libc.so.6 | grep GLIBC
    ```

    

