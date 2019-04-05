# nginx关键字之rewrite
### 语法须知
**一、location匹配规则及优先级**：    
1. = 严格匹配这个查询。如果找到，停止搜索。
2. ^~ 匹配路径的前缀，如果找到，停止搜索。
3. ~ 区分大小写匹配
4. ~* 不区分大小写匹配 
5. ! 和以上搭配，不匹配

**二、文件及目录匹配**：
1. -f和!-f用来判断是否存在文件
2. -d和!-d用来判断是否存在目录
3. -e和!-e用来判断是否存在文件或目录
4. -x和!-x用来判断文件是否可执行

**三．rewrite指令：**
>在server块下，会优先执行rewrite部分，然后才会去匹配location块 
1. last 相当于apache里面的[L]标记，表示rewrite。
2. break本条规则匹配完成后，终止匹配，不再匹配后面的规则。
3. redirect 返回302临时重定向，浏览器地址会显示跳转后的URL地址。
4. permanent 返回301永久重定向，浏览器地址会显示跳转后的URL地址。



















### 场景用法

- 路由重定向
```
location / {
    if ( $request_uri = "/") {
        rewrite "/" /xxx last;
    }
}
<!--
这个意思是，访问ip:port的时候，自动重定向到ip:port/xxx
-->
```
- 400重定向
```
if ( !-e $request_filename )
　　　　{
　　　　　　rewrite ^/(.*)$ index.html last;
　　　　}

```