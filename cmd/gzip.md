- gzip [opt] [file]

- 功能：文件压缩

- 命令参数：

  - -a或--ascii，使用ASCII模式
  - -c或--stdout或--to-stdout，将压缩后的文件输出到标准输出设备，不改动原始文件
  - -d或--decompress或--uncompress ，解压文件
  - -I或--list，列出压缩文件的相关信息
  - -L或--license，显示版本与版权信息
  - -n或--no-name，压缩文件时，不保存原来的文件名称及时间戳
  - -N或--name，压缩文件时，保存原来的文件名称及时间戳
  - -q或--quiet，不显示警告信息
  - -r或--recursive，递归处理
  - -S <压缩字尾字符串>，更改压缩字尾字符串
  - -t或--test，测试压缩文件是否正确
  - -v或--verbose，显示指令执行过程
  - -V或--version，显示版本信息
  - -num，用指定的数字num调整压缩的速度，-1或--fast表示最快压缩方法（低压缩比）

- 示例：

  - 将目录下的每个文件压缩成.gz文件

    ```bash
    gzip *
    ```

  - 将每个压缩文件解压，并列出详细信息

    ```bash
    gzip -dv *
    ```

  - 列出所有压缩文件中的文件信息，但不解压

    ```bash
    gzip -I *
    ```

  - 递归压缩目录

    ```bash
    gzip -rv test_dir
    ```

  - 递归解压目录

    ```bash
    gzip -dr test_dir
    ```

    
