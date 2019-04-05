# 安装Nginx(以centos平台为例)
[nginx安装教程参考](http://www.nginx.cn/install)  

Nginx版本：nginx-1.14.2[下载](http://nginx.org/en/download.html)    
linux版本：centos-6.5

### 1、安装依赖
```
yum -y install gcc  #GNU编译器套件
yum -y install pcre-devel #用C编写的正则表达式库，匹配路由用的
yum -y install zlib-devel #nginx非常适合静态资源的传输，就是因为这个库
yum -y install openssl-devel  #这个负责安全的传输
```
##### 顺便了解linux
devel 包主要是供开发用，至少包括以下2个东西:
1. 头文件
2. 链接库，有的还含有开发文档或演示代码。
以 glib 和 glib-devel 为例:
如果你安装基于 glib 开发的程序，只需要安装 glib 包就行了。
但是如果你要编译使用了 glib 的源代码，则需要安装 glib-devel。


### 2、安装nginx
```
<!--进入nginx解压包目录，执行下面命令-->
./configure         #此处就直接默认安装了
<!--可选参数-->
--prefix=绝对路径    定义一个目录，存放服务器上的文件 ，也就是nginx的安装目录。默认使用 /usr/local/nginx。

<!--然后执行make编译，从Makefile文件中读取指令编译-->
make
<!--然后执行make install安装，也从Makefile文件中读取指令-->
make install

<!--也可以一次性，./configure && make && make istall-->
```
##### 了解典型的使用GNU的AUTOCONF和AUTOMAKE产生的程序的安装步骤
1、**./configure** 是用来检测你的安装平台的目标特征的。比如它会检测你是不是有CC或GCC，并不是需要CC或GCC，它是个shell脚本。   
2、**make** 是用来编译的，它从Makefile中读取指令，然后编译。  
3、**make install**是用来安装的，它也从Makefile中读取指令，安装到指定的位置（--prefix参数指定的位置）。
> 详解：        
1、./configure      
　　这一步一般用来生成Makefile，为下一步的编译做准备，你可以通过在 configure 后加上参数来对安装进行控制，比如代码:./configure –prefix=/usr 意思是将该软件安装在 /usr 下面，执行文件就会安装在/usr/bin（而不是默认的/usr/local/bin),资源文件就会安装在/usr/share（而不是默认的/usr/local/share）。同时一些软件的配置文件你可以通过指定 –sys-config= 参数进行设定。有一些软件还可以加上 –with、–enable、–without、–disable 等等参数对编译加以控制，你可以通过允许 ./configure –help 查看详细的说明帮助。    
2、make     
　　这一步就是编译，大多数的源代码包都经过这一步进行编译（当然有些perl或python编写的软件需要调用perl或python来进行编译）。如果在make过程中出现error，你就要记下错误代码（注意不仅仅是最后一行），然后你可以向开发者提交bugreport（一般在INSTALL里有提交地址），或者你的系统少了一些依赖库等，这些需要自己仔细研究错误代码。可能遇到的错误：make *** 没有指明目标并且找不到makefile。问题很明了，没有Makefile，怎么办，原来是要先./configure 一下，再make。      
3、make install     
　　这条命令来进行安装（当然有些软件需要先运行 make check 或 make test 来进行一些测试），这一步一般需要你有 root 权限（因为要向系统写入文件）。
　　
### 3、启动nginx
```
cd /usr/local/nginx/sbin/
./nginx
<!--然后访问ip:80，就可以看到welcome nginx界面了，80是默认端口-->
<!--重启nginx-->
./nginx -s reload 
<!--关闭nginx-->
./nginx -s stop

```