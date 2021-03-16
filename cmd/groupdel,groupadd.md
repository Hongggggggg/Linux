- groupdel [OPTIONS] GROUP

- 功能：删除一个组，groupdel 命令用于删除指定的工作组，本命令要修改的系统文件包括 /ect/group 和 /ect/gshadow。

- 示例：

  - 删除用户组

    ```bash
    groupdel g1
    ```



- groupadd [OPTIONS] GROUP

- 功能：命令是系统管理员命令，用于创建一个新组，命令使用命令行上指定的值以及系统中的默认值创建一个新的组帐户。新组将根据需要被添加到系统文件中。

- 常用选项：

  - -f，如果组已经存在则成功退出，如果GID已经存在则取消
  - -g，为新组使用GID
  - -k，不使用 /etc/login.defs 中的默认值
  - -o，允许创建有重复GID的组
  - -p，为新组使用加密过的密码
  - -r，创建一个系统组

- 示例：

  - 添加一个新组

    ```bash
    groupadd g1
    ```

  - 添加一个用户组并指定GID

    ```bash
    groupadd -g 888 g2
    ```

  - 使用-r创建系统工作组

    ```bash
    groupadd -r -g 889 g3
    ```

  - 允许创建有重复GID的组

    ```bash
    groupadd -o -r -g 889 g4
    ```

    