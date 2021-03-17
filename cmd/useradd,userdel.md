- userdel [options] LOGIN

- 功能：userdel（user delete） 命令是系统管理员命令，用于删除用户账户和相关文件。

  其实 userdel 命令实际上是修改了系统的用户账号文件 /etc/passwd、/etc/shadow 以及 /etc/group 文件，这与 Linux 系统“一切操作皆文件”的思想正好吻合。

  ​	值得注意的是，如果有该要删除用户相关的进程正在运行，userdel 命令通常不会删除一个用户账号。如果确实必须要删除，可以先终止用户进程，然后再执行userdel命令进行删除。但是 userdel 命令也提供了一个面对该种情况的参数，即 -f 选项。

- 选项：

  - -f，强制删除用户，即使用户当前已经登录
  - -r，删除用户的同事删除与用户相关的所有文件，比如删除主目录和邮件池
  - -R，--root CHROOT_DIR，在CHROOT_DIR目录种应用更改并使用CHROOT_DIR目录中的配置文件
  - -Z，为用户删除所有的SELinux用户映射

- 示例：

  - 删除用户，但不删除其家目录及文件

    ```bash
    userdel user
    ```

  - 删除用户并删除所有相关文件，比如主目录和邮件池

    ```bash
    userdel -r user
    ```

  - 强制删除用户

    ```bash
    userdel -f user
    ```

    

- useradd [options] LOGIN
  useradd -D
  useradd -D [options]

- 参数选项：

  - -b, --base-dir BASE_DIR
     新账户的主目录的基目录
  - -c, --comment COMMENT
     新账户的备注信息，备注信息保存在 /etc/passwd 的备注栏中
  - -d, --home-dir HOME_DIR
     新账户的主目录
  - -D, --defaults
     显示或更改默认的 useradd 配置
  - -e, --expiredate EXPIRE_DATE
     新账户的过期日期，日期格式为 YYYY-MM-DD。如果未指定，useradd 将使用在 /etc/default/useradd 中指定的到期日期 EXPIRE，或默认情况下使用空字符串(无过期)
  - -f, --inactive INACTIVE
     指定在密码过期后多少天即关闭该账号。如果为 0 账号立即被停用；如果为 -1 则账号一直可用。默认值为 -1
  - -g, --gid GROUP
     指定用户所属的主组。主组必须已经存在
  - -G, --groups GROUPS
     指定用户所属的附加组，多个组使用逗号分隔
  - -h, --help
     显示帮助信息并推出
  - -k, --skel SKEL_DIR
     指定用户的骨架目录。与选项 -m （或 --create-home）联用，骨架目录包含要复制到用户主目录中的文件和目录
  - -K, --key KEY=VALUE
     不使用 /etc/login.defs 中的默认值（UID_MIN、UID_MAX、UMASK、PASS_MAX_DAYS 等）
  - -l, --no-log-init
     不要将此用户添加到最近登录和登录失败数据库
  - -m, --create-home
     创建用户的家目录。useradd 默认会创建 home 目录，除非 /etc/login.defs 中的 CREATE_HOME 设置为no
  - -M, --no-create-home
     不创建用户的主目录。即使 /etc/login.defs 中的 CREATE_HOME 设置为 yes
  - -N, --no-user-group
     不创建同名的组
  - -o, --non-unique
     允许使用重复的 UID 创建用户
  - -p, --password PASSWORD 
     设置账户密码，注意是使用 crypt(3) 加密后的用户密码，不是密码的明文。默认是用户密码不可用。推荐使用 passwd 命令给用户设置密码
  - -r, --system
      创建一个系统账户
  - -R, --root CHROOT_DIR
     设置根目录。在 Linux 系统中，系统默认的根目录是 /
  - -s, --shell SHELL 
     新账户的登录 Shell
  - -u, --uid UID
     新账户的用户 ID
  - -U, --user-group
     创建与用户同名的组，并将用户添加到此组中。为默认动作，除非 /etc/login.defs 中 USERGROUPS_ENAB 被设置为 no 或显示使用选项 -N, --no-user-group
  - -Z, --selinux-user SEUSER
     为 SELinux 用户映射使用指定 SEUSER

- 示例：

  - 添加新用户

    ```bash
    useradd hammer
    ```

    默认在创建用户时的同时会创建一个同名的用户主组和在 /home 目录下同名的家目录，除非在配置文件 /etc/login.defs 中 USERGROUPS_ENAB 和 CREATE_HOME 被设置为 no。

  - 添加新用户时指定家目录和所属组

    ```bash
    useradd -d /home/hammer -g root hammer
    ```

  - 添加用户，并设置密码

    ```bash
    useradd hammer
    passwd hammer
    ```

  - 添加用户并设置有效期

    ```bash
    useradd -e 2021-10-20 hammer
    ```

  - 查看创建新用户时的默认信息

    ```bash
    useradd -D
    #或
    cat /etc/default/useradd
    ```

  - 修改创建新用户时的默认信息

    ```bash
    useradd -D -f 0
    ```

    

