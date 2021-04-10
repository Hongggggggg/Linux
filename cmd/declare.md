- declare [-aAfFgilrtux] [-p] [name[=value] ...]
typeset [-aAfFgilrtux] [-p] [name[=value] ...]
- 功能：declare（别名 typeset）属 Shell 内建命令，用于申明 Shell 变量并设置变量属性，或查看已定义的 Shell 变量和函数。若不加上任何参数，只执行 declare/typeset 则会显示全部的 Shell 变量与函数（与执行 set 指令的效果相同）。
- 参数选项：
  - -a：申明数组变量
  - -A：申明关联数组，可以使用字符串作为数组索引
  - -f：仅显示已定义的函数
  - -F：不显示函数定义
  - -g：指定变量为全局变量，即使在函数内定义变量
  - -i：声明整型变量
  - -l：将变量值的大写字母变为小写
  - -r：设置只读属性
  - -t：设置变量跟踪属性，用于跟踪函数进行调试，对于变量没有特殊意义
  - -u：变量值的小写字母变为大写
  - -x：将指定的Shell变量换成环境变量
  - -p：显示变量定义的方式和值
  - +：取消变量属性，但是 +a 和 +r 无效，无法删除数组和只读属性，可以使用unset删除数组，但是 unset 不能删除只读变量

- 示例：

  - 定义关联数组并访问：

    ```bash
    declare -A assArray=([lucy]=beijing [yoona]=shanghai)
    
    #读取关联数组全部内容
    echo ${assArray[*]}
    #或
    echo ${assArray[@]}
    #输出
    beijing shanghai
    
    #读取指定索引的数组值
    echo ${assArray[lucy]}
    #输出：
    beijing
    
    #列出数组索引列表
    echo ${!assArray[*]}
    #或
    echo ${!assArray[@]}
    #输出
    yoona lucy
    ```

  - 定义只读变量：

    ```bash
    declare -r name1="lvlv1"
    #或
    typeset -r name2="lvlv2"
    #或
    readonly name3="lvlv3"
    ```

    Shell 规定，只读变量生命周期与当前 Shell 脚本进程相同，且不能消除只读属性和删除只读变量，除非 kill 当前 Shell 脚本进程。

  - 使用`-p`选项显示变量 name1 和 name2 的定义方式和当前值。

    ```bash
    declare -p name1 name2
    #输出
    declare -r name1="lvlv1"
    declare -r name2="lvlv2"
    ```

  - 使用`-x`选项将shell变量转换为临时环境变量，供当前Shell会话的其他shell进程使用，退出当前Shell会话则失效。

    ```bash
    declare -x name1;
    ```

  - 显示所有 Shell 环境变量。

    ```bash
    declare -x
    ```

  - 使用`+x`选项取消变量为环境变量。

    ```bash
    delcare +x name1
    ```

  - 申明整型变量，赋值浮点型数值将报错。

    ```bash
    declare -i integer=666
    ```

    

