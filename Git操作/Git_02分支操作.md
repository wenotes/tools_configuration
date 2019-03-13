# 分支操作
一、获取远程分支
```
git fetch
```

二、查看分支
```
#查看本地分支
git branch

#查看远程分支
git ls-remote

#查看所有分支
git branch -a
#若出现无法显示全部分支的情况，按照下面操作，先创建一个test.txt文件，然后add、commit、push,在执行此命令就可以了。
```

三、本地创建分支推送到远程
```
#新建并切换到本地分支
git checkout -b <自定义本地分支名>
#推送远程
git push origin <本地分支名>
```

四、切换分支并推送内容到远程
```
git checkout <本地分支>
# 下面操作必须是commit过了的
git push origin <远程分支名>
```

五、切换远程分支到本地
```
git checkout -b <远程分支名> origin/<远程分支名>
#然后就可以git pull下来了
```

六、删除分支
```
#删除本地分支
git branch -d <本地分支名>
#删除远程分支
git push origin --delete <远程分支名>
```