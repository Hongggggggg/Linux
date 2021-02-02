 

-  tail  [OPTION]... [FILE]...
   
   

- 功能：显示文件末尾内容

  

- 参数：

  - -f，循环读取
  - -q，不显示处理信息
  - -v ，显示详细的处理信息
  - -c <行数>，显示的字节数
  - -n <行数>，显示的行数
  
  
  
- 显示:

  - 显示文件的末尾5行：

    ```bash
    tail -n 5 test.txt
    ```
    
  - 循环查看文件内容：
    
    ```bash
    tail -f test.txt
    ```
    
  - 从第五行开始显示文件：
    
    ```bash
    tail -n +5 test.txt
    ```

