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
3. 创建本地分支 git checkout -b dev   git pull origin master // 从master上拉，这样与master同步
4. 写代码
5. git add .  git commit -m "" git push origin dev
6. 建立追踪 git branch --set-upstream-to dev origin/dev
7. 每次提交之前下git pull

----
代码merge到master
1. 分支push后切换到主分支
2. git merge dev
3. git push

merge到master，master分支在dev之前


gitlab 发布
git push origin daily/0.0.1
提交到git lab 上，并发布日常到cdn 


git tag publish/0.0.1
git push origin publish/0.0.1
发布正式版本到cdn，并merge到master 

## 删除本地分支
git branch -d dev

## 删除远程分支
git push origin --delete dev



生成RSA密钥对 
ssh-keygen -t rsa -C "email" 全程回车，不输密码，push，pull就不用输密码
-t指定密钥类型，默认是rsa，可以省略。 
-C设置注释文字，比如邮箱。 

ssh 和 https的区别
1.clone项目:使用ssh方式时，首先你必须是该项目的管理者或拥有者，并且需要配置个人的ssh key。而对于使用https方式来讲，就没有这些要求。
2.push:在使用ssh方式时，是不需要验证用户名和密码，如果你在配置ssh key时设置了密码，则需要验证密码。而对于使用https方式来讲，每次push都需要验证用户名和密码。

配置ssh key
1.检查是否存在ssh key

$ ls ~/.ssh/id_rsa.pub
1
2
如果出现文件路径则存在

2.生成ssh key

$ ssh-keygen -t rsa -C "your@email.com"
1
连续3个回车。如果不需要密码的话。 
最后得到了两个文件：id_rsa和id_rsa.pub。 
如果你是第一次使用git，在此步骤前先设置自己的用户名和邮箱

$ git config --global user.name "yourname"
$ git config --global user.email "your@email.com"
1
2
3.添加密钥到github上 
打开你的id_rsa.pub文件，拷贝内容粘贴到github上的ssh设置里就可以了。

4.测试

$ ssh -T git@github.com