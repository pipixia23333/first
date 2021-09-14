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

SSH key : GitHub 用于识别推送是自己提交的



