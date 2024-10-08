## 什么是 Shebang?

简单来说，就是你在脚本开头看到的这个：

```sh
#!/usr/bin/bash
```

Shebang（也称为 hash-bang、pound-bang 或者 bang）是一个作为脚本文件中的第一行的特殊注释，它告诉系统用哪个解释器来执行脚本。Shebang 后面直接跟着解释器的绝对路径。

在上面的例子中，Shebang 指示系统使用 `/usr/bin/bash` 作为脚本的解释器。当我们使用如下的命令运行脚本时：

```sh
./script.sh
```

系统就会自动使用 `/usr/bin/bash` 作为解释器来运行该脚本，即使我们在命令中并没有指定解释器。其作用相当于：

```sh
/usr/bin/bash script.sh
```

然而，如果系统中没有 `/usr/bin/bash` 这个程序，那么在执行上面的命令时就会出现报错：

```
zsh: ./script.sh: bad interpreter: /usr/bin/bash: no such file or directory
```

实际上，即便系统中的某个地方安装有 `bash` 程序，但因为我们指定的解释器是 `/usr/bin/bash`，所以只要 `bash` 没有安装在 `/usr/bin` 目录下，那么执行脚本的命令 `./script.sh` 就会报错。

最佳实践是通过 `env` 程序来寻找解释器：

```sh
#!/usr/bin/env bash
```

一般来说，每个 *nix 系统在 `/usr/bin` 目录下都有 `env` 程序。`env` 程序的作用是在系统环境变量 PATH 下寻找我们需要的程序，在这个例子中是 `bash`。也就是说，通过 `#!/usr/bin/env xxx` 的形式，我们允许需要的程序安装在系统的不同位置，这样就提升了我们脚本的兼容性。它允许了解释器安装在非标准位置的用户也能通过 `./script.sh` 命令运行我们的脚本，或者某些希望使用非系统版本解释器的用户能够继续使用自定义的解释器来执行我们的脚本（前提是他在系统环境变量 PATH 的前面指定了自定义解释器的路径）。

## 误区

注意，以下写法是不建议的：

```py
#!.venv/bin/python
```

你可能误以为这里给出的相对路径 `.venv/bin/python` 是相对于脚本文件的，但实际上不是。Shebang 中的路径是相对于当前工作目录的，而不是相对于脚本文件的。所以，如果你在执行脚本时不在脚本文件所在的目录下，那么这种写法就会出错。

正确的写法是在 Shebang 中使用绝对路径。

## Shebang 的历史

Shebang 的历史可以追溯到 1971 年的 UNIX 第七版。在那个时候，Shebang 的格式是 `#!` 后面直接跟着解释器的名称，而不是路径。这种写法的问题在于，解释器的名称可能会因系统而异，所以这种写法的兼容性很差。直到 1980 年代，Shebang 才被修改为现在的格式。