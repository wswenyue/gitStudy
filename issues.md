####git问题集
#push到github时，每次都要输入用户名和密码的问题

每次push  的时候，都要输入用户名和密码，很是麻烦
原因是使用了https方式 push

在termail里边 输入  git remote -v 
可以看到形如一下的返回结果
origin https://github.com/yuquan0821/demo.git (fetch)
origin https://github.com/yuquan0821/demo.git (push)

下面把它换成ssh方式的。
1. git remote rm origin
2. git remote add origin git@github.com:yuquan0821/demo.git
3. git push origin 
===============================================