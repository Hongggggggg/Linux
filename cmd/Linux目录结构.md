- [Linux目录结构](https://mp.weixin.qq.com/s?__biz=MzAxODI5ODMwOA==&mid=2666540201&idx=2&sn=f1e89f7d92131f636536500671d3ecd2&chksm=80dce802b7ab61140852e1d88c34bdcc5ca2e13b5f36dbd54c7b61649a69ffdff50f777fabc8&scene=21#wechat_redirect)

- 四种类型：

  - 可分享的：

    ​    可以分享给其他系统挂载使用的目录，所以包括执行文件与用户的邮件等数据，是能够分享给网络上其他主机挂载用的目录。

  - 不可分享的：

    ​    自己机器上面运作的装置文件或者是与程序有关的socket文件等，

  - 不变的：

    ​    有些数据不会经常变动，跟随这distribution而不变动。例如函数库、说明文档、系统管理员所管理的主机服务配置文件等

  - 可变动的：

    ​    经常改变的数据，例如登录文件等。


​    

- 根目录（/）的内容：

  | 目录   | 应放置档案内容                                               |
  | ------ | ------------------------------------------------------------ |
  | /bin   | 系统有很多放置执行档的目录，但/bin比较特殊。因为/bin放置的是在单人维护模式下还能够被操作的指令。在/bin底下的指令可以被root与一般帐号所使用，主要有：cat,chmod(修改权限), chown, date, mv, mkdir, cp, bash等等常用的指令。 |
  | /boot  | 主要放置开机会使用到的文件，包括Linux核心文件以及开机选单与开机所需设定文件等等。Linux kernel常用的档名为：vmlinuz ，如果使用的是grub这个开机管理程式，则还会存在/boot/grub/这个目录。 |
  | /dev   | 在Linux系统上，任何装置与周边设备都是以文件的型态存在于这个目录当中。 只要通过存取这个目录下的某个文件，就等于存取某个装置。比要重要的档案有/dev/null, /dev/zero, /dev/tty , /dev/lp*, / dev/hd*, /dev/sd*等等 |
  | /etc   | 系统主要的配置文件几乎都放置在这个目录内，例如人员的帐号密码文件、各种服务的启始文件等等。 一般来说，这个目录下的各文件属性是可以让一般使用者查阅的，但是只有root有权力修改。 FHS建议不要放置可执行文件(binary)在这个目录中。 比较重要的文件有：/etc/inittab, /etc/init.d/, /etc/modprobe.conf, /etc/X11/, /etc/fstab, /etc/sysconfig/等等。 另外，其下重要的目录有：/etc/init.d/ ：所有服务的预设启动script都是放在这里的，例如要启动或者关闭iptables的话： /etc/init.d/iptables start、/etc/init.d/ iptables stop /etc/xinetd.d/ ：这就是所谓的super daemon管理的各项服务的配置文件目录。/etc/X11/ ：与X Window有关的各种配置文件都在这里，尤其是xorg.conf或XF86Config这两个X Server的设定文件。 |
  | /home  | 这是系统预设的使用者家目录(home directory)。 在你新增一个一般使用者帐号时，预设的使用者家目录都会规范到这里来。比较重要的是，家目录有两种代号： ~ ：代表当前使用者的家目录，而 ~guest：则代表用户名为guest的家目录。 |
  | /lib   | 系统的库非常的多，而/lib放置的则是在开机时会用到的库，以及在/bin或/sbin底下的指令会呼叫的库而已 。 |
  | /media | media是媒体的英文，顾名思义，这个/media底下放置的就是可移除的装置。 包括软碟、光碟、DVD等等装置都暂时挂载于此。 常见的文件名有：/media/floppy, /media/cdrom等等。 |
  | /mnt   | 如果你想要暂时挂载某些额外的装置，一般建议妳可以放置到这个目录中。在古早时候，这个目录的用途与/media相同。 只是有了/media之后，这个目录就用来暂时挂载用了。 |
  | /opt   | 这个是给第三方软件放置的目录 。比如，KDE这个桌面管理系统是一个独立的计画，不过他可以安装到Linux系统中，因此KDE的软体就建议放置到此目录下了。 另外，如果你想要自行安装额外的软件(非原本的distribution提供的)，那么也能够将你的软件安装到这里来。 不过，以前的Linux系统中，我们还是习惯放置在/usr/local目录下。 |
  | /root  | 系统管理员(root)的家目录。 之所以放在这里，是因为如果进入单人维护模式而仅挂载根目录时，该目录就能够拥有root的家目录，所以我们会希望root的家目录与根目录放置在同一个分区中。 |
  | /sbin  | Linux有非常多指令是用来设定系统环境的，这些指令只有root才能够利用来设定系统，其他使用者最多只能用来查询而已。放在/sbin底下的为开机过程中所需要的，里面包括了开机、修复、还原系统所需要的指令。至于某些伺服器软体程式，一般则放置到/usr/sbin/当中。至于本机自行安装的软体所产生的系统执行档(system binary)，则放置到/usr/local/sbin/当中了。常见的指令包括：fdisk, fsck, ifconfig, init, mkfs等等。 |
  | /srv   | srv可以视为service的缩写，是一些网路服务启动之后，这些服务所需要取用的资料目录。 常见的服务例如WWW, FTP等等。 举例来说，WWW伺服器需要的网页资料就可以放置在/srv/www/里面。 |
  | /tmp   | 这是让一般使用者或者是正在执行的程序暂时放置文件的地方。这个目录是任何人都能够存取的，所以需要定期的清理一下。 FHS甚至建议在开机时，应该要将/tmp下的资料都删除。 |

  除了这些目录的内容之外，另外要注意的是，因为根目录与开机有关，开机过程中仅有根目录会被挂载， 其他分区则是在开机完成之后才会持续的进行挂载的行为。就是因为如此，因此根目录下与开机过程有关的目录， 就不能够与根目录放到不同的分区去。那哪些目录不可与根目录分开呢？有底下这些：

  /etc：配置文件

  /bin：重要执行档

  /dev：所需要的装置文件

  /lib：执行档所需的函式库与核心所需的模块

  /sbin：重要的系统执行文件

  这五个目录千万不可与根目录分开在不同的分区。

  

- /usr：

  依据FHS的基本定义，/usr里面放置的数据属于可分享的与不可变动的(shareable, static)。

  /usr不是user的缩写，其实usr是Unix Software Resource的缩写， 也就是Unix操作系统软件资源所放置的目录，而不是用户的数据。这点要注意。 FHS建议所有软件开发者，应该将他们的数据合理的分别放置到这个目录下的次目录，而不要自行建立该软件自己独立的目录。

  因为是所有系统默认的软件(distribution发布者提供的软件)都会放置到/usr底下，因此这个目录有点类似Windows 系统的C:Windows + C:Program files这两个目录的综合体，系统刚安装完毕时，这个目录会占用最多的硬盘容量。 一般来说，/usr的次目录建议有底下这些：

  | 目录          | 应放置文件内容                                               |
  | ------------- | ------------------------------------------------------------ |
  | /usr/X11R6/   | 为X Window System重要数据所放置的目录，之所以取名为X11R6是因为最后的X版本为第11版，且该版的第6次释出之意。 |
  | /usr/bin/     | 绝大部分的用户可使用指令都放在这里。请注意到他与/bin的不同之处。(是否与开机过程有关) |
  | /usr/include/ | c/c++等程序语言的档头(header)与包含档(include)放置处，当我们以tarball方式 (*.tar.gz 的方式安装软件)安装某些数据时，会使用到里头的许多包含档。 |
  | /usr/lib/     | 包含各应用软件的函式库、目标文件(object file)，以及不被一般使用者惯用的执行档或脚本(script)。 某些软件会提供一些特殊的指令来进行服务器的设定，这些指令也不会经常被系统管理员操作， 那就会被摆放到这个目录下啦。要注意的是，如果你使用的是X86_64的Linux系统， 那可能会有/usr/lib64/目录产生 |
  | /usr/local/   | 统管理员在本机自行安装自己下载的软件(非distribution默认提供者)，建议安装到此目录， 这样会比较便于管理。举例来说，你的distribution提供的软件较旧，你想安装较新的软件但又不想移除旧版， 此时你可以将新版软件安装于/usr/local/目录下，可与原先的旧版软件有分别啦。 你可以自行到/usr/local去看看，该目录下也是具有bin, etc, include, lib…的次目录 |
  | /usr/sbin/    | 非系统正常运作所需要的系统指令。最常见的就是某些网络服务器软件的服务指令(daemon) |
  | /usr/share/   | 放置共享文件的地方，在这个目录下放置的数据几乎是不分硬件架构均可读取的数据， 因为几乎都是文本文件嘛。在此目录下常见的还有这些次目录：/usr/share/man：联机帮助文件 /usr/share/doc：软件杂项的文件说明/usr/share/zoneinfo：与时区有关的时区文件 |
  | /usr/src/     | 一般原始码建议放置到这里，src有source的意思。至于核心原始码则建议放置到/usr/src/linux/目录下。 |

- /var：

  如果/usr是安装时会占用较大硬盘容量的目录，那么/var就是在系统运作后才会渐渐占用硬盘容量的目录。 因为/var目录主要针对常态性变动的文件，包括缓存(cache)、登录档(log file)以及某些软件运作所产生的文件， 包括程序文件(lock file, run file)，或者例如MySQL数据库的文件等等。常见的次目录有

  | 目录        | 应放置文件内容                                               |
  | ----------- | ------------------------------------------------------------ |
  | /var/cache/ | 应用程序本身运作过程中会产生的一些暂存档                     |
  | /var/lib/   | 程序本身执行的过程中，需要使用到的数据文件放置的目录。在此目录下各自的软件应该要有各自的目录。 举例来说，MySQL的数据库放置到/var/lib/mysql/而rpm的数据库则放到/var/lib/rpm去 |
  | /var/lock/  | 某些装置或者是文件资源一次只能被一个应用程序所使用，如果同时有两个程序使用该装置时， 就可能产生一些错误的状况，因此就得要将该装置上锁(lock)，以确保该装置只会给单一软件所使用。 举例来说，刻录机正在刻录一块光盘，你想一下，会不会有两个人同时在使用一个刻录机烧片？ 如果两个人同时刻录，那片子写入的是谁的数据？所以当第一个人在刻录时该刻录机就会被上锁， 第二个人就得要该装置被解除锁定(就是前一个人用完了)才能够继续使用 |
  | /var/log/   | 非常重要。这是登录文件放置的目录。里面比较重要的文件如/var/log/messages, /var/log/wtmp(记录登入者的信息)等。 |
  | /var/mail/  | 放置个人电子邮件信箱的目录，不过这个目录也被放置到/var/spool/mail/目录中，通常这两个目录是互为链接文件。 |
  | /var/run/   | 某些程序或者是服务启动后，会将他们的PID放置在这个目录下      |
  | /var/spool/ | 这个目录通常放置一些队列数据，所谓的“队列”就是排队等待其他程序使用的数据。 这些数据被使用后通常都会被删除。举例来说，系统收到新信会放置到/var/spool/mail/中， 但使用者收下该信件后该封信原则上就会被删除。信件如果暂时寄不出去会被放到/var/spool/mqueue/中， 等到被送出后就被删除。如果是工作排程数据(crontab)，就会被放置到/var/spool/cron/目录中。 |

  由于FHS仅是定义出最上层(/)及次层(/usr, /var)的目录内容应该要放置的文件或目录数据， 因此，在其他次目录层级内，就可以随开发者自行来配置了。