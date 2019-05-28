# 常用插件
&emsp;用法：在book.json中添加"plugins"和"pluginConfig"字段。然后执行gitbook install，或者使用NPM安装npm install gitbook-plugin-插件名，也可以从源码GitHub地址中下载，放到node_modules文件夹里（GitHub地址在进入插件地址右侧的GitHub链接）

常用插件 | 作用 | 
---------|----------|
 back-to-top-button |  回到顶部 | 
 chapter-fold |  导航目录折叠，支持多层目录，点击导航栏的标题名就可以实现折叠扩展。（最好用） | 
 expandable-chapters-small | 导航目录 | 
 expandable-chapters  |  导航 | 
 code|  代码添加行号&复制按钮（可选) | 
 todo | 待做项 | 
 advanced-emoji|  支持emoji表情 |  
 github |  在右上角添加github图标 | 
 search-pro | 中文搜索，需要去掉默认插件："-lunr",  "-search", | 
emphasize| 为文字加上底色|
splitter| 侧边栏宽度可调节|
sharing-plus|分享
tbfed-pagefooter| 页面添加页脚（简单的）添加页脚，版权信息
page-copyright| 页面页脚版权（内容多）
sectionx | 将页面分块显示.用于将页面分成多个部分
hide-element | 隐藏元素
flexible-alerts  |警报；这个GitBook插件将块引用转换为漂亮的警报。可以在全局和警报特定级别配置外观
 auto-scroll-table |表格滚动条。为避免表格过宽，增加滚动条
  popup| 弹出大图。单击图片，在新页面查看大图。
  lightbox | 单击查看图片。点击图片可显示，大小不变
  click-reveal| 点击显示。默认隐藏，点击可显示。
  custom-favicon| 修改标题栏图标
 accordion |折叠模块

# 插件详细介绍

## code
&emsp;代码添加行号&复制按钮（可选) ，如果想去掉复制按钮，在book.json的插件配置块更新：
```
{
    "plugins" : [ 
            "code" 
     ],
    "pluginsConfig": {
      "code": {
        "copyButtons": false
      }
    }
}

```

## todo  待做项☑

&emsp;添加 Todo 功能。默认的 checkbox 会向右偏移 2em，如果不希望偏移，可以在 website.css 里加上下面的代码:
```
input[type=checkbox]{
    margin-left: -2em;
}

```
```
使用示例：
*   [ ]  write some articles
*   [x]  drink a cup of tea

```
insert-logo  插入logo将logo插入到导航栏上方中

```
{
    "plugins": [ "insert-logo" ]
    "pluginsConfig": {
      "insert-logo": {
        "url": "images/logo.png",
        "style": "background: none; max-height: 30px; min-height: 30px"
      }
    }
}

```

## github 在右上角添加github图标

```
{
    "plugins": [ 
        "github" 
    ],
    "pluginsConfig": {
        "github": {
            "url": "https://github.com/zhangjikai"
        }
    }
}
```
## emphasize 为文字加上底色

{
    "plugins": [
        "emphasize"
    ]
}

然后在markdown / asciidoc内容中，使用以下内容突出显示一些文本：
```

  This text is {% em %}highlighted !{% endem %}
  This text is {% em %}highlighted with **markdown**!{% endem %}
  This text is {% em type="green" %}highlighted in green!{% endem %}
  This text is {% em type="red" %}highlighted in red!{% endem %}
  This text is {% em color="#ff0000" %}highlighted with a custom color!{% endem %}

```

## tbfed-pagefooter 页面添加页脚（简单的）添加页脚，版权信息

```
{
    "plugins": [
       "tbfed-pagefooter"
    ],
    "pluginsConfig": {
        "tbfed-pagefooter": {
            "copyright":"Copyright &copy xxxx.com 2017",
            "modify_label": "该文件修订时间：",
            "modify_format": "YYYY-MM-DD HH:mm:ss"
        }
    }
}

```

## page-copyright 页面页脚版权（内容多）

```
{
    "plugins" : ["page-copyright"],
    "pluginsConfig" : {
        "page-copyright": {
          "description": "modified at",
          "signature": "你的签名",
          "wisdom": "Designer, Frontend Developer & overall web enthusiast",
          "format": "YYYY-MM-dd hh:mm:ss",
          "copyright": "Copyright &#169; 你的名字",
          "timeColor": "#666",
          "copyrightColor": "#666",
          "utcOffset": "8",
          "style": "normal",
          "noPowered": false,
        }
    }
}

```

## sectionx  将页面分块显示.用于将页面分成多个部分，并添加按钮以允许读者控制每个部分的可见性。
### 插件配置

