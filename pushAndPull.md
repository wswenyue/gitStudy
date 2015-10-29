# push

```bash 
# push所有分支
$ git push       
     
# 将本地主分支推到远程主分支             
$ git push origin master 
 
# 将本地主分支推到远程(如无远程主分支则创建，用于初始化远程仓库)       
$ git push -u origin master  

# 创建远程分支， origin是远程仓库名       
$ git push origin <local_branch> 
 
# 创建远程分支
$ git push origin <local_branch>:<remote_branch> 
 
# 先删除本地分支(git br -d <branch>)，然后再push删除远程分支
git push origin :<remote_branch> 
```

##拉取远程仓库分支
```bash
# 拉取远程仓库到本地tmp分支
$ git fetch origin master:tmp

# 查看是否有更改，如果有，考虑要不要合并
$ git diff tmp 

# 合并分支到本地
$ git merge tmp
-----------------
$ git pull  #相当于是从远程获取最新版本并merge到本地

$ git pull origin master # 这一条是上面三条的功能

# 建议使用上面三条，因为你不确定远程仓库的就是最好的版本
```

##git仓库的代码版本高于本地仓库时，不允许提交覆盖的问题解决

git仓库中已经有一部分代码，所以它不允许你直接把你的代码覆盖上去。于是你有2个选择方式：

>#### 1，强推，即利用强覆盖方式用你本地的代码替代git仓库内的内容

```bash
$ git push -f
```
>#### 2，先把git的东西fetch到你本地然后merge后再push
```bash
$ git fetch
$ git merge

# 这2句命令等价于
$ git pull  
```

示例：

```bash
# 取回origin主机的next分支，与本地的master分支合并，需要写成下面这样
$ git pull origin next:master
# 如果远程分支是与当前分支合并，则冒号后面的部分可以省略。
$ git pull origin next
# 上面命令表示，取回origin/next分支，再与当前分支合并。实质上，这等同于先做git fetch，再做git merge。
$ git fetch origin
$ git merge origin/next
```

##push的其他知识

```bash
# 如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push。
$ git push -u origin master
# 上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。
# 不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。如果要修改这个设置，可以采用git config命令。

$ git config --global push.default matching
# 或者
$ git config --global push.default simple
# 还有一种情况，就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要使用--all选项。

$ git push --all origin
# 上面命令表示，将所有本地分支都推送到origin主机。
# 如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做git pull合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用--force选项。

$ git push --force origin 
# 上面命令使用--force选项，结果导致远程主机上更新的版本被覆盖。除非你很确定要这样做，否则应该尽量避免使用--force选项。
# 最后，git push不会推送标签（tag），除非使用--tags选项。

$ git push origin --tags
```

