## Linux基础

## 1. The Shell

什么是 Shell ? Shell 本质上是一个程序，从键盘接收命令，然后发送给操作系统执行。

像一些图形用户界面的 “Terminal” 或 “Console" 这样的程序，它们实际上是用来启动一个 shell 的工具

接下来，我们将使用 **bash shell** （Bourne Again shell）

还有其它的 shell，但是我们不会涉及

**Shell 提示符**

Shell 提示符（shell prompt）可能会有所不同，但通常会遵守以下格式：

```ruby
username@hostname:current_directory
```

例如：

![shell_prompt](..\pic\pic_1\shell_prompt.png)

请注意提示符最后的 `$`符号

不同的 shell 会使用不同的提示符，但以 bash shell 为例，普通用户的提示符号通常是`$`

在你输入命令的时候，不需要输入这个符号，它只是用于标识提示符的而已

**第一条命令：echo**

`echo`  回声，顾名思义，**原样显示（回声在）**终端上

![echo](..\pic\pic_1\echo.png)

同样地，我们可以试试`date`（日期，显示当前的日期和时间），和`whoami`（我是谁，显示当前用户名），看看会输出什么？

![date_whoami](..\pic\pic_1\date_whoami.png)

## 2. pwd (Print Working Directory)

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

例如，如果你有一个名为 `home` 的文件夹，里面有一个子文件夹叫做 `elo`，而在 `elo` 里面又有一个子文件夹叫做 `Movies`，那么这个路径会长这样：

```bash
/home/elo/Movies
```

如果我们希望在文件系统中来去自如，我们首先就需要知道**当前所在的目录位置**，可以使用 `pwd` 命令

例如：

![pwd](..\pic_1\pwd.png)

## 3. cd (Change Directory)

现在你已经知道“我在哪了”，现在我们试试看如何在**文件系统中“走动”**

记住，我们在文件系统的“导航”是通过“路径”来实现的。而路径有两种方式：

**1. 绝对路径（Absolute Path）**

- 从**根目录开始**写出的完整路径
- 根目录就像树的根，所有路径都从这里开始
- 只要路径以 `/` 开头，那就是绝对路径

例如：

```bash
$ cd /home/elo/Desktop
```

意思是：进入根目录 `/` → 然后进入 `home` → 然后进入 `elo` → 然后进入 `Desktop`



**2. 相对路径（Relative Path）**

- 这是**相对于你当前所在目录**来写的路径
- 不需要从 `/` 开始，而是从当前位置出发

如果你已经在：

```bash
/home/elo/Documents
```

你想进入这个目录里的子目录叫做 `taxes`，你不需要写完整路径 `/home/elo/Documents/taxes`，你只要写：

```bash
$ cd taxes
```



对于以上两种路径，例如，为了到达 `/home/elo/test/a/b` 这个文件夹内，如果我们想使用绝对路径：

![absolute_path](..\pic\pic_1\absolute_path.png)

假设我们已经在 `/home/elo/test/a`，那么直接使用如下命令：

![relative_path](..\pic\pic_1\relative_path.png)



不过，总是使用相对路径和绝对路径也是很累的，仍然有些快捷路径可以帮助我们导航：

-  `.`：当前目录
-  `..`：上一级目录
-  `~`：用户主目录
-  `-`：上次访问过的目录

```bash
$ cd .  # 留在当前目录
$ cd ..	# 回到上一级目录
$ cd ~  # 回到主目录(比如/home/elo)
$ cd -  # 回到一个你刚才去过的目录
```

![shortcut](..\pic\pic_1\shortcut.png)

## 4. ls(List Directory)

现在我们已经在知道如何再文件系统中移动了，可是，**我们如何知道当前目录下有哪些东西呢？**

我们可以使用一个很有用的命令： `ls` 

默认情况下，它会列出**当前目录**下的目录和文件夹

```bash
$ ls
```

如果想查看**某个特定目录**里的内容，也可以在后面加上路径：

```bash
$ ls /home/elo
```

**命令参数（Command Options / Flags）**

在 Linux 中，很多命令可以通过添加**参数（也叫选项、flag)**来扩展或改变行为，例如：

```bash
$ ls -l
```

这些字母告诉命令要”怎么做“，或者”做的更详细“

例如刚刚的示例命令，`l` 代表  **long format（长格式）**，它会显示每个文件的详细信息

包括权限、链接数、拥有者，用户组，大小，时间戳，文件名

另外，在 linux 中，不是所有文件都是默认可见的，**以 `.` 开头的文件都是”隐藏文件“**

如果希望查看隐藏文件，可以使用 `-a`（a 代表 all）

![ls_1](..\pic\pic_1\ls.png)