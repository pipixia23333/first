## 基本命令

mkdir #文件名    //创建文件

cd #文件名

pwd //显示当前目录

git init //把这个目录变成git可以管理的仓库



git可以跟踪文本文件的改动

word文件是二进制格式



git commit -m " "  // 提交文件-m 后面写说明

git add #文件名



### 获取信息

git status //获取工作区状态

git diff //获取修改内容

git log //获取历史记录

q退出



git log --pretty=oneline//按行输出



git reset --hard HEAD^  //^个数表示后退版本个数 

100个版本  HEAD~100

git reset --hard 版本号 //退回指定版本（包括曾经退掉的版本

git reflog 用来记录每一次的命令命令日志



### 撤销修改

git restore -- #文件名 //丢弃工作区的修改，

有暂存区先回退到暂存区

无暂存区撤回到版本库

> `git checkout -- file`命令中的`--`很重要，没有`--`，就变成了“切换到另一个分支”的命令



git restore --staged #文件名 //将暂存区文件放回工作区



### 删除文件

rm #文件名

git rm #filename // delete file while staged



git checkout -- #文件名 //从版本库里恢复删除的文件

git restore #文件名



## 原理

git add 添加到暂存区

git commit 把暂存区的所有东西提交到当前分支

![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)



Git 跟踪并管理的是修改而非文件

commit 提交的是暂存区里的修改内容而非工作区的



## 远程库

### 推送远程库

SSH key : GitHub 用于识别推送是自己提交的

绑定

```git
git remote add origin git@github.com:michaelliao/learngit.git
```

```git
$ git push -u origin master
```

推送到远程库上

### 删除远程库

```git
$ git remote -v
```

查看远程库信息

```
$ git remote rm origin
```

此处的删除时解除了本地和远程的绑定关系

删除origin

要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；

关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；

关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

### 克隆仓库

git clone #GitHub的地址

ssh协议最快

## 分支管理

每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即`master`分支。`HEAD`严格来说不是指向提交，而是指向`master`，`master`才是指向提交的，所以，`HEAD`指向的就是当前分支。

创建一个新的分支dev，HEAD改下指向，新的提交里dev继续前进

![git-br-dev-fd](E:\OneDrive - mail.sdu.edu.cn\md\image\l.png)

假如我们在`dev`上的工作完成了，就可以把`dev`合并到`master`上。Git怎么合并呢？最简单的方法，就是直接把`master`指向`dev`的当前提交，就完成了合并：

![git-br-ff-merge](E:\OneDrive - mail.sdu.edu.cn\md\image\0.png)

首先，我们创建`dev`分支，然后切换到`dev`分支：

```
$ git checkout -b dev
Switched to a new branch 'dev'
```

`git checkout`命令加上`-b`参数表示创建并切换，相当于以下两条命令：

```
$ git branch dev
$ git checkout dev
Switched to branch 'dev'
```

然后，用`git branch`命令查看当前分支：

```
$ git branch
* dev
  master
```

```
$ git merge dev
```

合并到当前分支

Fast-forward 直接更改指针指向

```
$ git branch -d dev
```

创建并切换到新的`dev`分支，可以使用：

```
$ git switch -c dev
```

直接切换到已有的`master`分支，可以使用：

```
$ git switch master
```

### 总结

Git鼓励大量使用分支：

查看分支：`git branch`

创建分支：`git branch <name>`

切换分支：`git checkout <name>`或者`git switch <name>`

创建+切换分支：`git checkout -b <name>`或者`git switch -c <name>`

合并某分支到当前分支：`git merge <name>`

删除分支：`git branch -d <name>`

### BUG分支

`stash`功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作

`cherry-pick <commit>`命令，能复制一个特定的提交到当前分支

一是用`git stash apply`恢复，但是恢复后，stash内容并不删除，你需要用`git stash drop`来删除；

另一种方式是用`git stash pop`，恢复的同时把stash内容也删
