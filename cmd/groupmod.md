- groupmod [OPTIONS] GROUP

- 功能：系统管理员命令，用于更改群组识别码或名称。

- 参数：

  - -g，将组ID改为GID
  - -n，改名为NEW_GROUP
  - -o，允许使用重复的GID
  - -p，将密码更改为PASSWORD

- 示例

  - 更改用户组ID

    ```bash
    groupmod -g 8888 g5
    ```

  - 更改用户组名

    ```bash
    groupmod -n heima g5
    ```

  

