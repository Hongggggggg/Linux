 

-  touch [OPTION]... FILE...
   
   

- 功能：创建新文档，更改文档或目录的日期时间

  

- 参数：

  - -a，只更改存取时间
  - -c，--no-creat 不建立任何文档
  - -d，使用指定的时间代替
  - -m，只更改变动时间
  - -r，将指定文档或目录的时间改为参考文档或目录的时间
  - -t，使用指定的时间日期
  
  
  
- 示例:

  - 创建不存在的文件：

    ```bash
    touch test1 test2 test3
    ```
    
  - 更新时间：
    
    ```bash
    touch -r test1 test2	#更新test1的时间和test2相同
    ```
  - 设定文件的时间戳：
    
    ```bash
    touch -t [[CC]YY]MMDDhhmm[.SS] test1
    ```
    
    

