- rm [选项]  [dirName]

  

- 功能：删除一个目录中的一个或多个文件或目录，若没有使用-r选项，则rm不会删除目录。如果使用rm来删除文件，通常仍可以将该文件恢复原状。

  

- 参数：

  - -f，--force   忽略不存在的文件，从不给出提示
  - -i，--interactive 进行交互式删除
  - -r，-R，--recursive  将全部目录和自目录递归删除
  - -v，--verbose  详细显示进行的步骤
  
  
  
- 示例:

  - 删除文件：

    ```bash
    rm file_name
    ```
    
  - 删除文件，删除前逐一询问确认：
    
    ```bash
    rm -i file_name
    rm -i *.txt		删除所有txt文件
    ```
    
  - 递归删除目录：
    
    ```bash
    rm -r dir
    ```
  - 强制删除目录，并且不用一一确认：
    
    ```bash
    rm -rf dir
    ```
    

