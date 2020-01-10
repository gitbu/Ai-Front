# 写文章手册

##　怎么插入图片等静态资源

### 绝对路径
当Hexo项目中只用到少量图片时，可以将图片统一放在public/img文件夹中，通过markdown语法访问它们。

public/img.jpg
1
![](/img/img.jpg)
图片既可以在首页内容中访问到，也可以在文章正文中访问到。

### 相对路径
图片除了可以放在统一的images文件夹中，还可以放在文章自己的目录中。文章的目录可以通过配置_config.yml来生成。

_config.yml
1
post_asset_folder: true
将_config.yml文件中的配置项post_asset_folder设为true后，执行命令$ hexo new post_name，在source/_posts中会生成文章post_name.md和同名文件夹post_name。将图片资源放在post_name中，文章就可以使用相对路径引用图片资源了。

_posts/post_name/image.jpg
1
![](image.jpg)