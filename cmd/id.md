- id [OPTION]... [USER]，OPTION 和 USER 都是可选的，如果不提供 USER，则打印当前用户的 ID 信息。

- 功能：id 命令用于查看真实有效的用户 ID（UID）和组 ID（GID）

- 参数选项：

  - -Z，显示当前用户的安全环境
  - -g，仅显示用户的所有属组
  - -G，显示用户所有的属组，包括附属组
  - -n，对于-ugG显示名称而不是数字ID
  - -r，对于-ugG显示真实ID而不是有效ID
  - -u，只显示有效用户ID
  - -z，使用NULL字符分隔条目而不是空格

- 示例：

  - 查看当前用户与属组的信息

    ```bash
    id
    uid=1000(hammer) gid=1000(hammer) groups=1000(hammer),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),131(lxd),132(sambashare)
    ```

    输出结果中，uid 表用用户 ID，gid 表示用户主组 ID，groups 表示用户所有的属组。

  - 查看当前用户的主组ID

    ```bash
    id -g
    ```

  - 查看当前用户的主组名称

    ```bash
    id -gn
    ```

    

