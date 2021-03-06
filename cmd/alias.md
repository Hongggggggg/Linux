- alias [-p] [NAME[=VALUE] ...]

- 功能：设置命令的别名，不带参数或使用-p选项时，会打印所有别名列表

- 参数：

  - -p，以可重用的格式  alias name = value 打印所有已定义的别名

- 示例：

  - 查看所有已定义的别名：

    ```bash
    alias
    alias -p # 同上
    ```

  - 查看指定命令的别名：

    ```bash
    alias ll
    ```

  - 设置命令别名：

    ```bash
    alias ll = “ls -l --color=auto -h”
    ```

    

- unalias [-a] [NAME...]

- 功能：删除命令别名

- 参数：

  - -a，删除所有的别名定义

- 示例：

  - 删除指定别名：

    ```bash
    unalias ll
    ```

  - 删除所有别名：

    ```bash
     unalias -a
    ```

    