## Linux基础

## 1. The Shell

什么是 Shell ? Shell 本质上是一个程序，从键盘接收命令，然后发送给操作系统执行。

像一些图形用户界面的 “Terminal” 或 “Console" 这样的程序，它们实际上是用来启动一个 shell 的工具

接下来，我们将使用 **bash shell** （Bourne Again shell）

还有其它的 shell，但是我们不会涉及

### Shell 提示符

Shell 提示符（shell prompt）可能会有所不同，但通常会遵守以下格式：

```ruby
username@hostname:current_directory
```

例如：

![shell_prompt](D:\MarkdownBin\Linux\pic_1\shell_prompt.png)

请注意提示符最后的 `$`符号

不同的 shell 会使用不同的提示符，但以 bash shell 为例，普通用户的提示符号通常是`$`

在你输入命令的时候，不需要输入这个符号，它只是用于标识提示符的而已

### 第一条命令：echo

`echo`  回声，顾名思义，**原样显示（回声在）**终端上

![echo](D:\MarkdownBin\Linux\pic_1\echo.png)

同样地，我们可以试试`date`（日期，显示当前的日期和时间），和`whoami`（我是谁，显示当前用户名），看看会输出什么？

![date_whoami](D:\MarkdownBin\Linux\pic_1\date_whoami.png)

## 2. pwd(Print Working Directory)

 在 Linux 中，**一切皆文件**

所有的文件都被组织在一个**分层的目录树（hierarchical directory tree）中，这个目录的结构的起点叫做根目录（root directory）**，用一个斜杠 `/` 来表示

根目录下面可以包含很多的文件夹和文件，而每个文件夹里又可以继续包含更多的文件夹和文件，就像一颗倒挂的树

```lua
/
|-- bin
|   |-- file1
|   |-- file2
|-- etc
|   |-- file3
|   `-- directory1
|       |-- file4
|       `-- file5
|-- home
|-- var

```

这个结构的意思是：

- `/` 是根目录
- `/bin` 的目录下有 `file1` 和 `file2`
-  `/etc` 下有 `file3` 和一个子目录 `directory1`，这个子目录中还有 `file4` 和 `file5`
- `/home`、`/var` 也是根目录下的文件夹

其中，这些文件和目录的名字称之为**路径**

例如，如果你有一个名为 `home` 的文件夹，里面有一个子文件夹叫做 `pete`，而在 `pete` 里面又有一个子文件夹叫做 `Movies`，那么这个路径会长这样：

```ruby
/home/pete/Movies
```

如果我们希望在文件系统中来去自如，我们首先就需要知道**当前所在的目录位置**，可以使用 `pwd` 命令

例如：

![pwd](D:\MarkdownBin\Linux\pic_1\pwd.png)