git remote remove <name> 

git remote  add cn git@code.csdn.net:wenyue1994/bankmanage.git
 git remote
git remote rename gh github
 git remote -v
 git checkout -b cn
git push csdn cn:master
====================
1添加remote信息
git remote  add coding https://coding.net/wswenyue/BankManage.git
2为每个仓库建立单独的分支
git checkout -b co
3.把本地分支推送到远端仓库的master分支
git push coding co:master


====================
++++++++++++++++++
git仓库中已经有一部分代码，所以它不允许你直接把你的代码覆盖上去。于是你有2个选择方式：
1，强推，即利用强覆盖方式用你本地的代码替代git仓库内的内容
git push -f
2，先把git的东西fetch到你本地然后merge后再push
$ git fetch
$ git merge
这2句命令等价于
$ git pull  
++++++++++++++++++

-----------------------------
如果远程仓库与本地仓库不一致

++++++++++++++++
取回origin主机的next分支，与本地的master分支合并，需要写成下面这样
$ git pull origin next:master
如果远程分支是与当前分支合并，则冒号后面的部分可以省略。
$ git pull origin next
上面命令表示，取回origin/next分支，再与当前分支合并。实质上，这等同于先做git fetch，再做git merge。
$ git fetch origin
$ git merge origin/next

++++++++++++++++
git push命令用于将本地分支的更新，推送到远程主机。它的格式与git pull命令相仿。
$ git push <远程主机名> <本地分支名>:<远程分支名>
注意，分支推送顺序的写法是<来源地>:<目的地>，所以git pull是<远程分支>:<本地分支>，而git push是<本地分支>:<远程分支>。
$ git push origin master
上面命令表示，将本地的master分支推送到origin主机的master分支。如果后者不存在，则会被新建。
如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。

$ git push origin :master
# 等同于
$ git push origin --delete master
上面命令表示删除origin主机的master分支。
如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。
$ git push origin
上面命令表示，将当前分支推送到origin主机的对应分支。
如果当前分支只有一个追踪分支，那么主机名都可以省略。

$ git push
如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push。

$ git push -u origin master
上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。
不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。如果要修改这个设置，可以采用git config命令。

$ git config --global push.default matching
# 或者
$ git config --global push.default simple
还有一种情况，就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要使用--all选项。

$ git push --all origin
上面命令表示，将所有本地分支都推送到origin主机。
如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做git pull合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用--force选项。

$ git push --force origin 
上面命令使用--force选项，结果导致远程主机上更新的版本被覆盖。除非你很确定要这样做，否则应该尽量避免使用--force选项。
最后，git push不会推送标签（tag），除非使用--tags选项。

$ git push origin --tags
++++++++++++++++
git pull origin master
此句命令的作用是：将origin远程仓库的master分支拉下来与本地分支合并，同时更新本地分支


git remote -v                    # 查看远程服务器地址和仓库名称
git remote show origin           # 查看远程服务器仓库状态
git remote add origin git@github:robbin/robbin_site.git         # 添加远程仓库地址
git remote set-url origin git@github.com:robbin/robbin #修改远程地址
git remote rm #删除远程创库地址

==================================================
//拉取远程仓库到本地tep分支
git fetch origin master:tmp
//查看是否有更改，如果有，考虑要不要合并
git diff tmp 
//合并分支到本地
git merge tmp
-----------------
git pull：相当于是从远程获取最新版本并merge到本地
git pull origin master
这一条是上面三条的功能
建议使用上面三条，因为你不确定远程仓库的就是最好的版本


