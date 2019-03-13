# Git使用注意事项
- 1.一般来说命令后加 -h 可以查看帮助，例如git add -h
- 2.目录下的文件名称尽量不要有中文或者空格之类的
- 3.git 上传不了空文件夹


- 4.尽量不要在git仓库中修改已上传过服务器的文件夹名称，然后git push，会报错，如果想修改则要,如下操作：
```
<!--例如：把文件夹testA名称改成testB-->
1、首先本地修改testA改成testB
git status  # 可以看到要让你rm本地的testA
2、删除本地缓存区的testA和下面的文件
git rm testA*
3、添加testB到本地缓存区
git add testB*
4、提交改动的内容到本地仓库
git commit -m '文件夹testA名称改成testB'
5、把改动内容推到远程仓库
git push
```