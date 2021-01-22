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

    - 查看当前目录下文件个数 ./指当前目录，wc为统计指定文件中的字节数、字数、行数，-l为行数：

      ```bash
      $find ./ | wc -l
      ```

  - 查看文件内容: cat  vi  head  tail  more

    - 查看文件并显示行号：

      ```bash
      cat -n filename
      ```

    - 一页一页查看文件

      ```bash
      more filename
      ```

      ```bash
    less filename
      ```
  
    - 只看前10行：

      ```bash
    head -10 filename
      ```
  
    - 倒数5行： 

      ```bash
      tail -5 filename
      ```
  
    - 查找file中匹配的内容
    
      ```bash
      egrep *** filename
      ```
  
  - 文件与目录权限修改: 
    
    - 改变文件的拥有者 chown
    - 改变文件读写执行等属性 chmod
    

  
  
- 命令执行顺序控制：

  - 顺序执行多条命令：

    ```bash
    command1;command2;command3
    ```

  - 条件执行命令：
  
    - &&：如果前一条命令执行成功则执行下一条命令
    - ||：如果前一条执行不成功则执行下一条命令
    - $？：储存上一次命令的返回结果
  
    ```bash
    which command1 && command2 || command3
    ```
  
  
  
- 管道命令（将一个命令的输出作为下一个命令的输入）：
  
  - 管道符|
  
    - 查看文件readme.txt是否在当前目录下，将ls命令的输出发送到grep命令
  
      ```bash
      ls -l | grep readme.txt
      ```
  



  - 重定向

      - 输出重定向 >    >>:

        - 将标准输出重定向到新文件中(若存在则覆盖内容):
        
          ```bash
          echo "abcd" > filename
          ```
          
        - 将标准输出追加到文件中:
          
          ```bash
          echo "abcd" >> filename
          ```
        
      - 输入重定向 <    <<:

        - command < file，将 file 文件中的内容作为 command 的输入:

          ```
          wc -l < readme.txt
          ```
          
        - command << END 从标准输入（键盘）中读取数据，直到遇见分界符 END 才停止（分界符可以是任意的字符串，用户自己定义）:
        
          ```bash
      wc -l << END
            >123
            >456
            >789
            >END
            4
          ```
          
        - command < file1 > file2，将 file1 作为 command 的输入，并将 command 的处理结果输出到 file2。
        
          将test.txt中的内容覆盖至out.txt:
        
          ```bash
          cat > out.txt < test.txt
          ```



- 文本处理

  - find文件查找：待更新

  - grep文本搜索：

    查找指定目录/etc/acpi 及其子目录（如果存在子目录的话）下所有文件中包含字符串"update"的文件

    ```bash
    grep -r update /etc/acpi
    ```

  - wc统计行和字符：

    ```bash
    wc -l file//统计行数
    wc -w file//统计单词数
    wc -c file//统计字符数
    ```

- 特殊变量：NR、NF、$0、$1、$2

- 磁盘管理（待更新）

- 进程管理（待更新）

- 性能监控（待更新）

- 网络工具（待更新）

  - 网络路由

    - DNS查询，寻找域名对应的IP

      ```bash
      host github.com
      ```
      
      

- 用户管理

  - 用户

    - 添加用户
  
      ```bash
      useradd username
      ```
    
    - 设置密码
    
      ```bash
      passwd username
      ```
    
  - 删除用户
    
      ```bash
      userdel -r username
      ```
    
    - 切换用户
    
      ```bash
      su userB
      ```
    
  - 用户的组
    
    - 查看当前所属的组
    
        ```bash
        group
        ```
        
    - 将用户加入到组
      
      ```bash
      usermode -G groupname username
      ```
      
    - 更变用户的组（从原有的组删除）
      
      ```bash
      usermode -g groupname username
      ```
    
  - 用户权限
  
      - 更改读写权限
  
          ```bash
          chmod 740 main	将main的用户权限设置为rwxr--
          ```
          
      - 更改文件或目录的拥有者
        
        ```bash
        chown -R username dirFile    -R表示递归选项
        ```
  
- 系统管理

  - 查询系统版本

    ```bash
    uname -a
    ```
    
  - 查询CPU信息：
    
    ```bash
    sar -u 5 10		5s更新一次，共10条数据
    ```
    
  - 查看内存信息
  
    ```bash
    cat /proc/meminfo
    ```
- IPC资源管理（待更新）
  