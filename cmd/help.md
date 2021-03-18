- help [-dms] [PATTERN...]

- 功能：help 命令是 Bash 内建命令，用于查看 Bash 内部命令的帮助信息。

- 选项：

  - -d，输出每个命令的简短描述
  - -m，以类似于man手册的格式描述
  - -s，只显示命令使用格式

- 示例：

  - 查看help自身的帮助信息

    ```bash
    help help
    ```

  - 以类似于man手册格式查看help命令的帮助信息

    ```bash
    help -m help
    ```

  - 查看help命令的简短描述

    ```bash
    help -d help
    ```

  - 查看help和cd命令使用格式

    ```bash
    help -s help cd
    ```

    
