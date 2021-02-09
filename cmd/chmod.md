- chmod [OPTION]... MODE[,MODE]... FILE...
chmod [OPTION]... OCTAL-MODE FILE...
  chmod [OPTION]... --reference=RFILE FILE...

- 功能：改变目录权限

- 参数

  - -c，发生改变时报告处理信息
  - -f，错误信息不输出
  - -R，递归处理目录
  - -v，显示详细的处理信息

- 示例：

  ```bash
  chmod 777 file
  ```
