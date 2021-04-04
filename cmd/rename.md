- rename [OPTIONS] EXPRESSION REPLACEMENT FILE...

  EXPRESSION：原字符串，即文件名需要替换的字符串；
  REPLACEMENT ：目标字符串，将文件名中含有的原字符替换成目标字符串；
  FILE…：指定要改变文件名的文件列表。

  rename支持的通配符：

  ​	?，可替代单个字符

  ​	*，可替代多个字符
  ​	[charset]，可替代charset集中的任意单个字符

- 功能：可实现文件或目录的重命名

- 参数：

  - -s, --symlink
     不要重命名符号链接，而是重命名它的目标
  - -v, --verbose
     以冗余模式运行，显示哪些文件已被重命名
  - -o, --no-overwrite
     不要覆盖现有文件
  - -i, --interactive
     更名前询问是否确定

- 示例：

  - 重命名文件lvlv为lala

    ```bash
    rename v a lv？？
    ```

  - 将当前目录下的所有文件的后缀名由.html改为.php

    ```bash
    rename .html .php *
    ```

    

  

