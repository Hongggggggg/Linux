- usermod [OPTIONS] LOGIN

- 功能：系统管理员命令，用于修改用户账号，usermod可用来修改用户账号的各项设定，修改系统账号文件来反映通过命令行指定的变化。

- 选项：

  - -c，添加设备信息
  - -d，设置用户的新主目录
  - -e，设定账户的过期日期
  - -f，设定过期几天后，密码为失效状态
  - -g，--gid GROUP，强制使用GROUP为新组
  - -G，--groups GROUPS，新的附加组列表GROUPS
  - -a，--append GROUP，将用户追加至上边-G中提到的附加组中，并不从其他组中删除此用户
  - -l，设置新的登录名
  - -L，锁定用户账号
  - -m，将家目录内容移至新的位置（仅和-d一起使用）
  - -o，允许使用重复的UID
  - -p，将加密过的密码设为新密码
  - -s，设置该用户的账号新登录shell
  - -u，设置用户账号的新UID
  - -U，解锁用户账号
  - -Z，用户账户的新SELinux用户映射

- 示例：

  - 修改用户的家目录

    ```bash
    usermod -d /home/hammer hammer
    ```

  - 改变用户的uid

    ```bash
    usermod -u 888 hammer
    ```

  - 修改用户名为hammer

    ```bash
    usermod -l hammer tom
    ```

  - 锁定hammer用户

    ```bash
    usermod -L hammer
    ```

  - 解锁hammer用户

    ```bash
    usermod -U hammer
    ```

  - 添加新的附加组

    ```bash
    usermod -G deng hammer
    ```

  - 修改用户登录shell

    ```bash
    usermod -s /bin/sh hammer
    ```

  - 修改用户的GID

    ```bash
    usermod -g 1003 hammer
    ```

  - 指定账号过期日期

    ```bash
    usermod -e 2021-10-10 hammer
    ```

  - 指定用户账号密码过期多少天后禁用该账号

    ```bash
    usermod -f 3 hammer
    ```

    

