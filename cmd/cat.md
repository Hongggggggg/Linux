- cat  [OPTION]...  [FILE]...

- 功能：

  -  显示整个文件：cat  filename
  -  创建一个文件：cat  >  filename 只能创建新文件，不能编辑已有文件
  -  将几个文件合并为一个文件：cat  file1  file2  >  file

- 参数：

  - -A，--show-all
  
  - -b，--number-nonblank    对非空输出行编号
  
  - -E，--show-ends    在每行结束处显示$
  
  - -n，--number    对输出的所有行编号
  
  - -s，有两行以上的空白行，就替换为一行空白行
  
  - -T，--show-tabs    将跳格字符显示为^|
  
    
  
- 示例:

  - 同时显示两个文件并且带上行号：

    ```bash
    cat -n test1 test2
    ```
    
  - 逆序输出：
    
    ```bash
    tac test1
    ```
    
    

