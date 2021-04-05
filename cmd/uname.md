- uname [OPTION]...
- 功能：uname 命令用于打印当前系统相关信息（内核版本号、硬件架构、主机名称和操作系统类型等）。
- 参数选项：
  - -a, --all
     显示主机全部信息，以下面的顺序展示
  - -s, --kernel-name
     显示内核名称
  - -n, -nodename
     显示在网络上的主机名称
  - -r, --kernel-release
     显示操作系统内核发行版本号
  - -v, --kernel-version
     显示内核版本号
  - -m, --machine
     显示机器硬件架构
  - -p, --processor
     显示处理器类型或者 unknown
  - -i, --hardware-platform
     显示硬件平台或 unknown
  - -o, --operating-system
     显示操作系统名称

- 示例：

  - 显示主机名称：

    ```bash
    uanme -n
    ```

  - 显示操作系统名称：

    ```bash
    uname -o
    ```

  - 显示操作系统内核名称：

    ```bash
    uname -s
    ```

  - 显示操作系统内核版本：

    ```bash
    uname -r
    ```

  - 显示主机全部信息

    ```bash
    uname -a
    ```

    