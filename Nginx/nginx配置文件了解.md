
#### 初始的nginx.conf文件
```
#user  nobody; #指定 Nginx 进程运行用户
worker_processes  1; #一般情况下不用修改，不过此时有两个线程，还有一个主的
#1、SSL、gzip这些比较消耗CPU的工作如果是多核cpu的话，可以设置和cpu核数一样
#2、如果要处理很多很多的小文件，且文件总大小比内存大很多的时候，可以加点进程，以充分利用IO带宽

# worker_rlimit_nofile 65535; # 这个参数主要是根据系统支持打开最大文件数来确定的

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;
#pid        logs/nginx.pid;

events {
    worker_connections  1024;
    # 指单个工作进程可以允许同时建立（内外）连接的数量
}

http {
    include       mime.types;# 是文件扩展名与文件类型映射表
    default_type  application/octet-stream;# 默认文件类型

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    sendfile        on;
    # sendfile指令指定 nginx 是否调用sendfile 函数（zero copy 方式）来输出文件，对于普通应用，必须设为on。如果用来进行下载等应用磁盘IO重负载应用，可设置为off，以平衡磁盘与网络IO处理速度，降低系统uptime。
    #tcp_nopush     on; #在 nginx 中，tcp_nopush 必须和 sendfile 搭配使用。
    #tcp_nodelay     on;#和tcp_nopush互斥，禁用Nagle算法。
    ## Nagle算法是tcp传输数据包的算法，它会将小数据包组成大数据包或者将大数据包分批发送的一种优化算法

    #keepalive_timeout  0;
    keepalive_timeout  65;
    #使用keep-alive可以改善这种状态，即在一次TCP连接中可以持续发送多份数据而不会断开连接。通过使用keep-alive机制，可以减少tcp连接建立次数，也意味着可以减少TIME_WAIT状态连接，以此提高性能和提高httpd服务器的吞吐率(更少的tcp连接意味着更少的系统内核调用,socket的accept()和close()调用)。
    #但是这个设置时间长了，无效的tcp连接占用系统资源
    #keepalive_timout时间值意味着：一个http产生的tcp连接在传送完最后一个响应后，还需要等等keepalive_timeout秒后，才开始关闭这个连接。为了看看浏览器还有没有http请求，意思别急关闭再等等。

    #gzip  on;#开启gzip压缩输出，还有附带一些其他关于压缩的参数配置

    server {
        listen       80;# 监听端口
        server_name  localhost;# 域名可以有多个，用空格隔开
        #charset koi8-r;#字符集
        #root /home/../..;前端包的路径

        #access_log  logs/host.access.log  main;

        location / {
            root   html;
            index  index.html index.htm;
        }

        #error_page  404              /404.html;
        
        # redirect server error pages to the static page /50x.html
        # 这个是500以上响应的页面，50x.html在nginx/html文件夹下面，可以自定制
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #location ~ /\.ht {
        #    deny  all;
        #}
    }

    # another virtual host using mix of IP-, name-, and port-based configuration
    # 这部分意思就是可以写多个server
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;
    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}

    # HTTPS server
    #HTTPS server是啥样色的
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;
    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}
}
```

相关博客参考：  
[Nginx配置文件nginx.conf详解](https://www.cnblogs.com/xuey/p/7631690.html)      
[keepalvie timeout解释参考，推荐](http://www.nowamagic.net/academy/detail/23350305)