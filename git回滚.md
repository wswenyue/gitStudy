# git回滚操作

```
# 丢弃工作区的改动
$ git checkout -- <file>... 
```

##修改之后，使用add添加到暂存区后，觉得修改都不要了，那么如何回滚：

```bash
$ git reset head 要回滚的文件
$ git checkout 要回滚的文件
```

## git修改之后不想提交，如何保存工作区进度：

```bash
$ git stash

# 恢复使用：
$ git stash pop
```

