# linux Python压缩包安装配置
1.下载python包  
[Python-3.5.2.tgz 压缩包](https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz)   
解压命令：tar zvxf Python-3.5.2.tgz  
[Python-3.5.2.tar.xz 压缩包](https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tar.xz)    
解压命令：tar xvf  Python-3.5.2.tar.xz  
两种格式的区别是大小不一样，解压方式也不一样


2.安装  
进入解压后目录，顺序执行：
```
./configure --prefix=安装在哪（可选）    #配置编译
make                                    #源码编译
make install                            #执行安装
```

3.建个软链接    
```
ln -s Python-3.5.2目录路径 /usr/bin/python3
#反正能链接到可执行程序就行
```
之后，执行python3进入交互式界面，pip3安装相关库

4.其他（待补充）
```
一定要注意，如果你不幸卸载了centos或者其他有yum命令的linux系统，再安装吧。因为yum命令就用到的是python脚本。     
python2.7的安装方式和3.5的一样，
重新安装python2.7之后，修改/usr/bin/yum文件，第一行的python改成python2.7版本的那个
```