- readelf \<option> <elffile...>

- 功能：readelf 用于读取 ELF（Executable and Linkable Format）格式文件的详细信息，包括目标文件、可执行文件、共享目标文件与核心转储文件。

  - ELF文件分类：

    - 可重定位文件（Relocatable File），这类文件包含了代码和数据，用于链接生成可以执行文件或共享目标文件，目标文件和静态链接库均属于可重定位文件，例如`*.o`或`lib*.a`文件；
    - 可执行文件（Executable File），用于生成进程映像，载入内存执行。Linux 环境下的 ELF 可执行文件一般没有扩展名，例如用户命令 ls；
    - 共享目标文件（Shared Object File），这种文件包含了代码和数据，用于和可重定位文件或其他共享目标文件一起生成可执行文件。例如 Linux 的动态共享对象（Dynamic Shared Object），C 语言运行时库 glibc-2.5.so；
    - 核心转储文件（Core Dump File），当进程意外终止时，系统可以将该进程的地址空间的内容及终止时的一些其他信息转储到核心转储文件。例如 Linux 下的 core dump。

  - ELF文件组成：

    ELF 文件头描述了 ELF 文件的总体信息，包括系统相关、类型相关、加载相关和链接相关的信息。

    - 系统相关，比如ELF 文件标识的魔数，以及硬件和平台等相关信息，增加了 ELF 文件的移植性，使交叉编译成为可能；
    - 类型相关，比如 ELF 文件类型，分别有目标文件、可执行文件、动态链接库与核心转储文件；
    - 加载相关，比如程序头，描述了 ELF 文件被加载时的段信息；
    - 链接相关，比如节头，描述了 ELF 文件的节信息。

- 选项：

  - -a,--all：显示全部信息，等价于 -h -l -S -s -r -d -V -A -I
  - -h,--file-header：显示文件头信息
  - -l,--program-headers,--segments：显示程序头（如果有的话）
  - -S,--section-headers,--sections：显示节头信息（如果有的话）
  - -g,--section-groups：显示节组信息（如果有的话）
  - -t,--section-details：显示节的详细信息（-S的）
  - -s,--syms,--symbols：显示符号表节中的项（如果有的话）
  - --dyn-syms：显示动态符号表节中的项（如果有的话）
  - -e,--headers：显示全部头信息，等价于-h -l -S
  - -n,--notes：显示note段（内核注释）的信息
  - -r,--relocs：显示可重定位段的信息。 
  - -u,--unwind：显示unwind段信息。当前只支持IA64 ELF的unwind段信息。 
  - -d,--dynamic：显示动态段的信息
  - -V,--version-info：显示版本段的信息
  - -A ,--arch-specific：显示CPU构架信息
  - -D,--use-dynamic：使用动态符号表显示符号，而不是符号表
  - -x <number or name>,--hex-dump=<number or name>：以16进制方式显示指定节内容。number指定节表中节的索引，或字符串指定文件中的节名
  - -R <number or name>,--relocated-dump=<number or name>：以16进制方显示指定节内容。number指定节表中节的索引，或字符串指定文件中的节名。节内容被展示前将被重定位。
  - -p <number or name>,--string-dump=<number or name>：以可打印的字符串显示指定节内容。number指定节表中节的索引，或字符串指定文件中的节名。
  - -c,--archive-index：展示档案头中的文件符号索引信息，执行与 ar 的 t 命令相同的功能，但不使用 BFD 库
  - -w[liaprmfFsoR],--debug-dump[=line,=info,=abbrev,=pubnames,=aranges,=macro,=frames,=frames-interp,=str,=loc,=Ranges]：显示调试段中指定的内容
  - --dwarf-depth=n：将“.debug_info”节的转储限制为n个子级。这只对--debug dump=info有用。默认为打印所有DIE（debugging information entry）；n的特殊值0也将具有此效果
  - --dwarf-start=n：只打印以编号为n的模具开始的DIE，仅适用于使用--debug dump=info选项时。该选项可以与--dwarf-depth=n连用。
  - -I,--histogram：显示符号的时候，显示 bucket list 长度的柱状图
  - -v,--version：显示 readelf 的版本信息
  - -H,--help：显示 readelf 所支持的命令行选项
  - -W,--wide：宽行输出
  - @file：可以将选项集中到一个文件中，然后使用这个 @file 选项载入

- 示例：

  - 读取可执行文件形式的ELF文件头信息

    ```bash
    readelf -h main.out 
    ```

  - 读取目标文件形式的 ELF 文件头信息。

    ```bash
    readelf -h print.o
    ```

  - 读取静态库文件形式的 ELF 文件头信息

    ```bash
    readelf -h libprint.a
    ```

  - 读取动态库文件形式的 ELF 文件头信息。

    ```
    readelf -h libprint.so 
    ```

  - 查看可执行的 ELF 文件程序头信息。

    ```
    readelf -l main.out
    ```

    