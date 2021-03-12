- stat [OPTION]... FILE...

- 功能：显示文件或文件系统的详细信息。在显示文件信息时，比ls更加详细

- 参数：

  - -L，跟随符号链接解析源文件而非符号链接

  - -f，显示文件所在文件系统信息而非文件信息

  - -c，以指定格式输出，而非默认格式

    - 显示文件信息可用格式控制符如下：
       %a：以八进制显示访问权限
       %A：以可读形式显示访问权限
       %b：显示占有块数
       %B：显示每一块占有的字节数
       %C：SELinux security context string
       %d：十进制显示文件所在设备号
       %D：十六进制显示文件所在设备号
       %f：十六进制显示文件类型
       %F：文件类型。Linux下文件类型主要分为普通文件、目录、字符设备文件、块设备文件、符号链接文件、套接字等
       %g：文件所有者组ID
       %G：文件所有者组名称
       %h：文件硬链接数
       %i：inode号
       %m：文件所在磁盘分区挂载点，比如/data
       %n：文件名称
       %N：单引号括起来的文件名称，如果是软链接，则同时显示指向的文件名称
       %o：optimal I/O transfer size hint
       %s：实际文件大小，单位字节
       %t：major device type in hex, for character/block device special files
       %T：minor device type in hex, for character/block device special files
       %u：所有者用户ID
       %U：所有者用户名称
       %w：文件创建时间，输出-表示无法得知
       %W：文件创建时间，输出Unix时间戳，0表示无法得知
       %x：可读形式输出最后访问时间atime
       %X：Unix时间戳输出最后访问时间atime
       %y：可读形式输出最后修改时间mtime
       %Y：Unix时间戳输出后修改时间mtime
       %z：可读形式输出最后状态改变时间ctime
       %Z：Unix时间戳输出最后状态改变时间ctime

       显示文件系统信息可用格式控制符有：
       %a：非超级用户可使用的自由block数
       %b：文件系统总block数
       %c：文件系统总文件节点数
       %d：可用文件节点数
       %f：可用文件block数
       %i：十六进制文件系统ID
       %l：最大文件名称长度
       %n：文件名称
       %s：一个块的大小，单位字节（for faster transfers）
       %S：一个块的基本大小，单位字节（用于统计block的数量）
       %t：十六进制输出文件系统类型
       %T：可读形式输出文件系统类型

- 示例：

  - 显示文件信息

    ```bash
    stat test.txt
    ```

  - 显示文件所在文件系统信息：

    ```bash
    stat -f test_file
    ```

    