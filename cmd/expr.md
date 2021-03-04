- expr EXPRESSION

  expr OPTION

- 功能：计算表达式的值。支持关系运算、算数运算、字符串匹配、截取获取长度等相关运算，只支持整数

- 示例：

  - 整数的算数运算

    ```bash
    expr 1 + 1
    expr 1 - 1
    expr 1 * 1
    expr 1 / 2
    expr 1 % 2
    ```

  - 整数的关系运算

    ```bash
    expr 1 \< 1 #<需要转义
    expr 1 \<= 1
    expr 1 \> 1
    expr 1 \>= 1
    expr 1 = 1
    expr 1 != 1
    ```

  - 字符串关系运算

    ```bash
    expr "abc" \< "acb"
    ```

  - 截取字符串

    ```bash
    expr substr "abcd" 1 3
    ```

  - 获取字符串长度

    ```
    expr length "abcd"
    ```

    

