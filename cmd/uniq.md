- uniq [OPTION]... [INPUT [OUTPUT]]

- 功能：用于去除有序文件中的重复行并将结果输出到标准输出

- 参数：

  - -c，显示行出现的次数
  - -d，仅显示重复出现的行，只打印一次
  - -D，仅显示重复的行，且打印重复行的所有行
  - -f，忽略前N个字段
  - -i，忽略大小写字符的不同
  - -s，跳过前面N个字符不比较
  - -u，只显示不重复的行
  - -w，指定每行要比较的前N个字符数

- 示例：

  - 对文件去重：

    ```bash
    cat test.txt | sort | uniq #使用uniq前需将文件进行排序
    ```

  - 排序后删除重复行，并在行首位置输出该行的重复次数

    ```bash
    sort test.txt | uniq -c
    ```

  - 仅显示存在重复的行，并在首航显示该行的重复次数

    ```bash
    sort testfile | uniq -dc
    ```

  - 仅显示不重复的行

    ```bash
    sort test.txt | uniq -u
    ```

  - 仅显示重复的行，且显示重复行的所有行

    ```bash
    sort testfile | uniq -D
    ```

  - 指定比较前N个字符

    ```bash
    uniq -w3 -D test.txt #比较前三个字符是否相同
    ```

    

