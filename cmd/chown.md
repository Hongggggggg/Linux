-  chown [OPTION]...\[OWNER][:[GROUP]] FILE...

- 功能：改变文件的拥有者和群组。

- 参数

  - 必选参数：
    - -c，显示更改部分的信息
    - -f，不显示错误信息
    - -h，修复符号链接
    - -R，目录递归处理
    - -v，显示详细处理信息
    - --dereference 作用域符号链接的指向，而不是符号链接本身
  - 可选参数：
    - --reference=<文件或者目录>
    - --from=<当前用户：当前群组>只有当前用户和群组和指定的的用户和群组相同时才进行改变
    - --help
    - --version

- 示例：

  - 改变拥有者和群组：

    ```bash
    chown owner:group test.txt 
    chown root: test.txt #group若与owner相同可省略
  ```
  
- 改变群组
  
    ```bash
    chwon :root test.txt #只改变群组为root，不该百年拥有者
  ```
  
- 改变指定目录以及其子目录下的所有文件的拥有者和群组
  
    ```bash
    chown -R -v root:hammer test_dir
  ```
  
    
