##### 1、Git的概念

###### 1.1、概念：

​		Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

###### 1.2、与SVN对比：

- Git是分布式，SVN是集中式管理

- Git把内容按元数据方式存储，而SVN是按文件。

  ​     元数据（Metadata）：<u>又称中介数据、中继数据，为描述数据的数据，主要描述数据属性的信息，用来支持如指示存储位置、历史数据、资源查找、文件记录等功能。</u>

- Git分支和SVN的分支不同

- Git没有一个全局的版本号，而SVN有。最大的区别

- Git的内容完整性要优于SVN，因为Git的内容存储算法是SHA-1哈希算法。确保代码内容的完整性。

    [SHA-1哈希算法](https://blog.csdn.net/u010536615/article/details/80080918) 、

##### 2、Git工作流程

        1. 克隆 Git 资源作为工作目录
        2. 在克隆的资源上添加或修改文件。
        3. 如果其他人修改了，你可以更新资源。
        4. 在提交前查看修改。
        5. 提交修改。
        6. 在修改完成后，如果发现错误，可以撤回并再次修改并提交。

​     ![Git工作流程](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

##### 3、Git工作区、暂存区和版本库

	- 工作区：在电脑里能看到的目录
	- 暂存区(stage |  index )：一般存放在.git目录下的index文件(.git/index)中，所以我们把暂存区有时也叫作索引(index)。
	- 版本库： 工作区有一个隐藏目录.git。这个不算工作区，而是Git的版本库。 

##### 4、Git创建仓库

###### 	4.1、git init

​		 **git init** 命令来初始化一个 Git 仓库，在执行完成 **git init** 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。

​		`git init  file`  初始化后，会在file目录下出现一个名为.git的目录，所有git需要的数据和资源都存放在这个目录中。

例：`git add *.c `   将目录下以.c结尾的文件提交到仓库中。

​		`git add README`   将目录下`README`文件提交到仓库中。 

​		`git commit -m ”提交说明“ `，提交到仓库中，在linux中用单引号，在windows中用双引

###### 	4.2 git clone

​		`git clone <repo>`	克隆仓库的命令   `repo`：Git仓库

​		`git clone <repo> <directory>`  克隆到指定的目录， `directory`：本地目录。

​		`git clone git://github.com/schacon/grit.git`   从网站上克隆Ruby 语言的 Git 代码仓库 Grit。执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。

​		`git clone git://github.com/schacon/grit.git mygrit` 自定义项目目录名称，在命令末尾指定新的名字即可，即重命名为`mygrit`。

###### 	4.3 配置

​		`git config --list`  显示当前的git配置信息

​		`git config -e`  编辑git配置文件，针对当前仓库

​		`git cinfig -e --global`  针对系统上所有的仓库。

​		设置提交代码时的用户信息(该步骤应在init后进行)：

​			`git config --global user.name "名字"`  在创建仓库后，这一步在这之后做，之后才能做add等操作。

​			`git config --global user.email xxx@xxx.com`   你的个人邮箱。

##### 5、Git基本操作

###### 5.1、6个基本命令

`git clone		git push		git add		git commit		git checkout		git pull`

 ![关系图](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

- workspace：工作区
- staging area：暂存区/缓冲区
- local repository：版本库或本地仓库
- remote repository：远程仓库

###### 5.2、创建仓库命令

`git init`：初始化仓库。直接输入即可，在执行完成 **git init** 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变

`git init  file`  初始化后，会在file目录下出现一个名为.git的目录，所有git需要的数据和资源都存放在这个目录中。

`git clone`：拷贝一份远程仓库，也就是下载一个项目，拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改。

`git clone [url]`，拷贝项目命令格式，`[url]`是要拷贝的项目链接。该项目名通常就是该 URL 最后一个 / 之后的项目名称。

`git clone [url] name`，对拷贝的项目重命名为name。

`git clone <repo>`	克隆仓库的命令   `repo`：Git仓库

`git clone <repo> <directory>`  克隆到指定的目录， `directory`：本地目录。

###### 5.3、提交与修改

Git的工作就是创建和保存你的项目的快照及与之后的快照进行对比。

###### 5.3.1 git add

`git add`，其作用是将文件添加到暂存区。

`git add [file1] [file2] ...`，添加一个或多个文件到暂存区。

`git add [dir]`，添加指定目录到暂存区，包括子目录。

`git add .`，添加当前目录下的所有文件到暂存区。

###### 5.3.2 git status

`git status`，该命令是用于查看在你上次提交之后是否有对文件进行再次修改。

`git status -s`，通过-s参数获得简短的输出结果

例：

``` git
$ git status -s
AM README
A  hello.php
```

文件的一些状态:

`??`：新添加的未跟踪文件。

`A`：新添加到暂存区中的文件前面有A标记。

`M`: 修改过的文件前面有M标记。

`M`：该M出现在左边，表示该文件被修改了并放入了暂存区。

`M`：该M出现在右边，表示该文件被修改了但是还没放入暂存区。

`MM`：该文件在工作区被修改并提交到暂存区后又在工作区中被修改

`AM`：文件添加到缓存之后又有改动。

###### 5.3.3 git diff

`git diff`命令：比较文件的不同，即比较文件在暂存区和工作区的差异。

`git diff`命令： 显示已写入暂存区和已被修改但尚未写入暂存区文件的区别。

`git diff`两个主要的应用场景：

- 尚未缓存的改动：`git diff`
- 查看已缓存的改动：`git diff --cached`
- 查看已缓存的与未缓存的所有改动：`git diff HEAD`
- 显示重要而非整个diff：`git diff --stat`

`git diff [file]`：显示file文件在暂存区和工作区的差异。

`git diff --cached [file] | git diff --staged [file]`：显示file文件暂存区和上一次提交的差异。

`git diff [first-branch]...[second-branch]`：显示两次提交之间的差异。

###### 5.3.4 git commit

在提交代码之前需要设置提交的用户信息，包括用户名和邮箱：

```git
git config --global user.name "用户名"
git config --global user.email xxx@xxx.com
去掉--global 参数只对当前仓库有效。 windows下是双引号。
```

`git commit`命令：将暂存区内容添加到本地仓库中。

`git commit -m [message]`：提交暂存区到本地仓库中，[message]="提交说明"，在linux中用单引号，在windows中用双引号。

`git commit [file1] [file2] ... -m [message]`：提交暂存区的指定文件到仓库区。

`git commit -a` ： -a参数设置修改文件后不需要执行git add命令，直接来提交。

例：

```git
修改了文件步骤*****
直接执行以下
git commit -am "修改xxx文件"
```

######  5.3.5 git reset

`git reset`命令：用于回退版本，可以指定退回某一次提交的版本。

`git reset [--soft | --mixed | --hard] [HEAD]`：语法格式

`git reset [HEAD]`：--mixed为默认，可以不用带参数，用于重置暂存区的文件与上一次的提交(commit)保存一致，工作区文件内容保持不变。

例：

```git
git reset HEAD^     #回退所有内容到上一个版本
git reset HEAD^ hello.php     #回退hello.php文件的版本到上一个版本
git reset 052e      #回退到指定版本
```

`git reset --soft HEAD`：--soft参数用于回退到某个版本

例：

```git
git reset --soft HEAD~3   #回退上上上一个版本
```

`git reset --hard HEAD`：--hard参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交。

例：

```git
git reset --hard HEAD~3    #回退上上上个版本
git reset --hard bae128    #回退到某个版本回退点之前的所有信息。
git reset --hard origin/master  #将本地的状态回退到和远程的一样
谨慎使用--hard参数，它会删除回退点之前的所有信息。
```

**HEAD参数说明**

- HEAD 表示当前版本
- HEAD^  上一个版本
- HEAD^^  上上一个版本
- HEAD^^^ 上上上一个版本     以此类推

也可以使用~数字表示

- HEAD~0 表示当前版本
- HEAD~1 上一个版本
- HEAD~2 上上一个版本        以此类推

`git reset HEAD`命令：用于取消已缓存的内容。

###### 5.3.6、git rm

`git rm`该命令用于删除文件。

`git rm <file>`：将文件从暂存区和工作区中删除。

例：

```git
git rm runoob.txt   #从暂存区和工作区中删除runoob.txt文件

如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f
git rm -f runoob.txt   #强行从暂存区和工作区中删除修改后的runoob.txt文件
```

`git rm --cached <file>`：将文件从暂存区域移除，但任然希望保留在当前工作目录中，即从跟踪清单中删除，使用`--cached`选项即可。

例：

```git
git rm --cached runoob.txt   #从暂存区中删除runoob.txt
```

可递归删除，如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件

`git rm -r *`：进入某个目录中，执行此语句，会删除该目录下的所有文件和子目录。

###### 5.3.7、git mv

`git mv`命令用于移动或重命名一个文件、目录或软连接

`git mv [file] [newfile]`

`git mv -f [file] [newfile]`：新文件名已经存在，但还是要重命名它，可以使用`-f`参数。

##### 6、提交日志

###### 6.1、git log

一般常用两个命令：

- `git log`  查看历史提交记录
- `git blame <file>` 以列表形式查看指定文件的历史修改记录 

`git log --oneline`：可以查看历史记录的简洁的版本。

`git log --graph`：--graph选项，查看历史中什么时候出现了分支、合并。

`git log --reverse --oneline`：`--reverse`参数来逆向显示所有日志。

`git log --author=name`：查找指定用户的提交日志。

###### 6.2、git blame

`git blame <file>`：如果要查看指定文件的修改记录。

##### 7、远程操作

###### 7.1、git remote命令

用于在远程仓库的操作，Git远程仓库(Github)

`Github`概念：是一个基于git的代码托管平台

`git remote add [shortname] [url]`：添加一个新的远程仓库，可以指定一个简单的名字，以便将来引用。

`git remote`：查看当前配置有哪些远程仓库。

`git remote -v`：执行时加上-v参数，可以看到每个别名的实际链接地址。

###### **提取远程仓库**：Git有两个命令用来提取远程仓库的更新。

`1、git fetch`：从远程仓库下载新分支与数据，该命令执行完后需要执行`git merge`远程分支到你所在的分支。

`2、git merge`：从远端仓库提取数据并尝试合并到当前分支。



`git fetch origin`：`origin` 为远程地址的别名。

`git fetch origin master`：从名为**origin**的远程上拉取名为**master**的分支到本地分支**origin/master**中，既然是拉取代码，当然需要同时指定远程名和分支名，室友分开写。

`git merge origin/master`：合并名为**origin/master**的分支到当前所在的分支，既然是分支的合并，当然就与远程名没有直接关系，所以没有出现远程名，需要指定的是被合并的分支。

**一次性拉取多个分支**：`git fetch master stable oldstable`

**一次性合并多个分支**：`git merge origin/master hotfix-2775 hotfix-2276 hotfix-2290`

###### **推送到远程仓库**

`git push origin master`：推送本地的**master**分支到远程**orgin**，涉及到远程以及分支，所以分开写。



`git remote rm [别名]`   : 删除远程仓库

`git remote rename old_name new_name` ： 修改仓库名。

