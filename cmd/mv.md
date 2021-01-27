- mv [选项] [源文件或目录] [目标文件或目录]
- 功能：根据第二个参数类型做区分是重命名文件还是将源文件移动至目标目录
- 常用参数：
  - -b：若需覆盖文件，则覆盖前先行备份
  - -f：不询问，强制覆盖
  - -i：目标文件存在时，询问是否覆盖
  - -u：若目标文件已经存在，且source比较新，才会更新(update)
  - -t：移动多个源文件至一个目录，此时目标目录在前，源文件在后
  
- 范例:

  - 文件改名：

    ```bash
    mv test.txt test1.txt	将text.txt名字修改为test1.txt
    ```
    
  - 移动文件：
    
    ```bash
    mv test.txt dir		将test.txt移动到dir目录中
    ```
    
  - 将多个文件移动到目录中：
    
    ```bash
    mv test1.txt test2.txt test3.txt test_dir
    mv -t /gcc/test_dir test1.txt test2.txt test3.txt
    ```
  - 移动(重命名)目录：
    
    ```bash
    mv dir1 dir2	若dir2存在，则将dir1移动至dir2,否则将dir1改名为dir2
    ```
  - 移动当前文件夹下的所有文件到上一级目录：
    
    ```bash
    mv * ../
    ```

