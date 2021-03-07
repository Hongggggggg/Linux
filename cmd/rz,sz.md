- rz [OPTIONS]

- 功能：将文件批量上传至linux服务器，不能上传文件夹

- 参数：

  - -+，将文件追加到已存在的同名文件
  - -a，以文本方式传输
  - -b，以二进制方式传输
  - --delay-startup N，等待N秒
  - -e，对所有控制字符转义
  - -p，对ZMODEM协议有效，如果目标文件已存在则跳过
  - -q，不输出提示信息
  - -v，输出提示信息
  - -y，存在同名文件则替换
  - --X，使用XMODEM协议
  - --ymodem，使用YMODEM协议
  - -Z，使用ZMODEM协议

- 示例：

  - 以二进制、并对字符进行转义，替换已存在的同名文件

    ```bash
    rz -bye
    ```

    

- sz [OPTIONS] FILES

- 功能：通过ZMODEM协议将多个文件从远程服务器下载到本地

- 参数：与rz基本相同

- 示例：

  - 下载多个文件

    ```bash
    sz file1 file2
    ```

    