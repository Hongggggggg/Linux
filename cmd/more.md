 

-  more  [OPTION]... FILE...
   
   

- 功能：与cat一样都是查看文件里的内容，有所不同的是more可以按页来查看文件内容，还支持直接跳转行等功能

  

- 参数：

  - +n，从第n行开始显示
  
  - -n，一次只显示n行
  
  - +/str，在文件中搜索字符串(str)，然后从该字符串前两行之后开始显示
  
  - -c，从顶部清屏，然后显示
  
  - -d，提示“Press space to continue，’q’ to quit（按空格键继续，按q键退出）”，禁用响铃功能
  
  - -I，忽略Ctrl+I（换页）字符
  
  - -p，通过清除窗口而不是滚屏来对文件进行换页，与-c选项相似
  
  - -s，把连续的多个空行显示为一行
  
  - -u把文件中的下划线去掉
  
  
  
- 常用操作：
  
  -  Enter  向下n行，默认1行
  -  Ctrl + F 向下滚动一屏
  -  Space  向下滚动一屏
  -  =  输出当前行的行号
  -  :f  输出文件名和当前行的行号
  -  V  调用v编辑器
  -  !命令  调用shell，并执行命令
  -  q  退出more
  
  
  
- 示例:

  - 显示文件中从第三行起的内容：

    ```bash
    more +3 test.txt
    ```
    
  - 从文件中查找第一个出现“abc”字符串的行，并从该处前两行开始显示：
    
    ```bash
    more +/abc test.txt
    ```
  - 设定每屏行数为5：
    
    ```bash
    more -5 test.txt
    ```
  - 分页显示一个目录下的文件：
    
    ```bash
    ls -l | more -5
    ```
    

