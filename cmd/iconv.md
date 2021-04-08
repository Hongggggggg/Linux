- iconv -f FROMCODE -t TOCODE FILE ...

- 功能：iconv命令是用来转换文件的编码方式，比如它可以将UTF8编码的转换成GB18030的编码。Linux下的iconv开发库包括`iconv_open,iconv_close,iconv`等C函数（非标准库函数），可以用来在C/C++程序中很方便的转换字符编码。

- 参数选项：

  - -c ，静默丢弃不能识别的字符，而不是终止转换

  - -f, --from-code=CODE，指定待转换文件的编码。

  - -t, --to-code=CODE，指定目标编码

  - -l, --list，列出已知的字符编码。

  - -o, --output=FILE，列出指定输出文件，而非默认输出到标准输出

  - -s, --silent，关闭警告。

  - --verbose，显示进度信息

  - -?, --help，显示帮助信息

  - --usage，显示简要使用方法

  - -V, --version，显示版本信息

    -f 和 -t 所能指定的合法编码可以在 -l 选项的结果中查看。

- 常用示例

  - 将GBK文件转换为UTF8文件

    ```bash
    iconv -f gbk -t utf8 inputFile.txt -o outputFile.exe.utf8
    ```