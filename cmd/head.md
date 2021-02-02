 

-  head  [OPTION]... [FILE]...
   
   

- 功能：显示文档开头至标准输出中，默认打印10行

  

- 参数：

  - -q，隐藏文件名
  - -v，显示文件名
  - -c <字节>，显示字节数
  - -n <行数>，显示的行数
  
  
  
- 显示:

  - 显示文件的前5行：

    ```bash
    head -n 5 test1.txt
    ```
    
  - 显示文件的前n个字节：
    
    ```bash
    head -c 20 test.txt
    ```
    
  - 显示除了最后20个字节的所有内容：
    
    ```bash
    head -c -20 test.txt
  ```
  
  - 显示除了最后5行的所有内容：
    
    ```bash
    head -n -5 test.txt
    ```