# git命令

## git clone

这个命令就是把远程的代码克隆到本地下来

## git branch -vv

查看本地对应远程的分支对应关系

## git branch -a 

查看本地和远程所有分支

## git status

这个命令适用于查看哪些代码改变了

## 第一次提交代码

### git init

这个命令是初始化git仓库

### git add .

这个命令是把所变动的文件添加到暂存区

### git commit -m '描述'

这个命令是将暂存区的文件变动提交到本地

### git remote add origin 远程仓库url

这个命令是是将本地仓库与远程仓库进行关联

- `git remote add`: 这部分表示使用 Git 命令来添加一个远程仓库。
- `origin`: 这是给远程仓库起的一个名称，通常习惯上将远程仓库的主要地址命名为 `origin`，但你也可以使用其他名称。
- `远程仓库url`: 这是指远程仓库的 URL 地址，可以是 HTTPS 或 SSH 协议的 URL。

### git push -u origin master

这个命令是将本地仓库推送到远程仓库的master分支，并且将本地分支与远程对应分支

### git push origin 仓库名

这个命令是把本地代码提交到远程仓库
