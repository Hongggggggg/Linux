 

-  cp [OPTION]...	[-T]	SOURCE DEST
   cp [OPTION]...	SOURCE... 	DIRECTORY
   cp [OPTION]...	-t 	DIRECTORY	 SOURCE...

   cp其实是cp -i的别名，所以cp -f也依旧会询问是否覆盖

  

- 功能：将源文件复制至目标文件，或将多个源文件复制至目标目录

  

- 参数：

  - -f，--force   忽略不存在的文件，从不给出提示
  - -i，--interactive 进行交互式删除
  - -r，-R，--recursive  将全部目录和自目录递归删除
  - -v，--verbose  详细显示进行的步骤
  
  
  
- 示例:

  - 复制单个文件到目标目录，目标文件存在时会询问是否覆盖：

    ```bash
    cp test.txt test_dir
    ```
    
  - 复制整个目录：
    
    ```bash
    cp -a test1 test2	#若test2存在，则会将test1复制到test2中
    					#若test2不存在，则会生成一个和test1一样的test2
    ```
    
    
    

