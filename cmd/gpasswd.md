- gpasswd [option] group

- 功能：Linux下工作组文件 /etc/group 和 /etc/gshadow 管理工具，系统管理员可以使用 -a 选项定义组管理员，使用 -m 选项定义成员，由组管理员用组名调用的 gpasswd 只提示输入组的新密码。

- 参数：

  - -a，向组group中添加用户user
  - -d，从组group中删除用户
  - -r，删除组密码
  - -R，向其成员限制访问组
  - -M，设置组GROUP的成员列表
  - -A，设置组的管理员列表

- 示例：

  - 向组test中添加用户itcast

    ```bash
    gpasswd -a itcast test
    ```

  - 从组test中删除用户

    ```bash
    gpasswd -d itcast test
    ```

  - 移除组的密码

    ```bash
    gpasswd -r test
    ```

  - 设置组的管理员列表

    ```bash
    gpasswd -A deng test
    ```

  - 给用户组创建密码：

    ```bash
    gpasswd test
    ```

    