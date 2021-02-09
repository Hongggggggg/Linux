- tar 必要参数 可选参数 文件

- 命令功能：将文件打包（tar只进行打包，压缩是通过其他指令执行的）

- 命令参数：

  - 必要参数
    - -A，新增压缩文件到已存在的压缩
    - -B，设置区块大小
    - -c，建立新的压缩文件
    - -d，记录文件的差别
    - -r，添加文件到已经压缩的文件
    - -u，添加改变了和现有的文件到已经存在的压缩文件
    - -x，从压缩的文件中提取文件
    - -t，显示压缩文件的内容
    - -z，支持gzip解压文件
    - -j，支持bzip2解压文件
    - -Z，支持compress解压文件
    - -v，显示操作过程
    - -I，文件系统边界设置
    - -k，保留原有文件不覆盖
    - -m，保留文件不被覆盖
    - -W，确认压缩文件的正确性
  - 可选参数：
    - -b 设置区块数目
    - -C 切换到指定目录
    - -f 指定压缩文件
    - --help 显示帮助信息
    - --version 显示版本信息

- 常见压缩和解压命令：

  - tar

    ```bash
    tar xvf FileName.tar #解包
    tar cvf FileName.tar DirName #打包
    ```

  - gzip/gunzip

    ```bash
    gzip FileName #压缩
    gunzip FileName.gz #解压
    gzip -d FileName.gz #解压
    ```

  - .tar.Z

    ```bash
    tar Zxvf FileName.tar.Z	#解压
    tar Zcvf FileName.tar.Z DirName #压缩
    ```

  - .zip

    ```bash
    unzip FileName.zip #解压
    zip FileName.zip DirName #压缩
    ```

  - .rar

    ```bash
    rar x FileName.rar #解压
    rar a FileName.rar DirName #压缩
    ```



- 示例

  - 将文件打包

    ```bash
    tar -cvf test.tar test1.txt test2.txt #仅打包，不压缩
    tar -zcvf test.gz test1.txt test2.txt #打包后以gzip压缩
    tar -jcvf test.tar.bz2 test1.txt test2.txt #打包后以bzip2压缩
    ```

  - 查看tar包中有哪些内容

    ```bash
    tar -ztvf test.tar.gz #由于查看的是.gz，所以要加上z这个参数
    ```

  - 解压缩

    ```bash
    tar -zxvf test.tar.gz
    tar -zxvf test.tar.gz test1.txt #单独解压出其中一个文件
    ```

    

