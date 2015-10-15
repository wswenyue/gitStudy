
========================================
为了防止Github被墙，最好在国内的托管商做一个备份，这就需要同时提交到多个远端仓库，例如一个open source项目同时要提交csdn和github，url分别是：

git@github.com:lutaf/auto-complete.git
git@code.csdn.net:lutaf/autocomplete.git
方法很简单，一共分4步：

第一步：添加remote信息

git remote  gh git@github.com:lutaf/auto-complete.git 
git remote cn git@code.csdn.net:lutaf/autocomplete.git 


git remote  add cn git@code.csdn.net:wenyue1994/bankmanage.git

第二步：为每个仓库建立单独的分支

git checkout -b github 
... 
git checkout -b csdn 
第三步：在各自分支上完成开发，并提交

第四步：把本地分支推送到远端仓库的master分支

git checkout csdn 
git push  cn csdn:master 
第四步很关键，一定是要推送到远端仓库的master分支

====================================
git remote 不带参数，列出已经存在的远程分支，例如：
#git remote

git remote -v | --verbose 列出详细信息，在每一个名字后面列出其远程url，例如：
#git remote -v

git remote add name url 在url创建名字为name的仓库（Adds a remote named <name> for the repository at <url>）
name为远程仓库的名字

git remote show name 必须要带name，否则git remote show的作用就是git remote，给出remote name的信息。 

$ git remote rm origin
$ git remote add origin
$ git remote add origin git@github.com:tualatrix/gentoo.git
$ git push origin 


++++++++++++++++++++++++++++++
在windows下的文件的权限因为无法和linux上完全一致，所以用Git检出的文件权限可能显示为被更改。 另外因为windows下的换行和linux上也不一样，协作开发时也容易出问题。所以在windows上使用Git的同学需要加上以下2行配置参数：

git config --global core.filemode false //第一句是忽略文件权限的改动。
git config --global core.autocrlf true //第二句是将文件checkout时自动把LF转成CRLF，check in 时自动把CRLF转成LF
++++++++++++++++++++++++++++++
设置常用命令的别名
在用户的home目录下，有一个.gitconfig文件，里面可以配置一些别名，方便平时的git操作。
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

----------------------------

