- cksum [filename]

- 示例：

  ```bash
  cksum test.txt
  ```



- md5sum [OPTION]...  [FILE]...

- 示例：

  - 生成md5

    ```bash
    md5sum test.txt
    ```

  - 生成md5至文件中

    ```bash
    md5sum file1 file2 > file_sum.md5
    ```

  - 查看文件是否改动：

    ```bash
    md5sum -c file_sum.md5
    ```

  - 生成一个目录下的所有MD5

    ```bash
    find dir/ -type f -print -exec md5sum {} > file_sum.md5 \
    or
    find dir/ -type f -print0 xargs -0 md5sum >> file_sum.md5
    
    md5sum -c file_sum.md5#验证所有文件是否被改动
    ```



- sha1sum，用法与md5sum相同