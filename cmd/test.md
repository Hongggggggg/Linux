- test [EXPRESSION]

- 功能：test 用于检查某个条件是否成立，它可以进行数值、字符串和文件三个方面的测试。

- 参数选项：

  - 逻辑运算
    - ! EXPRESSION，逻辑非，EXPRESSION 为 false 返回 true
    - EXPRESSION1 -a EXPRESSION2，逻辑与，两个表达式均为 true 返回 true
    - EXPRESSION1 -o EXPRESSION2，逻辑或，两个表达式只要有一个为 true 返回 true
  - 数值间的比较
    - INTEGER1 -eq INTEGER2，两整数是否相等
    - INTEGER1 -ne INTEGER2，整数 INTEGER1 是否不等于 INTEGER2
    - INTEGER1 -gt INTEGER2，整数 INTEGER1 是否大于 INTEGER2
    - INTEGER1 -ge INTEGER2，整数 INTEGER1 是否大于等于 INTEGER2
    - INTEGER1 -lt INTEGER2，整数 INTEGER1 是否小于 INTEGER2
    - INTEGER1 -le INTEGER2，整数 INTEGER1 是否小于等于 INTEGER2
  - 字符串的比较
    - -n STRING，字符串不为空返回 true
    - -z STRING，字符串为空返回 true
    - STRING1 = STRING2，字符串相等返回 true
    - STRING1 != STRING2，字符串不相等返回 true
  - 文件的比较与类型判断*
    - FILE1 -ef FILE2，两个文件是否为同一个文件。主要看文件设备号与 inode 是否一致
    - FILE1 -nt FILE2，文件 FILE1 是否比 FILE2 新（修改时间新）
    - FILE1 -ot FILE2，文件 FILE1 是否比 FILE2 旧（修改时间旧）
    - -b FILE，文件存在且是块（block）设备文件
    - -c FILE，文件存在且是字符（character）设备文件
    - -d FILE，文件存在且是目录（directory）
    - -e FILE，文件存在（exist）返回 true
    - -f FILE，文件存在且是普通文件
    - -g FILE，文件存在且设置了 SGID
    - -G FILE，文件存在且属于有效组ID
    - -h FILE，文件存在且是软链接。同 -L
    - -k FILE，文件存在且设置了粘着位（Sticky Bit）
    - -L FILE，文件存在且是软链接。同 -h
    - -O FILE，文件存在且属于有效用户ID
    - -p FILE，文件存在且属于命名管道
    - -r FILE，文件存在且可读
    - -s FILE，文件存在且内容不为空
    - -S FILE，文件存在且是一个套接字（socket）
    - -t FD，文件描述符是在一个终端打开的
    - -u FILE，文件存在且设置了 SUID 位
    - -w FILE，文件存在且且可写
    - -x FILE，文件存在且可执行

- 示例：

  - 判断数值是否相等：

    ```bash
    test 0 -eq 0; echo $? #test 退出码等于0表示条件成立
    ```

  - 判断文件是否存在：

    ```bash
    test -e /etx/passwd;echo $?#test 退出码等于0表示文件存在
    ```

  - 判断文件是否是同一个文件

    ```bash
    test /etc/passwd -ef /etc/shadow; echo $? #test 退出码等于1表示不是同一个文件
    ```

    

