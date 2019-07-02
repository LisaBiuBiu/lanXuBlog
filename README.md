## 搭建个人博客 ##

1.安装git
2.安装Node.js
3.安装Hexo
	
	npm install -g hexo-cli	
	hexo -v // 查看hexo的版本
4.初始化hexo
	
	hexo init     #Hexo自动在当前文件夹下下载搭建网站所需的所有文件
	npm install   #安装依赖包
	hexo g        #完整命令为hexo generate，生成静态文件
	$ hexo s        #完整命令为hexo server，启动服务器，用来本地预览
	hexo clean
	清除缓存文件 (db.json) 和已生成的静态文件 (public)。
	
新建完成后，指定文件夹目录下有：

	public：存放生成的页面
	scaffolds：生成文章的一些模板
	source：用来存放你的文章
	themes：主题
	** _config.yml: 博客的配置文件**