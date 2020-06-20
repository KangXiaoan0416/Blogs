---
title: Git 基础
date: 2018-03-26 15:29:29
tags: git
categories: Git
---
## This a note of studying git.
### What's git?
> When we begin to learn something, the most important thing
for us to know,I think , is what it is and what it can be used to do?
##### 当我们学习一个新的东西的时候,首先我们应该清楚它是什么，它能用来做什么？

### Git In My Eyes
1. #### git简介
首先，git必然先是一个版本控制工具，以前我接触过的版本控制工具只有svn,但是今天学习git的时候，了解了一下版本控制工具的发展历史，也了解到了git 和svn的不同.
2. #### git和svn之间的不同
#### svn
svn是一个集中化的版本控制，它将历史变更保存在服务器上，每次更新的时候都会从服务器前获取历史，所以，缺点显而易见：不能进行离线更新．如果中央服务器因为某些缘故宕机的话，那么所有属于这个项目的然都是无法进行更新的.而且所有的变更记录都保存在一个服务起上，意味着历史变更只有一份记录，当服务器因某些缘故导致记录丢失的话．那么影响将会是巨大的．
#### git
与svn 相比，git的优势显而易见．这源于git的机制，每当分机更新的时候，会把服务器仓库完整的镜像下来，这意味着，每个本地仓库的文件都相当于一个完整的备份记录．这无疑是极好的事情．
----
### How To Use GIt
>#### Git 的三种状态

* 已提交
* 已修改
* 已暂存

>#### 工作流程

1. 在工作目录中修改文件。
2. 暂存文件，将文件的快照放入暂存区域。
3. 提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录。

>#### 一. 基础操作

1. 克隆现有仓库，不同于其他的版本控制工具，git是将仓库玩完整的克隆下来．
```
$ git clone
```
2. 查看状态
```
$ git status
```
3.  添加文件到暂存区
```
$ git add
```
4. 提交文件变更
```
$ git commit
$ git commit -a                    
> 可以省去暂存的过程直接进行提交
$ git commit --amend   
> 重新提交，撤销上一次修改
```
5. 删除文件，从暂存去移除
```
$ git rm
```
6. 查看历史记录
```
$ git log
```
6. 文件改名和移动
```
$ git mv
```
类似linux操作指令
7. 查看远程仓库
```
$ git remote
```
-v
会显示需要读写远程仓库使用的 Git 保存的简写与其对应的 URL。
8. 拉取远程仓库中你没有的数据
```
$ git fetch
```
9. 推送到远程服务器分支
```
$ git push [remote] [branch]
```
remote  是本地设置的远程仓库的别名，branch就是要推送的分支
10. 远程仓库的移除和重命名
```
$ git remote rename [remote-name] [after-name]
> 远程仓库重命名
$ git remote rm [rmote-name]
> 移除某个远程仓库
```
11. 打标签
```
$ git tag
```
12. 别名
```
$ git config --global alias.unstage 'reset HEAD --'
```
