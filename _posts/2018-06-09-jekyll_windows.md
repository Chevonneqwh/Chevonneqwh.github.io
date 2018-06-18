---
layout: post
title: Win10配置Jekyll环境
date: 2018-06-09 
tags: 博客   
---



<br>

### 0、前言

Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过 Markdown （或者 Textile） 以及 Liquid 转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

Jekyll 是一个免费的简单静态网页生成工具，可以配合第三方服务例如： Disqus（评论）、多说(评论) 以及分享等扩展功能，Jekyll 可以直接部署在 Github（国外） 或 Coding（国内） 上，可以绑定自己的域名。[Jekyll中文文档](http://jekyll.bootcss.com/)、[Jekyll英文文档](https://jekyllrb.com/)、[Jekyll主题列表](http://jekyllthemes.org/)。

<br>

### 1、安装Ruby

- 下载地址：[RubyInstaller](https://rubyinstaller.org/downloads/)

- ![](/images/posts/blog/b1.jpg)

- 注意版本要选2.0~3.0之间

- 之后，运行安装。本机安装在

  > D:\Qinwenhui\Ruby\Ruby22-x64

- 安装成功后，添加环境变量 

  > D:\Qinwenhui\Ruby\Ruby22-x64\bin

<br>



### 2、安装DevKit

- 下载地址：[RubyInstaller](https://rubyinstaller.org/downloads/)

- ![](/images/posts/blog/b2.jpg)

- 双击运行，之后会出现解压的路径

- 本机选择的解压路径为

  > D:\Qinwenhui\Ruby\DevKit

- 运行cmd

- 将路径定位到DevKit文件夹下

![](/images/posts/blog/b3.jpg)

- 在DevKit路径的DOS窗口下，进行初始化

  ```c++
  ruby dk.rb init
  ```

- 运行之后，打开DevKit文件夹，此时已经创建了一个config.yml文件，打开此文件，或用命令打开此文件

  ```c++
  notepad config.yml  //用记事本打开config,yml
  ```

- 在该文件末尾添加

  ```c++
  - D:/Qinwenhui/Ruby/Ruby22-x64
  ```

- 之后回到DOS窗口，执行以下命令

  ```c++
  ruby dk.rb review  // 审查（非必须）
  ruby dk.rb install  //安装gem
  gem -v  //查看gem是否正常安装
  ```

  ![](/images/posts/blog/b4.jpg)

<br>



### 3、安装jekyll

- 还是在刚刚的窗口下，执行以下命令

  ```c++
  gem install jekyll
  ```

- 会出现很长的命令，等几十秒

  ![](/images/posts/blog/b5.jpg)

  ![](/images/posts/blog/b6.jpg)

- 安装成功

- 可测试一下

  ```c++
  jekyll --version
  ```

<br>



### 4、新建项目 & 运行

- 在窗口中执行下列命令

  ```c++
  jekyll new myBlog  //在DevKit文件夹下新建一个myBlog的项目
  ```

- 如果没有报任何错，会在DevKit文件夹下产生一个myBlog文件夹

  ![](/images/posts/blog/b7.jpg)

- 然后回到命令窗口，将路径定位到myBlog

  ```c++
  cd myBlog
  ```

- 运行服务器

  ```c++
  jekyll serve
  ```

  ![](/images/posts/blog/b8.jpg)

- 出现这个界面之后，打开浏览器，输入网址

  ```c++
  http://localhost:4000
  ```

- 新建的项目，运行成功是一个空白界面，修改index.md即可产生想要的内容

<br>



### 5、遇到的错误

#### 5.1 运行自己新建的项目出错

- 以上步骤不一定都可以运行成功

- 本此安装，在最后运行服务器jekyll serve处出错了

  ![](/images/posts/blog/b9.jpg)

- 基于此，安装bundler，执行以下命令

  ```c++
  gem install bundler
  ```

  ![](/images/posts/blog/b10.jpg)

- 因为之前出错的时候手动把项目删了，所以这里重建

  ```c++
  jekyll new mymy
  ```

  ![](/images/posts/blog/b11.jpg)

- 之后

  ```c++
  cd mymy
  jekyll serve
  ```

  

- 会发现还是有错误

  ![](/images/posts/blog/b12.jpg)

- 去mymy文件夹下将名为Gemfile的文件删除

  ![](/images/posts/blog/b13.jpg)

- 再次运行服务器

  ```c++
  jekyll serve
  ```

  ![](/images/posts/blog/b14.jpg)

- 打开mymy文件夹下的_config.yml文件，删除下面这句话

  ![](/images/posts/blog/b15.jpg)

- 保存之后，再次运行服务器

  ```c++
  jekyll serve
  ```

  ![](/images/posts/blog/b16.jpg)

- 之后打开浏览器，输入网址即可

  ![](/images/posts/blog/b17.jpg)



#### 5.2 运行模板有错误

- 在网上找了一个模板，想运行试试效果，结果出现了错误

  > Could not find public_suffix-3.0.0 in any of the sources(Bundler::GemNotFound)

- 在Stackoverflow找到了解决办法：命令行运行以下命令

  ```c++
  bundle update
  ```

  ![](/images/posts/blog/b18.jpg)

- 之后再次运行

  ```c++
  jekyll serve
  ```

- 成功

  ![](/images/posts/blog/b19.jpg)

- 在浏览器输入网址访问即可