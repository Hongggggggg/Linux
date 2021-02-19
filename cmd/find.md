 

-  find  pathname  -options  [-print -exec -ok ...]
   
- 功能：在文件书中查找文件并作出相应的处理

- 参数：

  - pathname：所查找的路径，. 表示当前路径，/表示根目录
  
  - print：将匹配的文件输出到标准输出
  
  - exec：find命令对匹配的文件执行该参数所给的shell命令。相应命令的形式为’command‘ {}；
  
  - -ok：和-exec的作用相同，只不过以一种更为安全的模式来执行该参数所给出的shell命令。在执行每一个命令之前都会给出提示，让用户来确定是否执行。
  
    
  
- 命令选项

  - -name  按照文件名查找文件

  - -perm  按照文件权限来查找文件
  
  - -prune  使用这一选项可以使find命令不在当前指定的目录中查找
  
  - -uers  按照文件属主来查找文件
  
  - -group 按照文件所属组来查找文件
  
  - -mtime -n +n 按照文件的更改时间来查找文件，-n表示文件更改时间距现在n天以内，+n表示文件更改时间距现在n天以前。
  
  - nogroup  查找无有效所属组的文件，即该文件所属组在/etc/groups中不存在
  
  - nouser  查找无有效属主的文件，即该文件的属主在/etc/passwd中不存在
  
  - -type：查找某一类型的文件，诸如：
  
    - b  块设备文件
  
    - d  目录
  
    - c 字符设备文件
  
    - p 管道文件
  
    - I 符号链接文件
  
    - f 普通文件
  
  - -size n：[c] 查找文件长度为n块的文件，带有c时表示文件长度以字节计。-depth：在查找文件时，首先查找当前目录中的文件，然后再在其子目录中查找
  
  - -fstype：查找位于某一类型文件系统中的文件，这些文件系统类型通常可以在配置文件/etc/fstab中找到，该配置文件中包含了本系统中有关文件系统的信息。
  
  - mount：在查找文件时不跨越文件系统mount点
  
  - follow：如果find命令遇到符号链接文件，就跟踪至链接所指向的文件。
  
  - -cpio：对匹配的文件使用cpio命令，将这些文件备份到磁带设备中。
  
    
  
- 示例:

  -  name选项：

    - 在当前目录查找以.txt结尾的文件
    
      ```bash
      find . -name "*.txt"
      ```
      
    - 在当前目录及子目录中查找以大写字母开头的文件
    
      ```bash
    find . -name "[A-Z]*"
      ```

  - perm 选项：

    - 按照目录或文件的权限来查找文件：

      ```bash
    find . -perm 777
      ```
    
  - 查找指定时间内修改过的文件：

    ```bash
    find -atime -2	#查找48h内修改过的文件
    ```

  - 按类型查找文件：

    ```bash
    find . -type f -name ".txt" #在当前目录查找.txt结尾的普通文件
    ```
    
  - 查找当前所有目录并排序：
    
      ```bash
      find . -type d|sort
      ```

  - 按大小查找文件：

    ```bash
    find . -size +1000c -print	#查找当前目录大于1k的文件
    ```
  - 忽略某个目录：

    ```bash
    find test -path "test/test1" -prune #查找test下所有文件，忽略test/test1
    ```

  - 按文件属主查找文件：

    ```bash
    find ~ -user hammer #查找属主为hammer的文件
    ```
    
    

- find exec:

  -exec 参数后面跟的是command命令，它的终止是以；为结束标志的，所以这句命令后面的分号是不可或缺的，考虑到各个系统中会有不同的意义，所以前面加反斜杠。

  {} 花括号代表前面find找出来的文件名。

  使用find时，只要把想要的操作写在一个文件里，就可以用exec来配合find查找。

  exec选项后面跟随着所要执行的命令或脚本，然后是一对儿{ }，一个空格和一个\，最后是一个分号。为了使用exec选项，必须要同时使用print选项

  - ls -l  命令放在find命令的-exec选项中

    ```bash
    find . -type f -exec ls -l {} \; #匹配当前目录下的所有普通文件，并在-exec选项中使用ls -l命令将它们列出
    ```

  - 在目录中查找更改时间在n日以前的文件并删除它们

    ```bash
    find . -type f -mtime +14 -exec rm {} \;
    ```
  - -exec中使用grep命令

    ```bash
    find /etc -name "passwd*" -exec grep "root" {} \; #find命令首先匹配所有文件名为“ passwd*”的文件，例如passwd、passwd.old、passwd.bak，然后执行grep命令看看在这些文件中是否存在一个root用户。
    ```
    
  - 查找文件移动到指定目录

    ```bash
    find . -name "*.log" -exec mv {} .. \;
    ```
  - 用exec选项执行cp命令

    ```bash
    find . -name "*log" -exec cp {} test \; 
    ```
