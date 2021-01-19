- 帮助命令

  - whatis 简要说明cmd作用，支持正则匹配

    ```bash
    whatis ifconfig
    ```

    ```bash
    whatis -w "ifco*"
    ```

  - info 更加详细的命令信息

    ```bash
    info ifconfig
    ```

  - man 查看说明文档

    ```bash
    man date
    ```

  - whereis 查看路径

    ```bash
    whereis ifconfig
    ```

    

- 文件及目录管理

  - 创建和删除

    - 创建：mkdir

    - 删除：rm

    - 删除非空目录：rm -rf

    - 移动：mv

      ```
      mv src dest
      ```

    - 复制：cp

      ```bash
      cp -r source_dir dest_dir
      ```

  - 查找目录及文件

    - 查看当前目录下文件个数：

      ```bash
      $find ./ | wc -l
      ```

  - 查看文件内容: cat  vi  head  tail  more

    - 查看文件并显示行号：

      ```bash
      cat -n filename
      ```

    - 只看前10行：

      ```bash
      head -10 filename
      ```

    - 倒数5行： 

      ```bash
      tail -5 filename
      ```

      
