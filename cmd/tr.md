- tr [OPTION]... SET1 [SET2]

- 功能：用来转换或者删除一段文字。

- 参数：

  - -c，将字符集SET1以外的其他字符删除或转换为字符集SET2中的最后一个字符（如果你指定了多个字符的话）
  - -d，删除SET1这个字符串
  - -s，如果SET1中的字符连续出现多次，压缩重复的字符，只保留一个
  - -t，先将SET1的长度截为和SET2相等

- 示例：

  - 将last输出的信息中所有小写的字符变成大写字符

    ```bash
    last | tr [a-z] [A-Z]
    ```

  - 将文件中的冒号删除

    ```bash
    cat test.txt | tr -d ':'
    ```

  - 删除多余空行

    ```bash
    cat file | tr -s "\n" > new_file
    ```

  - 将文件中的“abc”替换成“xyz”

    ```bash
    cat file | tr "abc" "xyz" > new_file
    ```

  - 替换指定字符集以外的字符

    ```bash
    echo -n "alv blv" | tr -c "lv" "x"
    ```

  -  从输入文本中将不在补集中的所有字符删除

    ```bash
    echo -n "alv blv" | tr -dc "lv"
    ```

    

