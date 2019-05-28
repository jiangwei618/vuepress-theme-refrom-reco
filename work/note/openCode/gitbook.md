# 安装
## node.js安装

&emsp;打开nodejs官网：https://nodejs.org/en/

&emsp;下载稳定版本(LTS)的node，下载完成之后通过如下命令检查：

```
node -v   // 检查node的版本，由于nodejsy已经集成了npm，所以安装了node，npm也一并安装好啦
npm -v    // 检查npm的版本
```

&emsp;**如果是使用下载包安装node.js 则需要创建软链接**
```
ln -s /usr/local/mine/node-v8.11.3-linux-x64/bin/node /usr/local/bin/node
ln -s /usr/local/mine/node-v8.11.3-linux-x64/bin/npm /usr/local/bin/npm
```

##gitbook-cli安装

```
npm install gitbook-cli -g  //mac && windows //gitbook-cli不同于gitbook，而是其一个命令行工具
gitbook -V  // 注意V为大写，不识别小写v
```
# 常用命令

| 命令                                 | 解释                                          |
| ------------------------------------ | --------------------------------------------- |
| gitbook build                        | 构建                                          |
| gitbook build                        | 生成静态网页                                  |
| gitbook build --gitbook=2.0.1        | 指生成时指定 gitbook 的版本, 本地没有会先下载 |
| gitbook build ./ --log=debug --debug | 获取更好的错误消息（使用堆栈跟踪）            |
| gitbook fetch beta                   | 下载并安装其他版本的 GitBook                  |
| gitbook help                         | 列出 gitbook 所有的命令                       |
| gitbook init                         | 初始化                                        |
| gitbook init ./directory             | 将书籍创建到一个新目录中                      |
| gitbook install                      | 安装插件                                      |
| gitbook ls-remote                    | 会列举可以下载的版本                          |
| gitbook serve                        | 运行一个 web 服务                             |
| gitbook serve --port                 | 指定端口                                      |
| gitbook update                       | 更新到 gitbook 的最新版本                     |


# 全局配置

1. title

&emsp;设置书本的标题
"title" : "Gitbook Use"

2. author

&emsp;作者的相关信息
"author" : "mingyue"

3. description

&emsp;本书的简单描述

`"description" : "记录Gitbook的配置和一些插件的使用"`

4. language

&emsp;Gitbook使用的语言, 版本2.6.4中可选的语言如下：

`en, ar, bn, cs, de, en, es, fa, fi, fr, he, it, ja, ko, no, pl, pt, ro, ru, sv, uk, vi, zh-hans, zh-tw`

&emsp;例如，配置使用简体中文

`"language" : "zh-hans"`

5. links

&emsp;在左侧导航栏添加链接信息
```
"links" : {
    "sidebar" : {
        "Home" : "https://www.baidu.com"
    }
}
```

6. styles
&emsp;自定义页面样式， 默认情况下各generator对应的css文件

```
"styles": {
    "website": "styles/website.css",
    "ebook": "styles/ebook.css",
    "pdf": "styles/pdf.css",
    "mobi": "styles/mobi.css",
    "epub": "styles/epub.css"
}
```

&emsp;例如使`<h1> <h2>`标签有下边框， 可以在website.css中设置
```
h1 , h2{
    border-bottom: 1px solid #EFEAEA;
}
```
# 插件
## 插件配置

### 配置使用的插件

```
"plugins": [
    "-search",
    "back-to-top-button",
    "expandable-chapters-small",
    "insert-logo"
]
```
&emsp;其中"-search"中的 - 符号代表去除默认自带的插件

&emsp;Gitbook默认自带有5个插件：

```
highlight： 代码高亮
search： 导航栏查询功能（不支持中文）
sharing：右上角分享功能
font-settings：字体设置（最上方的"A"符号）
livereload：为GitBook实时重新加载
```

### 插件属性配置pluginsConfig
&emsp;配置插件的属性,例如配置insert-logo的属性：
```
  "pluginsConfig": {
    "insert-logo": {
      "url": "images/logo.png",
      "style": "background: none; max-height: 30px; min-height: 30px"
    }
  }
```

#生成pdf

&emsp;1. 安装 Calibre

```
apt install calibre

```
&emsp;2. 配置book.json

```
{
    "title": "Cloudroom SDK Refference",
    "description": "云屋视频SDK参考文档",
    "author": "HeDonghai",
    "language": "zh-hans",
    "styles": {
        "website": "style.css"
    },
    "pluginsConfig": {
        "fontSettings": {
            "theme": "white",
            "family": "msyh",
            "size": 2
          }
    },
    "pdf": {
        "toc": true,
        "pageNumbers": true,
        "fontSize": 18,
        "paperSize": "a3",
        "margin": {
          "right": 30,
          "left": 30,
          "top": 30,
          "bottom": 50
        }
      }
}

```
&emsp;3. 安装ebook-convert

```
  npm install ebook-convert -g

```
&emsp;4. 生成pdf
```
gitbook pdf

```
&emsp;5. pdf文档内中文不显示或中文乱码  
原因是中文字体未支持，可手动配置支持，操作如下： 
1. 在插件配置中使用”yahei”(雅黑字体)并配置fontSettings  
2. 手动从windows系统的Fonts目录下复制c/windows/Fonts/msyh.ttc文件或msyh.ttf文件上传到Linux的/usr/share/fonts/truetype目录下  
3. 重新生成pdf即可  