| 命令          | 解释                                                                                                                                                           |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| data-collapse | 表示默认情况下是否打开（但仍然可见）该部分                                                                                                                     |
| data-id       | 对按钮控制很有用（在下一节中讨论）                                                                                                                             |
| data-id       | 对按钮控制很有用（在下一节中讨论）                                                                                                                             |
| data-nopdf    | 该部分是否将隐藏在 pdf 导出中。true：面板不会显示在.pdf 或.epub 中。                                                                                           |
| data-show     | true：默认情况下，面板内容对用户可见，面板标题可以单击。 false：默认情况下，面板内容对用户隐藏，面板标题不可点击，只能通过添加自定义按钮查看（在下一节中讨论） |
| data-show     | true：默认情况下，面板内容对用户可见，面板标题可以单击。 false：默认情况下，面板内容对用户隐藏，面板标题不可点击，只能通过添加自定义按钮查看（在下一节中讨论） |
| data-show     | true：默认情况下，面板内容对用户可见，面板标题可以单击。 false：默认情况下，面板内容对用户隐藏，面板标题不可点击，只能通过添加自定义按钮查看（在下一节中讨论） |
| data-title    | 该部分的标题，它将显示为 bootstrap 面板的标题（大小为 h2）。请注意，您不能使用"标题中的字符，请&quot;改用。                                                    |
| data-title    | 该部分的标题，它将显示为 bootstrap 面板的标题（大小为 h2）。请注意，您不能使用"标题中的字符，请&quot;改用。                                                    |
 ancre-navigation|  悬浮目录和回到顶部
klipse |嵌入类似IDE的功能。嵌入一块功能，可在代码段中实时交互，即（输入代码 > 执行结果                                            |

### 按钮配置
&emsp;通过在GitBook中添加内联HTML，以下代码可以添加一个按钮，以允许您查看或隐藏其他部分。
简单来说，就是在【使用1】的内容部分添加一个按钮：

`<button class="section" target="section1" show="显示下一部分" hide="隐藏下一部分"></button>`

| 参数   | 说明                                                       |
| ------ | ---------------------------------------------------------- |
| class  | 该按钮必须属于类“section”。//这里就是用到 1 部分的 section |
| class  | 该按钮必须属于类“section”。//这里就是用到 1 部分的 section |
| hide   | 目标部分可见时按钮上的文本。                               |
| show   | 隐藏目标部分时按钮上的文本。                               |
| target | 当按下时，将切换 id 为 target 的部分。                     |
| target | 当按下时，将切换 id 为 target 的部分。                     |

### markdown中示例代码：

<button class="section" target="section2" show="显示模块2" hide="隐藏模块2"></button>
\<!--sec data-title="模块2" data-id="section2" data-show=true ces-->
\<!--endsec-->`

混合使用
将第2节的button块添加到第1节的内容部分
markdown中示例代码：

`\<!--sec data-title="标题1" data-id="section0" data-show=true ces-->
data
\<button class="section" target="section1" show="显示下一部分" hide="隐藏下一部分"></button>
\<!--endsec-->
\<!--sec data-title="标题2" data-id="section1" data-show=true ces-->
\<!--endsec-->`

 page-treeview 生成页内目录，不需要插入标签，能支持到6级目录，安装可用

```
{
    "plugins": ["page-treeview"]
}

非必要的配置项：
{
    "plugins": [
        "page-treeview"
    ],
    "pluginsConfig": {
        "page-treeview": {
            "copyright": "Copyright &#169; aleen42",
            "minHeaderCount": "2",
            "minHeaderDeep": "2"
        }
    }
}

```

## simple-page-toc
&emsp;生成本页目录，需要在文章中插入标签，支持1-3级目录；页面顶端生成。另外 GitBook 在处理重复的标题时有些问题，所以尽量不适用重复的标题。

```
{
    "plugins" : [
        "simple-page-toc"
    ],
    "pluginsConfig": {
        "simple-page-toc": {
            "maxDepth": 3,
            "skipFirstH1": true
        }
    }
}

```


| Column A    | Column B                         |
| ----------- | -------------------------------- |
| "maxDepth"  | 使用深度最多为 maxdepth 的标题。 |
| skipFirstH1 | 排除文件中的第一个 h1 级标题。   |

使用方法: 在需要生成目录的地方用下面的标签括起来，全文都生成的话就在首尾添加

\<!-- toc -->内容部分<!-- endtoc -->

## page-toc-button 悬浮目录

```
{
    "plugins" : [ 
        "page-toc-button" 
    ],
    "pluginsConfig": {
        "page-toc-button": {
            "maxTocDepth": 2,
            "minTocSize": 2
           }
    }
}

```

##  donate  打赏插件
```
{
    "plugins": [
        "donate"
    ],
    "pluginsConfig": {
        "donate": {
            "wechat": "微信收款的二维码URL",
            "alipay": "支付宝收款的二维码URL",
            "title": "",
            "button": "赏",
            "alipayText": "支付宝打赏",
            "wechatText": "微信打赏"
        }
    }
}

```
## change_girls  可自动切换的背景
```
{
    "plugins":["change_girls"],
    "pluginsConfig": {
        "change_girls" : {
            "time" : 10,
            "urls" : [
                "girlUrl1", "girlUrl2",...""
            ]
        }
    }
}

```
## alerts 警报
这个GitBook插件将块引用转换为漂亮的警报。
插件地址
在book.json中添加以下内容。然后执行gitbook install，或者使用NPM安装npm install gitbook-plugin-flexible-alerts
{
    "plugins": ["alerts"]
}

用法样式：
信息样式
> **[info] For info**
>
> Use this for infomation messages.

警告造型
> **[warning] For warning**
>
> Use this for warning messages.

危险造型
> **[danger] For danger**
>
> Use this for danger messages.

成功造型
> **[success] For success**
>
> Use this for success messages.

###  accordion 折叠模块。这个插件名叫手风琴，可以实现将内容隐藏起来，外部显示模块标题和显示箭头，点击箭头可显示里面的内容。
```
用法：
编辑内容，用下面的标签括起来。
%accordion%模块标题%accordion%
内容部分
%/accordion%

```