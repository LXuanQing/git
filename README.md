## git的使用方法

 ![git命令](http://www.ruanyifeng.com/blogimg/asset/2014/bg2014061202.jpg)

    分为工作区、暂存区、本地仓库、远程仓库

## git checkout -- <file name>
`
    撤销工作区的修改，回到最后一次add或commit的状态
`
## git add .
`
    添加到暂存区
`
## git reset HEAD <filr name>
`
    暂存区的修改撤销掉，重新放回工作区
`
## git commit -m "描述"
`
    添加到本地仓库
`
## git checkout -- <file name>
`
    让这个文件回到最近一次git commit或git add时的状态。
`
## git reset --hard 424242fef
`
    版本回退
`
## git log --pretty=oneline
`
    查看提交日志
`
----

* git clone的时候，所有本地分支默认与远程主机的同名分支，建立追踪关系，也就是说，本地的master分支自动”追踪”origin/master分支。
* 随后建立的分支即使push后，也无法和远程分支建立追踪关系，提交和拉取需要带上远程分支名
`
    git push origin dev
    git pull origin dev
`
---
* 手动建立追踪关系
`  // git branch --set-upstream-to dev origin/dev
`
这样可以直接使用`git push`和`git pull`

# 工作中，git使用流程

1. 创建远程git仓库
2. 克隆代码
3. 创建本地分支 git checkout -b dev
4. 写代码
5. git add .  git commit -m "" git push origin dev
6. 建立追踪 git branch --set-upstream-to dev origin/dev
7. 每次提交之前下git pull

----
代码merge到master
1. 分支push后切换到主分支
2. git merge dev
3. git push








