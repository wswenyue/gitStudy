# tag

##常用指令

```bash
$ git tag v1.0.0 [SHA] 
# 打一个轻量级的tag，只是一个commit的指向引用,[SHA]是可选择值（某个commit的SHA），指定为哪个commit打tag，如果没写则直接为最后一个commit打tag

$ git tag -a v1.0.0 -m "你的附注信息" [SHA] 
# 一个带附注信息的tag，不是一个简单的引用，而是单独的一个对象，[SHA]是可选择值（某个commit的SHA），指定为哪个commit打tag，如果没写则直接为最后一个commit打tag

$ git tag 
# 列出所有的tag

$ git show v1.0.0  
# 打印指定tag的信息

$ git tag -d v1.0.0 
# 删除本地指定tag

$ git push origin :refs/tags/v1.0.0 
# 删除远程tag

$ git push github v1.0.0
# 把标签推到远端： v1.0.0为你的自定义标签名

```


