- realpath [OPTIONS] FILES

- 功能：realpath 用于获取指定目录或文件的绝对路径。

  编写 Shell 脚本中，通常会使用相对路径来指明文件，但有时候，我们需要用到绝对路径，此时可以使用 realpath 来获取。

- 参数：

  - -e, --canonicalize-existing
     文件 FILE 的所有组成部件必须都存在
  - -m, --canonicalize-missing
     文件 FILE 的组成部件可以不存在
  - -L, --logical
     在软链接之前解析父目录 ..
  - -P, --physical
     解析软链接，默认动作
  - -q, --quiet
     静默模式输出，禁止显示大多数错误消息
  - --relative-to=DIR
     相对于目录 DIR 的路径
  - --relative-base=DIR
     如果文件在基目录 DIR下，打印结果会省去基目录，否则打印绝对路径
  - -s, --strip, --no-symlinks
     不扩展软链接
  - -z, --zero
     不分隔输出，即所有的输出均在一行而不是单独每行

- 示例：

  - 打印指定文件的绝对路径。软连接也可以

    ```bash
    realpath ./test.sh
    ```

  - 打印某个文件相对于另外一个目录的路径

    ```bash
    realpath --relative-to=./src ./foo
    ```

  - 打印某个文件相对于基目录的路径，如果文件在基目录下，则会省去基目录。

    ```bash
    realpath --relative-base=/data/test ./foo
    ```

    