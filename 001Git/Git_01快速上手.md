# Git快速上手
一、新建仓库(repositories)
- 选择一个文件夹进入，执行：
```
git init                #初始化一个本地仓库
```
- GitHub上新建一个远程仓库(repositories)
- 修改隐藏目录.git中的config文件，在此文件中追加以下内容
```
[remote "origin"]
	fetch = +refs/heads/*:refs/remotes/origin/*
	url = 远程仓库地址
	pushurl= 远程仓库地址
[branch "master"]
	remote = origin
	merge = refs/heads/master
```

二、拉取远程仓库内容
```
git pull    #如果有readme.md文档的话，没有的话执行一下也不碍事
```

三、本地创建文件夹或者文件（文件必须得有），然后提交
```
#先add
    git add .
    git add all
#上面两个命令效果一样，都是添加所有变动内容，到缓存区。
#也可以add指定的文件
    git add 文件的路径
# 可以用git status 看看本地的add和commit情况
#然后commit
git commit -m '第一次测试提交'
```

