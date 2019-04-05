## MySQL安装要注意的及可能出现的问题
1.如果之前存在异常的mysql服务先删除
    
    mysqld -remove MySQL或者sc delete mysql；
    如果还删除不了，删除注册表文件，win+r输入regedit，
    进入目录\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services在这里找到mysql，删除此文件夹    
    
2.如果存在data文件夹先备份删除此文件夹    
    
    在执行mysqld --initialize

3.必须以管理员身份进入dos

    "这里注意，win10默认不是以管理员进入dos"
    执行下面这个命令：
    mysqld -install（可以自定义服务名，例如mysqld -install mysql8）
    
4.提示安装MySQL服务成功后执行net start MySQL

    若有错误，请查看logs/error.log或者DESKTOP-EGPRERG.err文件查看错误原因

5.*win10安装报错
    
    由于找不到msvcr120.dll等等，
    安装Visual C++ Redistributable Packages for Visual Studio 2013，位数自己选择
    （我的选择vcredist_x64.exe）
    下载链接：https://www.microsoft.com/en-us/download/details.aspx?id=40784

6.还有一些其他错误启动不了mysql服务，如果实在没办法尝试
    
    以管理员启动cmd，然后进入mysql的bin目录
    输入命令mysqld.exe --console来启动mysql，然后就可以使用了

7.安装多个mysql
    
    要改端口号port、basedir、datadir，
    尽量不要在一个盘下，mysql8配置文件中不要加sql-mode
    
8.mysql8建议使用msi文件自动安装

9.如果报这个错

    [warn] evsignal_init: socketpair: Permission denied，
    可能是因为公司办公内网设置了什么限制