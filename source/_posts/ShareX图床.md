---
title: Markdown写作必备:ShareX工作流+图床
date: 2020-01-01 17:43:26
tags: 
	- Blog
	- 图床
reward: true
---

Markdown写作一定会碰到的问题就是图的问题，我自己的解决方案是ShareX + SM.MS图床。

ShareX提供了截图后上传，以及上传后自动复制网址到剪贴板，将这两个动作连贯起来，体验还是比较舒服的。

### ShareX

ShareX在[官网](https://getsharex.com/)下载安装即可。ShareX是开源的，源码托管在Github:[ShareX](https://github.com/ShareX/ShareX)

![ShareX 官网](http://suo.im/5INXtF)



### SM.MS图床

当时从V2EX上看到这个图床，目前来看还是可用的。

在ShareX里点击: 上传至... -> 自定义上传目标...

然后按图设置:

请求Tab页:

![ShareX配置SM.MS图床](http://suo.im/6kCk1X)

响应Tab页:

![ShareX设置SM.MS图床](http://suo.im/6s8w2Q)

配置完成后可以测试一下。

或者可以将如下配置保存成文件后导入:

```json
{
  "Version": "12.4.1",
  "Name": "SM.MS图床",
  "DestinationType": "ImageUploader",
  "RequestMethod": "POST",
  "RequestURL": "https://sm.ms/api/upload",
  "Body": "MultipartFormData",
  "Arguments": {
    "ssl": "false",
    "format": "json"
  },
  "FileFormName": "smfile",
  "URL": "$json:data.url$",
  "DeletionURL": "$json:data.delete$"
}
```



然后在ShareX配置截图后上传和上传后复制网址:

![截图后动作](http://suo.im/5XZxxd)

![上传后动作](http://suo.im/6jSdnu)



### 短连接

从以上截图还看到，其实我还配置了短连接，用的是suomi，有兴趣的同学可以自己配置一下，这里提供suomi的配置json

```json
{
  "Version": "13.0.1",
  "Name": "suomi短网址",
  "DestinationType": "URLShortener",
  "RequestMethod": "GET",
  "RequestURL": "http://suo.im/api.htm",
  "Parameters": {
    "url": "$input$",
    "key": "!!!your key!!!",
    "expireType": "6"
  }
}
```

suomi是需要注册获取key的，上面配置隐去了我的key，大家替换成自己的key即可。



### 其他

其实还想过看能不能用github当图床，想着是自己写个工程，跑在本地或者云上，然后提供接口，调用接口上传图片到github或者gitee。

目前还只是想法，暂未试试。