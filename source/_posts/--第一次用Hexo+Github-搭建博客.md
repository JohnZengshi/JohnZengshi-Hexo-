---
title:	第一次用Hexo+Github 搭建博客
data: 2015/11/8 20:46:25
categories: 网站搭建
tags: 建站技巧
---
## 大概可以分为以下几个步骤：
``` bash
1.搭建环境准备（包括node.js和git环境，gitHub账户的配置）
2.安装Hexo
3.配置Hexo
4.怎样将Hexo与github page 联系起来
5.怎样发布文章
```



>### `搭建环境准备`

* Node.js 的安装和准备 (本文略过)
* Git的安装和准备 (本文略过)
* gitHub账户的配置(本文略过)

>### `安装Hexo`
##### *创建一个文件夹Hexo,并在命令行的窗口进入到该目录*
#### 1.命令行中输入：
	npm install hexo-cli -g
	npm install hexo --save
#### 2查看hexo版本：
	hexo -v
>### `hexo的相关配置`
#### 1.初始化Hexo：
	hexo init
	npm install（之后npm将会自动安装你需要的组件）
#### 2.在命令行中，输入：
	hexo g
	hexo s
##### *在浏览器中打开 http://localhost:4000 访问本地的博客*

>### `将Hexo与github page 联系起来`
#### 1.设置Git的user name和email：(如果是第一次的话)
	git config --global user.name "xujun"
	git config --global user.email "gdutxiaoxu@163.com"
#### 2.生成密钥(可以忽略)
	ssh-keygen -t rsa -C "gdutxiaoxu@163.com"
#### 3.配置Deployment（在_config.yml文件中，找到Deployment）
	deploy:
	type: git
	repo: git@github.com:yourname/yourname.github.io.git
	branch: master
>### `写博客、发布文章`
##### *博客文章存放在hexo\source\ _posts下*
#### 1.MarDown编辑器编辑文章后，执行下面的命令
	hexo d -g （#在部署前先生成）
#### 2.踩坑提醒：（注意需要提前安装一个扩展：）
	npm install hexo-deployer-git --save