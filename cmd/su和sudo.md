- su [选项] [用户名]
- 功能：su 用于临时切换身份到另一个指定的用户，未指定用户名默认为 root。使用 su 切换用户身份后，默认情况下不改变当前工作目录，但会改变 HOME、SHELL、USER、LOGNAME 等 Shell 的环境变量。

- 参数：
  - -c，执行完命令后，立即恢复原来的用户身份
  - -l，切换用户身份时启动一个新的Shell。
  - -f，不必读启动文件（如csh.cshrc等），仅用于csh或tcsh两种shell
  - -m，保留原用户的shell环境变量
  - -s，使用指定的shell



- sudo [OPTIONS] [CMD]

- 功能：使用指定的用户身份执行指定的命令，无需输入指定用户的密码，只需要输入当前用户的密码，未指定用户名默认为root

- 参数：

  - -A
     使用辅助程序（可能是图形化界面的程序）读取用户的密码并将密码输出到标准输出。如果设置了环境变量 SUDO_ASKPASS，它会指定辅助程序的路径，否则，由配置文件 /etc/sudo.conf 的 askpass 选项来指定辅助程序的路径。如果没有可用的辅助程序，sudo 将错误退出
  - -b
     选项 -b（background）把 sudo 所要运行的命令放到后台运行
  - -E
     选项 -E（preserve Environment）向安全策略指示用户希望保存他们现有的环境变量。如果指定了 -E 选项，且用户没有保留环境变量的权限，则安全策略可能返回错误
  - -H
     选项 -H（Home）将 HOME 环境变量设置为目标用户的家目录，目标用户默认为 root
  - -h
     选项 -h（help）显示帮助信息并退出
  - -i [CMD]
     选项 -i（simulate initial login）将模拟初始登录，即启动目标用户在 /etc/passwd 中配置的 Shell，相关的资源文件将被读取并执行，比如 ~/.profile 和 ~/.login。如果后跟命令 CMD，则 CMD 将被传递给 Shell 并被执行
  - -K
     选项 -K（sure Kill）类似于 -k，它只用于删除了用户的缓存凭据，不能与命令或其他选项一起使用
  - -k [CMD]
     单独使用 -k（kill）选项时，使密码缓存失效，也就是下次执行 sudo 时便需要输入密码。如果后跟命令，表示忽略缓存密码，需要用户重新输入密码 ，新输入的密码不会更新密码缓存
  - -l[l] [CMD]
     如果选项 -l（list）后不跟命令，则列出 sudo 允许当前用户（或使用 -U 指定的其他用户）执行的指令和无法执行的指令。如果指定了命令并被安全策略所允许，则将显示该命令绝对路径以及命令参数。如果指定了命令不被允许，sudo 以状态码 1 退出。如果使用 -ll 或多次指定 -l 选项，则使用长格式输出
  - -n
     选项 -n（non-interactive）表示以非交互模式执行 sudo，阻止 sudo 向用户询问密码。如果执行命令时需要密码，则 sudo 将报错误信息并退出
  - -p PROMPT
     改变询问密码的提示符号
  - -s [CMD]
     选项 -s（shell）执行环境变量 SHELL 表示的 Shell，如果 SHELL 没有值，则执行目标用户在配置文件 /etc/passwd 中配置的 Shell。如果选项后跟命令，则传递给 Shell 执行，如果没有指定命令，则执行交互式 Shell
  - -U USER
     选项 -U（other user）与 -l 选项一起使用，以指定应列出其权限的用户。sudoers 策略仅允许 root 用户或当前主机上具有 ALL 权限的用户使用此选项
  - -u USER
     选项 -u（user）指定执行命令时使用的用户身份，默认为 root。如果使用 uid 则使用 *#uid 表示用户*
  - -V
     选项 -V（version）显示版本信息并退出
  - -v
     选项 -v（validate）使密码有效期延长 5 分钟

  **注意：**
  sudo 运行时要参照配置文件 /etc/sudousers ，配置文件配置了用户能够执行的命令。

- su和sudo的区别

  - su 用来长时间切换用户，常见用法是`su USERNAME`，未指定 USERNAME 默认切换至 root。
  - sudo 允许被授权的用户以其他用户或者管理员身份来执行命令，可以使用 -u 选项来指明需要使用的用户身份，默认是 root。sudo 使一般用户不需要知道超级用户的密码即可获得权限。首先超级用户将普通用户的名字、可以执行的特定命令、按照哪种用户或用户组的身份执行等信息，登记在特殊的文件中（通常是 /etc/sudoers），即完成对该用户的授权（此时该用户称为 sudoer）。若其未经授权的用户企图使用 sudo，则会发出警告的邮件给管理员。用户使用 sudo 时，必须先输入当前用户密码，如果当前用户是 root 或者当前用户与目标用户一致，无需输入密码，之后的一段时间内（默认为 5 分钟，可在 /etc/sudoers 配置），使用 sudo 不需要再次输入密码