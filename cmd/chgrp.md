-  chgrp [OPTION]... GROUP FILE...

- 功能：改变文件或目录的所属群组

- 参数

  - 必选参数：
    - -c，发生改变时输出调试信息
    - -f，不显示错误信息
    - -R，目录递归处理
    - -v，显示详细处理信息
    - --dereference 作用域符号链接的指向，而不是符号链接本身
    - --no-dereference 作用与符号链接本身
  - 可选参数：
    - --reference=<文件或者目录>
    - --help
    - --version

- 示例：

  - 改变文件的群组属性：

    ```bash
    chgrp -v bin test.txt #将text.txt群组改为bin
    ```

  - 将文件的群组属性改为与指定文件相同

    ```bash
    chgrp --reference=test.txt test1.txt #改变test1.txt的群组属性与test.txt相同
    ```

  - 改变指定目录以及其子目录下的所有文件的群组属性

    ```bash
    chgrp -R bin test_dir
    ```

    
