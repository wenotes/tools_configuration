# nginx配置参考

一、前后端分离项目
- 前端vue或react打好的包(dist)，nginx启动
- 后端java打好的war包(project.war)，Tomcat启动
```
server {
        listen       port;#浏览器访问端口
        server_name  localhost;
        root /../../dist;#前端包绝对路径

        location /dist {
            root   html;
            index  index.html index.htm;
            try_files $uri $uri/ /index.html;
        }

        location /aiFactoryServer {
            proxy_pass http://ip:port/project;#Tomcat访问端口及路径
        }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
   }

```
二、