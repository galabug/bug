
### 1.安装Ruby和Ruby DevKit
      
      Ruby是Jekyll编写的编程语言。您需要安装Ruby和相应的DevKit，这需要将一些Jekyll的依赖项构建为“本地扩展”。


      [获取适用于Windows的Ruby](http://rubyinstaller.org/downloads/)

      执行安装程序并完成安装步骤。请确保选中“将Ruby可执行文件添加到PATH”框。


      安装Ruby DevKit

          Jekyll有一些依赖关系，它们只是提供原始的源代码。为了使它们成为功能完整的可执行文件，您可能需要安装开发套件。



  [获取Ruby DevKit](http://rubyinstaller.org/downloads/)

          下载是一个自解压存档。解压到一个没有空格的路径。我们推荐一些简单的，比如d:\RubyDevKit\

          接下来，您需要初始化DevKit并将其绑定到Ruby安装。打开您最喜欢的命令行工具，然后导航到您将DevKit解压缩到的文件夹。

          cd d:\RubyDevKit

          自动检测Ruby安装，并将它们添加到配置文件中以供下一步使用。

          ruby dk.rb init

          安装DevKit，将其绑定到Ruby安装。

          ruby dk.rb install


### 安装Jekyll

      安装

      Jekyll本身以Ruby Gem的形式出现，这是一个易于安装的软件包。要安装Jekyll及其所有默认依赖关系，请启动您最喜欢的命令行工具并输入以下命令。

      gem install jekyll

      等待完成。。。

      -----完成-----



    基本用法

    安装了 Jekyll 的 Gem 包之后，就可以在命令行中使用 Jekyll 命令了。有以下这些用法：

    jekyll build

    # => 当前文件夹中的内容将会生成到 ./site 文件夹中。

    jekyll build --destination <destination>

    # => 当前文件夹中的内容将会生成到目标文件夹<destination>中。

    jekyll build --source <source> --destination <destination>

    # => 指定源文件夹<source>中的内容将会生成到目标文件夹<destination>中。

    jekyll build --watch

    # => 当前文件夹中的内容将会生成到 ./site 文件夹中，

    #    查看改变，并且自动再生成。

    Jekyll 同时也集成了一个开发用的服务器，可以让你使用浏览器在本地进行预览。

    jekyll serve
    
    # => 一个开发服务器将会运行在 http://localhost:4000/

    jekyll serve --detach
    # => 功能和`jekyll serve`命令相同，但是会脱离终端在后台运行。
    #    如果你想关闭服务器，可以使用`kill -9 1234`命令，"1234" 是进程号（PID）。
    #    如果你找不到进程号，那么就用`ps aux | grep jekyll`命令来查看，然后关闭服务器。[更多](http://unixhelp.ed.ac.uk/shell/jobz5.html).

    jekyll serve --watch
    # => 和`jekyll serve`相同，但是会查看变更并且自动再生成。
    还有一些可以配置的配置选项. 很多配置选项既可以在命令行中作为标识(flags)设定，也可以在源文件根目录中的 _config.yml 文件中进行设定。Jekyll 会自动加载这些配置。比如你在你的 _config.yml 文件中添加了下面几行：

    source:      _source
    destination: _deploy
    那么就等价于执行了以下两条命令：

    jekyll build
    jekyll build --source _source --destination _deploy
    有关配置选项的更详细说明，请查看配置页面.















































      第一步，创建项目。

在你的电脑上，建立一个目录，作为项目的主目录。我们假定，它的名称为 jekyll_demo。



•$ mkdir jekyll_demo

对该目录进行git初始化:


•$ cd jekyll_demo
•$ git init

然后，创建一个没有父节点的分支 gh-pages，因为 github 规定，只有该分支中的页面，才会生成网页文件。


•$ git checkout --orphan gh-pages

以下所有动作，都在该分支下完成。
第二步，创建设置文件。

在项目根目录下，建立一个名为 _config.yml 的文本文件。它是 jekyll 的设置文件，我们在里面填入如下内容，其他设置都可以用默认选项，具体解释参见官方网页。



•baseurl: /jekyll_demo

目录结构变成：


•/jekyll_demo
•|--　_config.yml

第三步，创建模板文件。
在项目根目录下，创建一个 _layouts 目录，用于存放模板文件。



•$ mkdir _layouts

进入该目录，创建一个 default.html 文件，作为 Blog 的默认模板,并在该文件中填入以下内容。


•   
•   
•   
•   
•{{ page.title }}
•   
•   
•{{ content }}
•   
•  
Jekyll 使用 Liquid 模板语言，{{ page.title }} 表示文章标题，{{ content }} 表示文章内容，更多模板变量请参考官方文档。

目录结构变成：



•/jekyll_demo
•|-- _config.yml
•|-- _layouts
•|   |--　default.html

第四步，创建文章。
回到项目根目录，创建一个_posts目录，用于存放blog文章。



•   $ mkdir _posts

进入该目录，创建第一篇文章，文章就是普通的文本文件，文件名假定为 2012-08-25-hello-world.html。(注意，文件名必须为"年-月-日-文章标题.后缀名"的格式。如果网页代码采用 html 格式，后缀名为 html；如果采用 markdown 格式，后缀名为 md。）
在该文件中，填入



•---
•layout: default
•title: 你好，世界
•---
•{{ page.title }}
•我的第一篇文章
•{{ page.date | date_to_string }}

每篇文章的头部，必须有一个 yaml 文件头，用来设置一些元数据。它用三根短划线"---"，标记开始和结束，里面每一行设置一种元数据。"layout:default"，表示该文章的模板使用 _layouts 目录下的 default.html 文件；"title: 你好，世界"，表示该文章的标题是"你好，世界"，如果不设置这个值，默认使用嵌入文件名的标题，即 "hello world"。
在yaml文件头后面，就是文章的正式内容，里面可以使用模板变量。{{ page.title }} 就是文件头中设置的"你好，世界"，{{ page.date }} 则是嵌入文件名的日期（也可以在文件头重新定义date变量），"| date_to_string"表示将 page.date 变量转化成人类可读的格式。

目录结构变成：



•/jekyll_demo
•|--　_config.yml
•|--　_layouts
•|　　　|--　default.html
•|--　_posts
•|　　　|--　2012-08-25-hello-world.html

第五步，创建首页
有了文章以后，还需要有一个首页。

回到根目录，创建一个index.html文件，填入以下内容。



•---
•layout: default
•title: 我的Blog
•---
•{{ page.title }}
•最新文章
•   
•{% for post in site.posts %}
•{{ post.date | date_to_string }} {{ post.title }}
•{% endfor %}
•   

它的 Yaml 文件头表示，首页使用 default 模板，标题为"我的Blog"。然后，首页使用了{% for post in site.posts %}，表示对所有帖子进行一个遍历。这里要注意的是，Liquid 模板语言规定，输出内容使用两层大括号，单纯的命令使用一层大括号。至于 {{site.baseurl}} 就是 _config.yml 中设置的 baseurl 变量。
目录结构变成：



•/jekyll_demo
•|--　_config.yml
•|--　_layouts
•|　　　|--　default.html
•|--　_posts
•|　　　|--　2012-08-25-hello-world.html
•|--　index.html

第六步，发布内容。
现在，这个简单的 Blog 就可以发布了。先把所有内容加入本地 git 库。



•$ git add .
•$ git commit -m "first post"

然后，前往 github 的网站，在网站上创建一个名为 jekyll_demo 的库。接着，再将本地内容推送到 github 上你刚创建的库。注意，下面命令中的 username，要替换成你的 username。


•$ git remote add origin
https://github.com/username/jekyll_demo.git
•$ git push origin gh-pages

上传成功之后，等 10 分钟左右，访问 http://username.github.com/jekyll_demo/就可以看到 Blog 已经生成了（将 username 换成你的用户名）。
