# remote 相关

##基本指令
```bash
#列出已经存在的远程分支
$ git remote 

# 查看远程服务器地址和仓库名称 列出详细信息
$ git remote -v | --verbose

# 查看远程服务器仓库状态
$ git remote show origin            
# 添加远程仓库地址
$ git remote add origin git@github:wswenyue/demo.git       
#修改远程地址
$ git remote set-url origin git@github.com:wswenyue/demo 

# 删除远程创库地址
$ git remote rm 

```

##示例

- 查看远程仓库分支与本地分支的一些信息

```shell
$ git remote show origin

* remote origin
  Fetch URL: git@github.com:XXXX/xxx.git
  Push  URL: git@github.com:XXXX/xxx.git
  HEAD branch: master
  Remote branches:
    dev      tracked
    dev-elan tracked
    dev-time tracked
    dev-ui   tracked
    master   tracked
  Local refs configured for 'git push':
    dev      pushes to dev      (up to date)
    dev-elan pushes to dev-elan (fast-forwardable)
    dev-time pushes to dev-time (up to date)
    dev-ui   pushes to dev-ui   (local out of date)
    master   pushes to master   (up to date)

```

> ####从上面的信息我们可以知道：
- 远程仓库fetch、push 的url信息
- 远程仓库追踪的分支（dev、dev-elan、dev-time、dev-ui、master）
- 本地分支对于远程分支的状态：上面**（up to date）表示本地分支和远程分支同步**；**(fast-forwardable)表示本地分支领先于远程分支**；**(local out of date)表示本地分支落后于远程分支**
- 对于本地分支如果没有推到远程仓库，那么是不被追踪的，也就没有本地与远程的比较，也就没有信息






