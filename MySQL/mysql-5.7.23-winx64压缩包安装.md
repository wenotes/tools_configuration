# mysql-5.7.23-winx64压缩包安装
- 下载  
    百度云链接：
    https://pan.baidu.com/s/1xROKRUrwUWVtYUQbq9ZtFA     
    提取码：7pyq 

1、解压配置环境变量

2、在压缩包目录下新建个data文件夹，再新建my.ini文件，并添加如下内容(*注意：路径的斜杠是反斜杠)：
```
    [mysql]
	default-character-set=utf8
	[mysqld]
	# 端口号
	port = 3306 
	# 设置为自己MYSQL的安装目录，为避免你自己自定义的目录例如‘\s’开头的字符被转义建议双反斜杠
	basedir=B:\\mysql-5.7.23-winx64
	# 设置为自己的MYSQL的数据目录
	datadir=B:\\mysql-5.7.23-winx64\\data 
	max_connections=200
	character-set-server=utf8
	default-storage-engine=INNODB
	sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
	#开启查询缓存
    explicit_defaults_for_timestamp=true
```

3、cmd执行命令  
    
    "注意：win10默认不是以管理员进入dos，下面必须管理员身份执行"
	mysqld -install
	#显示 Service successfully installed. 之后执行：
	mysqld --initialize-insecure --user=mysql
	#然后执行：
	net start mysql
	#无密码，直接连接mysql，改密码：
	mysql -u root
	#顺序执行语句：
	use mysql
	update user set authentication_string=password('123456') where user="root";
	flush privileges;
	exit;
	#再次登录：
	mysql -u root -p
	#就会提示输入密码123456了。