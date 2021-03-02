- file [options] [filename]

- 功能：查看指定文件的类型信息

- 参数：

  - -b，不显示文件名
  - -i，输出MIME类型字符串：MIME 类型，即 Multipurpose Internet Mail Extensions，称为多用途互联网邮件扩展类型，用来标识和记录文件的打开方式，一些常见的类型包括：
    - text/plain：普通文本。
    - text/html：HTML文本。
    - application/pdf：PDF文档。
    - application/msword：Word文档。
    - image/png：PNG图片。
    - mage/jpeg：JPEG图片。
    - application/x-tar：TAR文件。
    - application/x-gzip：GZIP文件。
  - -L，查看软连接文件
  - -f，批量查看文本中指定的文件信息

- 示例：

  - 查看文件类型：

    ```bash
    file test.txt
    ```

  - 查看软连接文件：

    ```bash
    file -L test_s.txt #查看软连接指向的目标的信息
    ```

  - 批量查看文本中的文件：

    ```bash
    file -f file_list.txt
    ```

    

