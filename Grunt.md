
## Grunt dependencies

### [connect-livereload](https://github.com/intesso/connect-livereload)
实时监控代码变化，主动刷新浏览器，不再需要coding--save--F5。（尤其适合双屏）  
本例中没有安装这个插件，因为使用了livereload的chrome插件，如果不想用chrome插件，可以用这个grunt插件。  
不管哪种方式，这个都依赖 grunt-contrib-watch，也可以同grunt-contrib-connect整合。  
[梦幻神话的博文](http://www.bluesdream.com/blog/grunt-plugin-livereload-wysiwyg-editor.html)  

### grunt-angular-templates
自动缩编，整合页面，自动生成HTML模板

### grunt-autoprefixer
解析CSS文件，自动添加浏览器前缀

### grunt-concurrent
并发执行grunt任务，即可以配置没有前后顺序可以同时执行的任务，其他的任务还是按照顺序执行的。

### grunt-contrib-clean
删除文件或目录

### grunt-contrib-concat
连接多个文件，合并成一个

### grunt-contrib-connect
为前端静态文件，搭建一个web服务

### grunt-contrib-copy
复制文件或目录

### grunt-contrib-cssmin
css压缩

### grunt-contrib-htmlmin
html压缩

### grunt-contrib-imagemin
图片压缩

### grunt-contrib-jshint
javascript代码检查

### grunt-contrib-uglify
javascript文件压缩

### jshint-stylish
jshint报告

### grunt-contrib-watch
监听文件变化事件，当有变化时做出处理。但是它有一个问题，就是每当监听到一处变动时，就会大费周章地把所有被监听的文件都处理一遍。这个问题可以由grunt-newer解决。   
这个需要在控制台grunt watch来启动。使用grunt插件启动没动静，目前还不清楚原因(在yo-angular-fullstack里是这样)。

### grunt-filerev
为了消除浏览器缓存的问题，每次编译后的资源名称都会重新起名（即在文件名和扩展名中间加一段md5随机数）

### grunt-google-cdn

### grunt-karma
自动化测试框架

### grunt-newer
让watch在监听到某个文件变动时，仅仅对变动的文件进行事务处理。使用本身没有配置，只要在task的前面加上newer:

### grunt-ng-annotate
Add, remove and rebuild AngularJS dependency injection annotations
为了解决ng代码中注入部分要写两遍的问题，

### grunt-svgmin
SVG可伸缩矢量图形 (Scalable Vector Graphics)压缩

### grunt-usemin  
Replaces references from non-optimized scripts, stylesheets and other assets to their optimized version within a set of HTML files (or any templates/views).   
将index.html文件里的引用的各种类型的资源文件合并、压缩、filerev重命名。

### grunt-wiredep
监听你的bower.json文件，当有新的组件加入时，在index.html文件（源代码）和karma.conf.js（测试代码）的 bower/endbower 块中自动注入依赖引用。

### jit-grunt
Just In Time Loader.
有了它grunt的依赖不用再一个一个loadNpmTasks了
它会根据task的名称自动加载node_modules目录下以grunt-contrib-taskName、grunt-taskName、taskName命名的插件；
当然有些插件名称特殊，或者很长，你也可以自定义，taskName和插件名称不必有规律。

### time-grunt
计算任务执行时间

### grunt-dom-munger
### grunt-env
### grunt-express-server
### grunt-injector
### grunt-mocha-test
### grunt-node-inspector
### grunt-nodemon
### grunt-open
### grunt-protractor-runner
### grunt-rev
### grunt-build-control


## 任务的执行顺序

### build
依次运行：  
> * clean:dist
> * wiredep
> * useminPrepare
> * concurrent:dist
> * autoprefixer
> * ngtemplates
> * concat
> * ngAnnotate
> * copy:dist
> * cdnify
> * cssmin
> * uglify
> * filerev
> * usemin
> * htmlmin

### default
依次运行：  
> * newer:jshint watch有变动的文件，检验代码规范
> * test 
> * build

### test
依次运行：  
> * clean:server
> * wiredep
> * concurrent:test
> * autoprefixer
> * connect:test
> * karma

### test
依次运行：  
> * clean:server
> * wiredep
> * concurrent:test
> * autoprefixer
> * connect:test
> * karma

### serve
依次运行：  
> * clean:server
> * wiredep
> * concurrent:server
> * autoprefixer:server
> * connect:livereload
> * watch



### serve
依次运行：  
> * clean:server
> * wiredep
> * concurrent:server
> * autoprefixer:server
> * connect:livereload
> * watch


### serve:dist
依次运行：  
> * build
> * connect:dist:keepalive
> * clean:server
> * wiredep
> * concurrent:server
> * autoprefixer:server
> * connect:livereload
> * watch




