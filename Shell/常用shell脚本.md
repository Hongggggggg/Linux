- 字符串

  - 去除字符串首尾空格

    ```shell
    trim_string() {
        : "${1#"${1%%[![:space:]]*}"}"
        : "${_%"${_##*[![:space:]]}"}"
        printf '%s\n' "$_"
    }
    ```

    示例:

    ```shell
    $ trim_string "  Hello,   World   "
    Hello,   World
    
    $name="   Han  Meimei   "
    $trim_string "$name"
    Han  Meimei
    ```

    解析：

    - : 内置用于代替临时变量

    - $_ (下划线) 表示的是打印上一个输入参数行, 当这个命令在开头时, 打印输出文档的绝对路径名.

      ```shell
      $: "abc"
      $echo "$_"
      abc
      ```

    - [[:space:]]是正则表达式中的POSIX一个表达式表示所有空白符，包括tab和space

      [^[:space:]]与[![:space:]]等效为非空白符，[更多正则表达式说明](http://baiy.cn/utils/_regex_doc/index.htm)

      *表示任意次匹配

      所以[![:space:]]*表示非空白字符的任意次匹配

    - 字符串截取：

      | 格式                       | 说明                                                         |
      | -------------------------- | ------------------------------------------------------------ |
      | ${string: start :length}   | 从 string 字符串的左边第 start 个字符开始，向右截取 length 个字符。 |
      | ${string: start}           | 从 string 字符串的左边第 start 个字符开始截取，直到最后。    |
      | ${string: 0-start :length} | 从 string 字符串的右边第 start 个字符开始，向右截取 length 个字符。 |
      | ${string: 0-start}         | 从 string 字符串的右边第 start 个字符开始截取，直到最后。    |
      | ${string#*chars}           | 从 string 字符串第一次出现 *chars 的位置开始，截取 *chars 右边的所有字符（删除左边字符，保留右边字符）。 |
      | ${string##*chars}          | 从 string 字符串最后一次出现 *chars 的位置开始，截取 *chars 右边的所有字符。 |
      | ${string%chars*}           | 从 string 字符串最后一次出现 *chars 的位置开始，截取 *chars 左边的所有字符。 |
      | ${string%%chars*}          | 从 string 字符串第一次出现 *chars 的位置开始，截取 *chars 左边的所有字符。 |

      由上可得"${1%%[![:space:]]*}"表示截取$1这个字符串中第一个非空白字符的左边所有字符既字符串开头的所有空格

      假设字符串为“   ABC   ”，得到的结果既为ABC前面的三个空格"   "

      ${1#"${1%%[![:space:]]*}"}"既表示为$1这个字符串中开头空格的右边所有字符串

      假设字符串为“   ABC   ”,得到的结果既为"ABC   "

