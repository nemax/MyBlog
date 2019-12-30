---
title: 一篇文章搞定Github Pages托管Hexo博客
date: 2019-04-25 02:12:36
tags: 
	- Blog
	- Hexo
reward: true
---

## 1.基本环境搭建

诚如Hexo文档所言，搭建Hexo非常简单。可以参考[官方文档](https://hexo.io/zh-cn/docs/index.html)准备好本地环境。

唯一需要说明的就是安装好npm以后需要设置npm镜像服务器地址为淘宝镜像，否则可能出现npm下载速度慢的问题。

```shell
$ npm config set registry http://registry.npm.taobao.org
```

对node.js感兴趣的同学可以自行访问[TaoBaoNPM](http://npm.taobao.org/)进行学习，淘宝还改了个cnpm可以取代默认的npm...

如果设置registry成功可以通过命令:

```shell
$ npm config list | findstr registry
```

看到返回:

![NPM Registry设置结果](http://ww1.sinaimg.cn/large/69110301ly1g2e7cbeywvj20it0bemx5.jpg)

然后按照官方文档要求安装安装hexo-cli包

```power
npm install -g hexo-cli
```

![hexo-cli安装](http://ww1.sinaimg.cn/large/69110301ly1g2e7fyz9lij20ph0ei74o.jpg)	

至此，hexo-cli安装完毕，剩下的就是安装git了，因为之后hexo初始化本地目录时实际会调用git命令!

**Git的安装本教程不进行说明，请同学们自行完成。**

接下来就进入建站过程了

## 2.站点搭建

选择一个目录作为本地hexo目录，然后再本目录下进行初始化工作:

```shell
$ hexo init ./Blog
$ cd ./Blog
$ npm install
```

执行过程中可能出现NPM的审计检查报告:

![npm 审计检查报告](http://ww1.sinaimg.cn/large/69110301ly1g2e7rlv6wlj212t0cbmy6.jpg)

当依赖项中可能存在漏洞时会发出这个警告，按照提示键入

```shell
$ npm audit fix
```

即可，但有时候你可能会失望，比如此次修复就无济于事 😂

![NPM 审计修复失败](http://ww1.sinaimg.cn/large/69110301ly1g2e8421iu1j2104042dfy.jpg)

算了，小事情，继续前进。至此，你的目录下应该已经建好了站点的骨架。下一步就是进行配置了。

## 3.站点配置

这部分才考[官方文档](https://hexo.io/zh-cn/docs/configuration)即可

## 4.本地启动站点

如果前面的步骤都没问题，只消一句即可本地启动站点，之后也可以通过本地启动站点来测试对网页的修改后再部署到服务器端。

```shell
$ hexo server
```

默认端口是4000，打开网页，如果出现页面则表明成功!

![本地搭建好的Hexo博客](http://ww1.sinaimg.cn/large/69110301ly1g2e8km4vajj21hk0t4b0x.jpg)

## 5.更换主题

本次安装使用的主题为[yilia](https://github.com/litten/hexo-theme-yilia)。

进入博客目录下的theme目录，将主题克隆到本地

```shell
$ cd theme
$ git clone https://github.com/litten/hexo-theme-yilia.git ./yilia
```

然后将_config.yml中的的theme值改为yilia，然后重启服务即可

![修改主题后的博客](http://ww1.sinaimg.cn/large/69110301ly1g2e8qjm0ccj21020k8n55.jpg)

## 6.使用Github Pages服务托管博客

这里请参考github官方[Github Pages发布源配置文档](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages)创建承载博客的仓库

## 7.部署站点到Github Pages

安装git部署功能:

```shell
$ npm install hexo-deployer-git --save
```

根据[官方文档](https://hexo.io/zh-cn/docs/deployment)配置好_config.yml

然后一键部署到github:

```shell
#其实hexo deploy -g可以完成下面两句的命令
$ hexo generate
$ hexo deploy
```

成功后，博客就出来了:

![博客已经部署到Github Pages](http://ww1.sinaimg.cn/large/69110301ly1g2e9kqk5x5j21020k810s.jpg)

**这里需要注意的是每次对本地代码做了变动都需要先执行generate在deploy**

## 8.发布文章

这里可以参考Hexo提供的[文档](https://hexo.io/zh-cn/docs/writing)进行操作。基本步骤如下:

```shell
#1.生成文章，在source/_posts目录下会出现HelloWorld.md文件
$ hexo new post HelloWorld
#2.编辑HelloWorld.md
...
#3.文章编辑完成后，生成站点内容并提交文章
hexo deploy -g
```

经过上述步骤，新文章就会被推送到！