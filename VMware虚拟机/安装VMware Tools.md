# 安装VMware Tools


1、启动虚拟机

2、点击VMware“虚拟机”选项>选择“VMware Tools安装”，此时VMware Tools的安装镜像挂载到光驱上了。

3、通过df命令可以看到VMware Tools镜像的所在目录。
```
df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/vg_xiaoming2-lv_root   37G  4.2G   31G  12% /
tmpfs                             491M   76K  491M   1% /dev/shm
/dev/sda1                         485M   35M  426M   8% /boot
/dev/sr0                          4.2G  4.2G     0 100% /media/VMware Tools
# 最下面的就是镜像所在目录
```

4、一般来说，把这个VMware Tools的压缩包拿出来到自己的目录下进行安装操作。

5、拿出来，解压压缩包，然后进入目录执行./vmware-install.pl。