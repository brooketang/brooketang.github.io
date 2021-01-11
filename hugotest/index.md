# Windows下hugo小试


因为用Go，所以预料可以省很多事，要比Hexo省心，不懂Ruby,Jekyll也就无爱了。

#### 下载 
[[Github]https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases) 直接`hugo_0.xx.0_Windows-64bit.zip`
`hugo.exe`去掉`.exe` 放在%PATH里，Git Bash也能正常调用。

#### 运行 
```shell
hugo new site ./blog    #创建文件夹
cd cd blog/themes       #切换到主题文件夹
git clone https://github.com/dillonzq/LoveIt #https://themes.gohugo.io下有更多主题选择
cd ..
cp themes/LoveIt/exampleSite/config.toml ./ #修改config.toml信息为你自己博客信息
hugo new posts/first.md #编写文章
```

#### 调试
```shell
hugo -D #直接生成静态文件
hugo server -D  #生成静态文件并本地部署调试
```

#### 推送
```shell
cd blog/public
git init
#要预先建个名为xxx.github.io的respository
git remote add origin https://github.com/xxx/xxx.github.io.git #xxxGithub用户名
git add -A
git commit -m "first commit"
git push -u origin master
```
#### 其它
###### 推送出错
```shell
#本地和远端不同步时，从远端更新本地文件,远程的和本地的合并
git merge origin/master
#本地文件删除后标记'del'后git push删除远端文件
git commit -m 'del'
#强制git push
git push -f origin master
```
###### CDN加速
```code
https://cdn.jsdelivr.net/gh/xxx/xxx.github.io/*

CloudFlare用cname转发，先灰云，后黄云
```
###### 乱七八糟
* hugo new posts/*.md 无内容会报错
* `config.toml` 中 `enableGitInfo = false`
