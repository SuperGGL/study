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

​		git init  file  初始化后，会在file目录下出现一个名为.git的目录，所有git需要的数据和资源都存放在这个目录中。

例：git add *.c    将目录下以.c结尾的文件提交到仓库中。

​		git add README   将目录下README文件提交到仓库中。 

​		git commit -m ”提交说明“ ，提交到仓库中，在linux中用单引号，在windows中用双引号。

    ###### 	4.2、git clone

​		git clone \<repo\>	克隆仓库的命令   repo：Git仓库

​		git clone \<repo\> \<directory\>  克隆到指定的目录， directory：本地目录。

​		git clone git://github.com/schacon/grit.git   从网站上克隆Ruby 语言的 Git 代码仓库 Grit。执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。

​		git clone git://github.com/schacon/grit.git mygrit 自定义项目目录名称，在命令末尾指定新的名字即可。

###### 	4.3 配置

​		git config --list  显示当前的git配置信息

​		git config -e  编辑git配置文件，针对当前仓库

​		git cinfig -e --global  针对系统上所有的仓库。

​		