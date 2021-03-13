- paste [OPTION]... [FILE]...

- 功能：将多个问价你的相应行默认以Tab分隔符横向连接起来，输出到标注输出

- 参数：

  - -d，用指定的分隔符取代Tab
  - -s，顺序地合并一个文件的所有行到一行

- 示例：

  - 将一个文件的所有行合并到一行，以Tab分隔

    ```bash
    paste -s test.txt
    ```

  - 将N个文件合并成N行（各自合并成一行）

    ```bash
    paste -s test1.txt test2.txt
    ```

  - 横向连接两个文件，默认以Tab分隔：

    ```bash
    paste test1.txt test2.txt
    ```

    

