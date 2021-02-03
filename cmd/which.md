 

-  which - locate a command
   
   which [-a] filename ...

   
   
- 功能：在PATH指定的路径中，搜索某个系统命令或文件的位置，并返回第一个搜索结果

  

- 参数：

  - -a	打印所有符合的路径
  
  
  
- 示例:

  - 查找命令路径：

    ```bash
    which lsmode
    ```
    
  - 查找cd路径：
    
    ```bash
    which cd	#结果为空，原因是cd为bash内建命令，which默认是找PATH内所规定的目录，所以找不到
    ```
    
    

