---
layout: post
title: "Win10配置Git Bash环境"
date: 2018-06-07
description: "GitBash的安装、配置与使用"
tag: 博客
---



<br>

### 0、前言

Git是一个开源的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。Git是Linus Torvalds为了帮助管理Linux内核开发而开发的一个开放源码的版本控制软件。

GitHub是一个面向开源及私有软件项目的托管平台，因为只支持Git作为唯一的版本库格式进行托管，故名GitHub 。

当我们注册了GitHub的账号之后，可以建一个主仓库（username.github.io），这里用来存储我们的代码，我们可以利用Git Bash实现GitHub与电脑的同步。这样，在电脑上实现相应代码，再push到GitHub上，就可以搭建出自己的博客了，不需要购买域名和服务器。

如果有自己的域名，可以在将域名写在 CNAME文件中，这样访问自己的域名，就可以进入搭建在GitHub的个人博客。

因为很早之前就注册了GitHub的账号，也建立了主仓库，所以这里只记录Git Bash的安装与使用。

<br>



### 1、安装Git Bash

进入 [官网](https://git-scm.com) ，选择下载适合自己电脑版本的安装包，安装过程很简单，一路默认即可。

<br>



### 2、配置Git Bash

- 打开Git Bash

  ![](/images/posts/blog/a1.jpg)

- 获取自己的密钥（注意以下命令中的空格）

  ```c++
  $ ssh-keygen -t rsa -C "1057510406@qq.com"   //双引号内为注册GitHub时绑定的邮箱账号
  ```

  之后会有一些让你确认的操作，一路按回车即可。

- 成功创建密钥之后，去它提示的位置打开id_rsa文件，复制里面的内容，本机的密钥文件在

  > C:\Users\Administrator\.ssh\id_rsa

- 登录到GitHub，添加此密钥：头像——Settings——SSH and GPS keys——New SSH key

  ![](/images/posts/blog/a2.jpg)

  Title：是给此密钥起的名字，随意取即可

  Key：放入刚刚复制的密钥

  保存即可

  ![](/images/posts/blog/a3.jpg)

- 回到Git Bash，输入以下命令，检查是否绑定成功

  ```C++
  $ ssh -T git@github.com
  ```

  第一次绑定的时候输入以上命令之后，会提示是否continue，输入yes之后，如果出现以下提示命令，就说明，已经成功连上了GitHub

  > Hi username ! You've successfully authenticated, but GitHub does not provide shell access. 

- 接下来还需要设置username和useremail，输入以下命令（顺序可以颠倒）

  ```C++
  $ git config --global user.name "Chevonneqwh"	// 双引号内为用户名
  $ git config --global user.email "1057510406@qq.com"	// 双引号内为注册邮箱
  ```

- 至此，Git Bash已经配置完成了

  ![](/images/posts/blog/a4.jpg)

<br>



### 3、clone仓库到本地

将自己在GitHub上建的仓库克隆到本地，方便以后进行代码的编写与上传。

- 首先将路径定位到下载的位置，这里定位到E盘

  ```C++
  $ cd /E
  ```

  出现 /E即说明定位成功。

- 输入以下命令克隆仓库到E盘

  ```c++
  $ git clone https://github.com/Chevonneqwh/Chevonneqwh.github.io      //网址为仓库的地址
  ```

- 打开E盘，就可以看到这里已经有了一个有着我们仓库名的文件夹了

  ![](/images/posts/blog/a5.jpg)

- 之后可以在这个文件夹里实现相应的编码，再push到GitHub上即可

<br>



### 4、push仓库至GitHub

将自己在本地（仓库对应的文件夹）编写的文件，push到GitHub上，等几分钟后，就可以输入网址看到效果。

- 找到自己要上传的文件夹，在此文件夹上点击右键，选择Git Bash Here

  ![](/images/posts/blog/a6.jpg)

- 之后会弹出下面这个窗口

  ![](/images/posts/blog/a7.jpg)

- 在窗口中输入以下命令

  ```C++
  $ git add .	//将整个文件夹添加到缓冲区（注意add与.之间有一个空格）
  $ git commit -m "first push" 	//提交到分支（双引号内的内容是注释，对本次push进行说明，随意填写即可）
  $ git push origin master	//将当前分支推送到远程仓库
  ```

- 以上，就实现了本地与远程仓库的同步，等待几分钟，就可以刷新出内容了

  ![](/images/posts/blog/a8.jpg)