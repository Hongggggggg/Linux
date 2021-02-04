 

-  locate - find files by name
   
   locate [OPTION]... PATTERN...

   
   
- 功能：在数据库中找到文件，由于是从数据库中搜索，会比find命令直接从硬盘中搜索快得多，但若数据库没及时更新，很可能会找不到相应的内容

  

- 参数：

  -  -a，打印所有符合的结果
  -  -e，将排除在寻找的范围之外
  -  -i，忽略大小写
  -  -q，不会显示任何错误信息
  -  -r，使用正则表达式
  -  -d，指定数据库的路径
  -  -h，--help
  -  -V，--version
  
- 示例:

  - 查找和pwd相关的所有文件：

    ```bash
    locate pwd
    ```
    
  - 搜索etc目录下所有以sh开头的文件：
    
    ```bash
    locate /etc/sh
    ```

