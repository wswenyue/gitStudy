#git问题集
##push到github时，每次都要输入用户名和密码的问题

每次push的时候，都要输入用户名和密码，很是麻烦
原因是**使用了https方式push**

```bash
# 在termail里边 输入  
$ git remote -v 
# 可以看到形如一下的返回结果
origin https://github.com/wswenyue/demo.git (fetch)
origin https://github.com/wswenyue/demo.git (push)
```

下面把它换成ssh方式的。
```bash
$ git remote rm origin
$ git remote add origin git@github.com:wswenyue/demo.git
$ git push origin 
```

----
##在windows下的文件的权限因为无法和linux上完全一致，所以用Git检出的文件权限可能显示为被更改

**另外因为windows下的换行和linux上也不一样，协作开发时也容易出问题。所以在windows上使用Git的同学需要加上以下2行配置参数**：

```bash
# 忽略文件权限的改动。
$ git config --global core.filemode false 
# 将文件checkout时自动把LF转成CRLF，check in 时自动把CRLF转成LF
$ git config --global core.autocrlf true 
```

##设置常用命令的别名
在用户的home目录下，有一个`.gitconfig`文件，里面可以配置一些别名，方便平时的git操作。

```bash
--------------------------
[alias]
    st = status -s
    ci = commit
    l = log --oneline --decorate -13
    ll = log --oneline --decorate
    co = checkout
    br = branch
    rb = rebase
    dci = dcommit
--------------------------------
```