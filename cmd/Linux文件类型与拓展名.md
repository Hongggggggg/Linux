- 文件类型：

  - 普通文件：

    ​	用ls -lh来查看某些文件的属性时，可以看到有类似-rwxrwxrwx的属性，其中第一个符号是 - ，这样的文件在Linux中就属于普通文件。依照文件内容，大致又可分为：

    - 纯文本文件（ASCII）：

      ​	这是Linux系统中最多的一种文件类型，称为纯文本文件时因为内容是我们可以直接读到的数据，如数字、字母等。如 cat ~/.bashrc

    - 二进制文件（binary）：

      ​	Linux其实只认识二进制文件，Linux当中的可执行文件就是这种格式的文件。比如说cat命令就是一个binary file。

    - 数据格式文件（data）：

      ​	有些程序在运行的过程中会读取某些特定格式的文件，那些特定格式的文件可以被称为数据文件（data file）。举例来说，Linux在使用者登录时，都会将登录的数据记录在/var/log/wtmp的文件内，该文件就是一个data file，可以通过last指令读取出来，但使用cat 时，就会读出乱码。

  - 目录文件：

    ​	执行ls -lh时，会看到类似 drwxrwxrwx的属性，以d开头的文件就是目录

  - 字符设备或块设备文件：

    ​	进入/dev目录，ls -al 可以看到某些属性为crw-rw-rw-，第一个字符为c，这表示这个文件为字符设备文件，如串口设备等，若是第一个字符为 b，则表示为块设备，比如硬盘、光驱等设备。

  - 符号链接文件：

    文件属性的第一个字符是 l 的文件就是链接文件

  - 数据接口文件(sockets):

    ​	 数据接口文件，这种类型的文件通常呗用在网络上的数据承接。我们启动一个程序来监听客户端的要求，而客户端就可以通过这个socket来进行数据的沟通。它的第一个属性为s，最常在/var/run这个目录中看到这种文件类型。

    ​	例如：当启动MySQL服务器时，会产生一个mysql.sock的文件，文件属性的第一个字符就是s。

  - 数据传送文件（FIFO，pipe）：

    ​	FIFO也是一种特殊的文件类型，他主要的目的在解决多个程序同时存取一个文件所造成的错误问题，第一个属性为p



- 文件拓展名：	

  ​	基本上，Linux的文件是没有所谓的扩展名的，一个Linux文件能不能被执行，与他的第一栏的十个属性有关， 与档名根本一点关系也没有。这个观念跟Windows的情况不相同喔！在Windows底下， 能被执行的文件扩展名通常是 .com .exe .bat等等，而在Linux底下，只要你的权限当中具有x的话，例如[ -rwx-r-xr-x ] 即代表这个文件可以被执行。

  ​	不过，可以被执行跟可以执行成功是不一样的，举例来说，在root家目录下的install.log 是一个纯文本档，如果经由修改权限成为 -rwxrwxrwx 后，这个文件能够真的执行成功吗？ 当然不行，因为他的内容根本就没有可以执行的数据。所以说，这个x代表这个文件具有可执行的能力， 但是能不能执行成功，当然就得要看该文件的内容.

  ​	虽然如此，不过我们仍然希望可以藉由扩展名来了解该文件是什么东西，所以，通常我们还是会以适当的扩展名来表示该文件是什么种类的。底下有数种常用的扩展名：

  ​	*.sh ： 脚本或批处理文件 (scripts)，因为批处理文件为使用shell写成的，所以扩展名就编成 .sh 

  ​	*Z, *.tar, *.tar.gz, *.zip, *.tgz： 经过打包的压缩文件。这是因为压缩软件分别为 gunzip, tar 等等的，由于不同的压缩软件，而取其相关的扩展名！

  ​	*.html, *.php：网页相关文件，分别代表 HTML 语法与 PHP 语法的网页文件。 .html 的文件可使用网页浏览器来直接开启，至于 .php 的文件， 则可以透过 client 端的浏览器来 server 端浏览，以得到运算后的网页结果。

  ​	基本上，Linux系统上的文件名真的只是让你了解该文件可能的用途而已，真正的执行与否仍然需要权限的规范才行。例如虽然有一个文件为可执行文件，如常见的/bin/ls这个显示文件属性的指令，不过，如果这个文件的权限被修改成无法执行时，那么ls就变成不能执行。

  ​	上述的这种问题最常发生在文件传送的过程中。例如你在网络上下载一个可执行文件，但是偏偏在你的 Linux系统中就是无法执行，那么就是可能文件的属性被改变了。不要怀疑，从网络上传送到你的 Linux系统中，文件的属性与权限确实是会被改变的。


​    

​    

​    

