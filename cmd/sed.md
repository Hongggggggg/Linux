- sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  script-only-if-no-other-script 为处理动作，可以由-e指定多个

- 功能：sed（Stream EDitor）是一种流文件编辑器，它一次处理一行内容。

  ​	处理时，把当前处理的行存储在临时缓冲区中，称为“模式空间”（Pattern Space），接着用 sed 命令处理缓冲区中的内容，处理完成后，把缓冲区的内容送往屏幕，接着处理下一行，直到文件末尾。

  ​	文件内容不会被改变，除非使用-i选项。sed 主要用来编辑一个或多个文件，简化对文件的反复操作或者用来编写转换程序等。

  ​	sed 功能同 awk 类似，差别在于，sed 简单，对列处理的功能要差一些，awk 功能复杂，对列处理的功能比较强大。

- 参数：
  - -n，不打印STDIN的数据。
  - -e \<script>，指定sed动作，可以由多个-e指定多个动作。
  - -f  \<script-file>，直接将sed的动作写在又给文件内
  - -r，sed支持拓展正则表达式
  - -i，直接修改读取的文件内容，而不是输出到终端
  - 动作说明： [n1, [n2]] function，
    - n1，n2不一定存在，一般表示选择进行动作的行数
      - 举例说明：如果我的动作是需要在 10 到 20 行之间进行，则写作“10,20动作行为
    - function：
      - a ：新增， a 的后面可以接字串，而这些字串会在新的一行出现(目前的下一行)
      - c ：取代， c 的后面可以接字串，这些字串可以取代 n1,n2 之间的行！
      - d ：删除，因为是删除，所以 d 后面通常不接任何内容；
      - i ：插入， i 的后面可以接字串，而这些字串会在新的一行出现(目前的上一行)；
      - p ：列印，亦即将某个选择的数据印出。通常 p 会与参数 sed -n 一起运行～
      - s ：替换，通常这个s的动作可以搭配正规表示法！例如 1,20s/old/new/g。

- 示例：

  - 删除行操作：

    - 将 /etc/passwd 的内容列出并且列印行号，同时，请将第 2~5 行删除

      ```bash
      nl -n ln /etc/passwd | sed '2,5d'
      ```

    - 只删除第二行：

      ```bash
      nl /etc/passwd | sed '2d'
      ```

  - 新增行操作：

    - 在第二行后面加上“hello world”

      ```bash
      nl -nln /etc/passwd | sed '2a hello world'
      nl -nln /etc/passwd | sed '2a hello world\nHello World' #加两行
      nl -nln /etc/passwd | sed '2a I like drinking tea\
      > I like drinking beer' #或者每一行使用反斜杠\来分开，就可以在命令行中将一条命令分开多行输入
      ```

  - 替换行操作：

    - 将第2-5行的内容替换成为"No 2-5 number"。

      ```bash
      nl -nln /etc/passwd | sed '2,5c No 2-5 number'
      ```

  - 选择行打印

    - 仅列出 /etc/passwd 文件内的第 5-7 行

      ```bash
      nl -nln /etc/passwd | sed -n '5,7p'
      ```

  - 数据的查找：

    - 搜索 /etc/passwd有root关键字的行并输出

      ```bash
      nl /etc/passwd | sed -n '/root/p'
      ```

    - 删除/etc/passwd所有包含root的行，其他行输出

      ```bash
      nl /etc/passwd | sed '/root/d'
      ```

    - 数据的查找并替换：

      ```bash
      sed 's/被取代的字串/新的字串/g
      ```

    - 搜索/etc/passwd,找到root对应的行，执行后面花括号中的一组命令，每个命令之间用分号分隔，这里把bash替换为blueshell，再输出这行：

      ```bash
      nl /etc/passwd | sed -n '/root/{s/bash/blueshell/;p}'
      ```

  - 多点编辑：

    - 一条sed命令，删除/etc/passwd第三行到末尾的数据，并把bash替换为blueshell：

      ```bash
      nl /etc/passwd | sed -e '3,$d' -e 's/bash/blueshell/'
      ```

  - 修改文件：

    - 将 test.txt 内每一行结尾若为 . 则换成 !

      ```bash
      sed -i 's/\.$/!/g' test.txt #$表示结尾
      ```

    - 直接在test.txt 最后一行加入"# This is a test"

      ```bash
      sed -i '$a # This is a test' test.txt #$ 代表的是最后一行
      ```

      

    

