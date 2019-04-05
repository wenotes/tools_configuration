# sublime text 3配置Python环境

### 配置编译环境    
- ①如果你只装一个Python版本，则不用配置，只需要选择默认的python环境，前提是你配置了python环境变量。菜单选择
Tools-->Build System-->Python，然后写个测试脚本试试。
- ②如果装了多种版本的，上面的那种方式只适用默认的python版本。此时需要Tools-->Build System-->New Build System，粘贴如下代码，然后命名（比如python3就命名为python3）保存，然后Tools-->Build System-->Python3，然后Ctrl+b执行测试脚本，就是python3执行的了。
```
{
    "cmd": ["XXXXXXXXXX","-u","$file"],
    "file_regex":"^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector":"source.python",
}
<!--xxxx是python.exe的绝对路径，例如：C:/../../../python.exe，注意是反斜杠-->
```



### 安装插件管理工具Package Control

首先安装插件管理工具，<b title="点此进入官网安装说明，不知道是要翻墙还是什么原因，我不翻墙访问不到。但也访问到过的">[package control](https://packagecontrol.io/installation)</b>，两种方式安装如下：
- 脚本安装
```

<!--Ctrl+` 打开sublime text3控制台,粘贴以下从官网复制的代码，enter键执行-->
import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
<!--执行后，稍等一会，看到 Preferences==>Package Control菜单-->
```
- 手动安装  
[package control插件下载](https://packagecontrol.io/Package%20Control.sublime-package)，之后打开菜单 Preferences==>Browse Packages 进入 Packages文件夹，退出当前文件夹，进入Installed Packages文件夹，把Package Control插件放入此文件夹中，然后重启sublime Text3。

    
### 一些不错的插件推荐
Ctrl+Shift+p，调出Package Control插件管理工具：
- 输入Install Package，enter进入插件安装过程（此处别急），然后搜索指定插件，选择安装；
- 输入Remove Package，enter进入插件移除过程，然后选择移除；
- 其他指令了解，可参考[Package Control用法](https://packagecontrol.io/docs/usage);

1. SublimeCodeIntel ：代码提示插件，支持多种语言；     
2. SublimeTmpl ：新建文件的时候，可定制模板；
3. sublimeREPL ：调试程序用的，支持多种语言；
4. Alignment ：对齐代码，Ctrl+alt+a；
5. Emmet ：前端代码编写神器;
6. Git ：你懂得；
7. 


### sublime 主题配置
