README



### 说明

该仓库用于存放我的github pages博客写作工程，目前采用[Hexo](http://hexo.io/)博客框架配合[Yilia主题](https://github.com/litten/hexo-theme-yilia)进行写作。



### 如何使用

1. 先在个人电脑上找个地方执行如下命令:

    ```shell
    hexo init ./MyBlog
    ```

2. 克隆本仓库，并用本仓库内容替换MyBlog下的内容

3. 执行如下命令，让yilia主题的搜索功能生效

   ```shell
   npm i hexo-generator-json-content --save
   ```

4. 删除目录下的source/_posts/hello-world.md，该文件是hexo init命令留下的默认文章。

5. 提交变化到GithubPage需要安装如下组件, 否则提交时会提示找不到git

   ```shell
   npm i hexo-developer-git --save
   ```



经过以上几步，本地环境已经准备好，具体使用请参考这篇文章:

[一篇文章搞定Github Pages托管Hexo博客](http://nemax.github.io/2019/04/25/Hexo-install/)



###感谢

感谢Hexo ： [http://hexo.io/]( http://hexo.io/)

感谢Litten进行主题开发: [http://litten.me/](http://litten.me/)

