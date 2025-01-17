# 这大概是一篇文档

Github: [<i class="fas fa-link"></i> Renovamen/jekyll-theme-gungnir](https://github.com/Renovamen/jekyll-theme-gungnir){:target="_blank"}

在 [Huxpro/huxpro.github.io](https://github.com/Huxpro/huxpro.github.io){:target="_blank"} 的基础上瞎改的的主题，同时~~照搬~~借鉴了很多其他主题的代码和设计，包括但不限于 [mashirozx/Sakura](https://github.com/mashirozx/Sakura/){:target="_blank"}、[kitian616/jekyll-TeXt-theme](https://github.com/kitian616/jekyll-TeXt-theme){:target="_blank"}、[Fechin/hexo-theme-diaspora](https://github.com/Fechin/hexo-theme-diaspora){:target="_blank"}、[liuzc/LeaveIt](https://github.com/liuzc/LeaveIt){:target="_blank"} 等（这么看来似乎也没多少东西是我自己写的了，逃）。

**Gungnir**，冈格尼尔，北欧神话中主神奥丁使用的用世界树树枝做成的武器，和本主题并没有什么关系但我就是用了这个名字。


![theme-gungnir](../img/docs/gungnir.jpg)


## 安装

从 GitHub 克隆项目：

```bash
git clone https://github.com/Renovamen/jekyll-theme-gungnir.git
cd jekyll-theme-gungnir
```

本地运行主题需要参考[这里](https://jekyllrb.com/docs/installation/){:target="_blank"}安装 Ruby 和 Jekyll。然后安装依赖包：

```bash
bundle config set path 'vendor/bundle'
bundle install
```

然后即可本地预览：

```bash
bundle exec jekyll serve --watch
```

如果想要改动代码，你可能需要 [Node.js](https://nodejs.org/en/)，并安装 [Grunt](https://gruntjs.com/){:target="_blank"}（用于压缩 js 文件）：

```bash
npm install
```

然后：

```bash
npm run dev
```


## 配置

以下配置都在 `_config.yml` 中进行。
{:.info}


### 网站配置
```yaml
title: Renovamen # 标题
SEOTitle: Renovamen's blog # SEO 标题
description: Hmm, interesting blog. # 描述
keyword: "blog, personal website" # 关键词
url: "https://renovamen.ink" # 域名
baseurl: "" # 根路径。比如网站地址为 'https://renovamen.ink/blog'，则该项应为 '/blog'
avatar: "img/header-avatar.png" # 首页头像路径
```

### 主题风格
```yaml
theme_style: 
  highlight:  # 代码高亮主题
  alert:  # 提示风格
  post_preview: # 首页文章列表显示风格
```

#### 代码高亮

代码高亮渲染用 [Highlight.js](https://highlightjs.org/){:target="_blank"} 代替了 [Rouge](http://rouge.jneen.net/){:target="_blank"}。默认的代码高亮大概长这样：

```python
import food

class Dragon:
    def __init__(self, happiness):
        self.happiness = happiness
    def code(self):
        """ just code """
        self.happiness -= 60
    def eat(self, n)
        # just eat
        self.happiness += n * food.size

me = Dragon(100)

while True:
    me.code()
    me.eat(10)
```

点击显示编程语言的标签可以使代码块全屏，还有光标所在行高亮效果。如果你发现这两点跟 [Sakura](https://2heng.xin/theme-sakura/){:target="_blank"} 主题很像，那么没错这部分的代码就是从它那搬过来的...

代码高亮的默认主题为 `dark`，还有一个 `light` 主题可选：

```yaml
highlight: # "dark" (default), "light"
```

代码高亮的样式文件在 [`_sass/highlight`](https://github.com/Renovamen/jekyll-theme-gungnir/tree/master/_sass/highlight){:target="_blank"} 目录下，可以自行调整样式，或者直接引用 highlight.js 自带的[一堆主题](https://github.com/highlightjs/highlight.js/tree/master/src/styles){:target="_blank"}。


#### 提示
支持在 Markdown 中使用提示样式以呈现一些警告，[这里](#提示-1)是使用方法。指定提示风格：
```yaml
alert:  # "flat" (default), "modern"
```

默认为 `flat`，长[这样](#配置)。`modern` 风格长这样：

![alert-modern](../img/docs/alert-modern.png)


#### 首页文章列表

首页文章列表是否显示特征图片，`image` 为显示（默认），`text` 为不显示：

```yaml
post_preview: # "image" (default), "text"
```

`image`：
![preview-image](../img/docs/preview-image.jpg)


`text`：
![preview-text](../img/docs/preview-text.jpg)


### 社交链接

```yaml
sns:
  github_username: # Github
  weibo_username: # 微博
  zhihu_username: # 知乎
  twitter_username: # 推特  
  facebook_username: # Facebook
  linkedin_username:  # 领英
  email_address: # 邮件地址
```
填入用户名或用户 ID 后，社交链接会出现在首页封面和 About 页上。


### 导航菜单

一级菜单的配置如下：

```yaml
menus:
  - title: Home
    font: fab fa-fort-awesome
    url: /
  - title: Archive
    font: fas fa-archive
    url: /archive/
```

需要填入每个页面的名称、路径和图标。图标库使用了 [Font Awesome](https://fontawesome.com){:target="_blank"}，可以在[这里](https://fontawesome.com/icons){:target="_blank"}查找图标。

如果要添加**二级菜单**，则需要在需要添加二级菜单的一级菜单下添加 `submenus` 关键字，然后在 `submenus` 下填入每个二级菜单页面的名称、路径和图标：

```yaml
menus:
  - title: About
    font: fas fa-paw
    submenus:
      - title: Me
        font: fas fa-user-astronaut
        url: /about/
      - title: Theme
        font: fas fa-meteor
        url: /theme/
```

### 评论

```yaml
comment: 
  provider: # false (default), "disqus", "gitalk", "valine"
```

支持三种评论系统：Disqus、Gitalk 和 Valine。需要在 `provider` 中填入想要启用的评论系统的名字，如果不想用启用评论就填 `false` 或不填。

#### Disqus

在 [Disqus](https://disqus.com/){:target="_blank"} 申请一个自己网站的 Disqus，然后把 shortname 填入 `disqus_username`：

```yaml
comment: 
  provider: disqus
  disqus_username: # Disqus shortname
```

#### Gitalk

注册一个 [Github Application](https://github.com/settings/applications/new){:target="_blank"} 并搞到 Client ID 和 Client Secret，然后填入对应信息：

```yaml
comment: 
  provider: gitalk
  gitalk:
    clientID: # Github Application Client ID
    clientSecret: # Github Application Client Secret
    repo: # 用来放评论的 Github 仓库
    owner: # 上述 Github 仓库的拥有者 ID
    admin: 
      - 管理员1
      - 管理员2
      - ...
```

可以参考 [Gitalk 文档](https://github.com/gitalk/gitalk){:target="_blank"}。

#### Valine

按照 [Valine 文档](https://valine.js.org/){:target="_blank"} 在 [LeanCloud](https://www.leancloud.cn/){:target="_blank"} 注册应用，然后填入 App ID 和 App Key：

```yaml
comment: 
  provider: valine
  valine:
    appID: # LeanCloud App ID
    appKey: # LeanCloud App Key
```

### 站点统计

支持谷歌统计和百度统计。

#### 百度统计

搞到[百度统计](https://tongji.baidu.com/web/welcome/login){:target="_blank"}的统计代码并填入对应位置：

```yaml
analytics:
  ba_track_id: # 百度统计代码
```

#### 谷歌统计

搞到[谷歌统计](https://www.google.com/analytics/){:target="_blank"}的跟踪 ID 并填入对应位置：

```yaml
analytics:
  ga_track_id: 'G-ZYM02DSEHS' # 谷歌统计跟踪 ID
```

### CDN 源

```yaml
cdn: # "jsdelivr" (default), "bootcdn", "unpkg", "cdnjs"
```

默认使用 [jsDelivr](https://www.jsdelivr.com/){:target="_blank"} 作为所有引用的开源库的 CDN 源，也可以把 CDN 源配置为 [BootCDN](https://www.bootcdn.cn/){:target="_blank"}、[unpkg](https://unpkg.com/){:target="_blank"} 或 [cdnjs](https://cdnjs.com/){:target="_blank"}。可以在 `_data/cdn.yml` 中看到所有 CDN 地址。


### Markdown 附加功能

```yaml
math: 
    enable: # 是否对所有文章启用公式渲染
            # false (default), true 
    engine: # 公式渲染引擎
            # "katex" (default), "mathjax"
chart: # 是否启用 Chart.js：false (defaule), true
mermaid: # 是否启用 mermaid：false (default), true
emoji-plus: # 是否启用附加表情：false (default), true
```

[这里](#markdown-附加功能-1)是具体说明。



### 一言

```yaml
hitokoto: true # default: false
```

将 `hitokoto` 设为 `true` 可以开启首页的[一言](https://hitokoto.cn/){:target="_blank"}气泡，将鼠标悬浮在头像上气泡就会显示出来：

![Hitokoto Bubble](../img/docs/hitokoto-bubble.jpg)



## 页面

### 首页

在 `index.html` 的 Front-matter 中设置：

```yaml
description: # 想在首页显示的一句话
header-img:
  - url: # 首页封面图路径1
    mask: # 封面图1的遮罩（可选），格式：rgba(40, 57, 101, .4)
  - url: # 首页封面图路径2
    mask: # 封面图1的遮罩（可选）
```

在首页点击封面图左右两边的按钮可以在多图片之间进行切换。需要按上述格式在 `header-img` 下填入每张封面图的路径和遮罩的 RGB 数值（可选）。遮罩是指在封面图上盖一层半透明的颜色，如果图片比较复杂导致文字显示得不够清楚，可以考虑加个遮罩。




### About

参考一下本站 [About 页面](/about){:target="_blank"} 和它的 [Front-matter](https://github.com/Renovamen/jekyll-theme-gungnir/blob/master/about.html){:target="_blank"} 大概就知道怎么改了？


### Links

参考一下本站 [Links 页面](/links){:target="_blank"} 和它的 [Front-matter](https://github.com/Renovamen/jekyll-theme-gungnir/blob/master/links.html){:target="_blank"} 大概就知道怎么改了？（复读 *1）

如果没有指定某个链接的头像，那么会显示默认头像（`img/links/default.jpg`）。

如果想在该页面开启评论，需要在 `_config.yml` 中启用评论并在该页的 Front-matter 中设 `comment: true`。


## 内容

### 文章

把要发布的文章放在 `_posts/` 文件夹中，文件名格式为 `年-月-日-标题.md`，然后配置其 YAML Front-matter：

```yaml
---
layout: post
title: # 文章标题
subtitle: # 副标题
author: # 作者名称，默认为网站名称
header-img: # 文章封面图
header-mask: # 封面图遮罩，格式：rgba(40, 57, 101, .4)
header-style: text # 如果不想该文章显示封面图，就需要加这一项
catalog: # 是否显示目录：false (default), true
math: # 是否开启数学公式渲染
tags: # 标签
  - 标签1
  - 标签2
  - ...
---
```

其中 `header-img` 会同时显示在[首页](#首页文章列表)和文章页。`math` 的配置可以参考[这里](#数学公式渲染)。



### Markdown 附加功能

#### 数学公式渲染

支持使用 [Mathjax](https://github.com/mathjax/MathJax){:target="_blank"} 或 [Katex](https://github.com/KaTeX/KaTeX){:target="_blank"} 来在文章中渲染数学公式。

Katex 渲染速度快于 Mathjax（可以参考[这里](https://katex.org/){:target="_blank"}），但支持的 Tex 公式少于 Mathjax（[这里](https://katex.org/docs/supported.html){:target="_blank"}是 Katex 支持的公式列表）。

如果 `_config.yml` 中 `math.enable: false`，则只有 Front-matter 中添加了 `mathjax: true` 的文章才会开启公式渲染：

```yaml
---
layout: post
mathjax: true
---
```

否则所有文章（包括 `post` 和 `keynote`）中都会开启此功能。

示例：

Inline math: $$ E = mc^2 $$

Display math:

$$
i\hbar\frac{\partial \psi}{\partial t} = \frac{-\hbar^2}{2m} ( \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + \frac{\partial^2}{\partial z^2} ) \psi + V \psi.
$$


```plaintext
$$ E = mc^2 $$

$$
i \hbar \frac{\partial \psi}{\partial t}
= \frac{-\hbar^2}{2m} ( \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + \frac{\partial^2}{\partial z^2} ) \psi + V \psi
$$
```

#### 图表

##### Chart.js

使用了 [Chart.js](https://github.com/chartjs/Chart.js){:target="_blank"} 以在文章中加入可交互的图表。可以参考 [Chart.js 文档](https://www.chartjs.org/docs/latest/){:target="_blank"}来创建表格。

示例：


```chart
{
    "type": "bar",
    "data": {
        "labels": ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        "datasets": [{
            "label": "# of Votes",
            "data": [12, 19, 3, 5, 2, 3],
            "backgroundColor": [
                "rgba(255, 99, 132, 0.2)",
                "rgba(54, 162, 235, 0.2)",
                "rgba(255, 206, 86, 0.2)",
                "rgba(75, 192, 192, 0.2)",
                "rgba(153, 102, 255, 0.2)",
                "rgba(255, 159, 64, 0.2)"
            ],
            "borderColor": [
                "rgba(255, 99, 132, 1)",
                "rgba(54, 162, 235, 1)",
                "rgba(255, 206, 86, 1)",
                "rgba(75, 192, 192, 1)",
                "rgba(153, 102, 255, 1)",
                "rgba(255, 159, 64, 1)"
            ],
            "borderWidth": 1
        }]
    },
    "options": {
        "scales": {
            "yAxes": [{
                "ticks": {
                    "beginAtZero": true
                }
            }]
        }
    }
}
```

<pre><code class="json">```chart
{
    "type": "bar",
    "data": {
        "labels": ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        "datasets": [{
            "label": "# of Votes",
            "data": [12, 19, 3, 5, 2, 3],
            "backgroundColor": [
                "rgba(255, 99, 132, 0.2)",
                "rgba(54, 162, 235, 0.2)",
                "rgba(255, 206, 86, 0.2)",
                "rgba(75, 192, 192, 0.2)",
                "rgba(153, 102, 255, 0.2)",
                "rgba(255, 159, 64, 0.2)"
            ],
            "borderColor": [
                "rgba(255, 99, 132, 1)",
                "rgba(54, 162, 235, 1)",
                "rgba(255, 206, 86, 1)",
                "rgba(75, 192, 192, 1)",
                "rgba(153, 102, 255, 1)",
                "rgba(255, 159, 64, 1)"
            ],
            "borderWidth": 1
        }]
    },
    "options": {
        "scales": {
            "yAxes": [{
                "ticks": {
                    "beginAtZero": true
                }
            }]
        }
    }
}
```
</code></pre>

`注意`{:.warning}：`json` 中的 `key` 值一定要加**引号**，否则会渲染出错。


##### mermaid

使用了 [mermaid](https://github.com/knsv/mermaid){:target="_blank"} 以在文章中加入流程图、状态图、时序图、甘特图等。可以参考 [mermaid 文档](https://mermaid-js.github.io/mermaid/){:target="_blank"}来创建图。

示例：

```mermaid
classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
```

    ```mermaid
    classDiagram
        Animal <|-- Duck
        Animal <|-- Fish
        Animal <|-- Zebra
        Animal : +int age
        Animal : +String gender
        Animal: +isMammal()
        Animal: +mate()
        class Duck{
            +String beakColor
            +swim()
            +quack()
        }
        class Fish{
            -int sizeInFeet
            -canEat()
        }
        class Zebra{
            +bool is_wild
            +run()
        }
    ```

#### 标签

`消息标签`{:.info}

```markdown
`消息标签`{:.info}
```

`成功标签`{:.success}

```markdown
`成功标签`{:.success}
```

`警告标签`{:.warning}

```markdown
`警告标签`{:.warning}
```

`错误标签`{:.error}

```markdown
`错误标签`{:.error}
```

#### 提示

消息提示文案
{:.info}

```markdown
消息提示文案
{:.info}
```

成功提示文案
{:.success}

```markdown
成功提示文案
{:.success}
```

警告提示文案
{:.warning}

```markdown
警告提示文案
{:.warning}
```

错误提示文案
{:.error}

```markdown
错误提示文案
{:.error}
```

#### 表情
##### emoji

使用了 [jemoji](https://github.com/jekyll/jemoji){:target="_blank"} 插件以在文章中插入 emoji，需要手动安装这个插件：

```bash
gem install jemoji
```

从[这里](https://pages.github.com/versions/){:target="_blank"}可以看到 Github Pages 上自带 jemoji 插件。[这里](https://www.webfx.com/tools/emoji-cheat-sheet/){:target="_blank"}是所有 emoji 的代码。

示例：

:smile: :smirk: :racehorse: :wolf:

```markdown
:smile: :smirk: :racehorse: :wolf:
```

##### 附加表情

也可以在文章中插入其他表情，目前支持 Bilibili 的小电视表情 `斜眼笑`{:.emoji-plus}（效果出乎意料的好）。

示例：

`斜眼笑`{:.emoji-plus} `doge`{:.emoji-plus} `白眼`{:.emoji-plus}

```markdown
`斜眼笑`{:.emoji-plus} `doge`{:.emoji-plus} `白眼`{:.emoji-plus}
```

[附录](#附录)是所有支持的小电视表情和它们对应的代码，表情源文件来源于[这里](https://www.bilibili.com/video/av27621778/){:target="_blank"}。




#### 图片注释

![](../img/theme.jpg)

这是一张图片
{:.desc}

<pre><code class="markdown">![](../img/theme.jpg)

这是一张图片
{:.desc}
</code></pre>

## 用到的开源库

### CSS

- [Bootstrap](https://github.com/twbs/bootstrap){:target="_blank"}
- [Font Awesome](https://github.com/FortAwesome/Font-Awesome){:target="_blank"}
- [Font Awesome Animation](https://github.com/l-lin/font-awesome-animation){:target="_blank"}（图标动画）

### JavaScript
- [jQuery](https://github.com/jquery/jquery){:target="_blank"}
- [ScrollReveal](https://github.com/jlmakes/scrollreveal){:target="_blank"}（图片模式下文章列表上浮效果，About 页面的时间轴上浮效果）
- [Tocbot](https://github.com/tscanlin/tocbot){:target="_blank"}（文章目录）
- [AnchorJS](https://github.com/bryanbraun/anchorjs/){:target="_blank"}（文章锚点）
- [Gitalk](https://github.com/gitalk/gitalk){:target="_blank"}（Gitalk 评论）
- [Valine](https://github.com/xCss/Valine){:target="_blank"}（Valine 评论）
- [Chart.js](https://github.com/chartjs/Chart.js){:target="_blank"}（[图表](#chartjs)）
- [mermaid](https://github.com/mermaid-js/mermaid){:target="_blank"}（[图表](#mermaid)）
- [MathJax](https://github.com/mathjax/MathJax){:target="_blank"}（公式渲染）
- [Katex](https://github.com/KaTeX/KaTeX){:target="_blank"} （公式渲染）
- [hightlight.js](https://github.com/highlightjs/highlight.js){:target="_blank"} （代码高亮渲染）
- [hightlight-line-number.js](https://github.com/wcoder/highlightjs-line-numbers.js/){:target="_blank"} （给 hightlight.js 生成的代码块加行号的插件）
- [Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search){:target="_blank"}（搜索）
- [fastclick](https://github.com/ftlabs/fastclick){:target="_blank"}（解决移动设备上的点击延迟问题）


## 附录


| ---- | ---- |
|`白眼`{:.emoji-plus} `` `白眼`{:.emoji-plus} ``|`鄙视`{:.emoji-plus} `` `鄙视`{:.emoji-plus} ``|
|`闭嘴`{:.emoji-plus}   `` `闭嘴`{:.emoji-plus} ``|`馋`{:.emoji-plus}   `` `馋`{:.emoji-plus} ``|
|`打脸`{:.emoji-plus}   `` `打脸`{:.emoji-plus} ``|`大哭`{:.emoji-plus}   `` `大哭`{:.emoji-plus} ``|
|`大佬`{:.emoji-plus}   `` `大佬`{:.emoji-plus} ``|`呆`{:.emoji-plus}   `` `呆`{:.emoji-plus} ``|
|`点赞`{:.emoji-plus} `` `点赞`{:.emoji-plus} ``|`调皮`{:.emoji-plus} `` `调皮`{:.emoji-plus} ``|
|`发财`{:.emoji-plus}   `` `发财`{:.emoji-plus} ``|`发怒`{:.emoji-plus}   `` `发怒`{:.emoji-plus} ``|
|`尴尬`{:.emoji-plus}   `` `尴尬`{:.emoji-plus} ``|`鼓掌`{:.emoji-plus}   `` `鼓掌`{:.emoji-plus} ``|
|`害羞`{:.emoji-plus}   `` `害羞`{:.emoji-plus} ``|`黑人问号`{:.emoji-plus}   `` `黑人问号`{:.emoji-plus} ``|
|`坏笑`{:.emoji-plus} `` `坏笑`{:.emoji-plus} ``|`惊吓`{:.emoji-plus} `` `惊吓`{:.emoji-plus} ``|
|`可爱`{:.emoji-plus}   `` `可爱`{:.emoji-plus} ``|`抠鼻子`{:.emoji-plus}   `` `抠鼻子`{:.emoji-plus} ``|
|`困`{:.emoji-plus}   `` `困`{:.emoji-plus} ``|`流鼻血`{:.emoji-plus}   `` `流鼻血`{:.emoji-plus} ``|
|`流汗`{:.emoji-plus}   `` `流汗`{:.emoji-plus} ``|`腼腆`{:.emoji-plus}   `` `腼腆`{:.emoji-plus} ``|
|`难过`{:.emoji-plus} `` `难过`{:.emoji-plus} ``|`呕吐`{:.emoji-plus} `` `呕吐`{:.emoji-plus} ``|
|`亲亲`{:.emoji-plus}   `` `亲亲`{:.emoji-plus} ``|`色`{:.emoji-plus}   `` `色`{:.emoji-plus} ``|
|`生病`{:.emoji-plus}   `` `生病`{:.emoji-plus} ``|`生气`{:.emoji-plus}   `` `生气`{:.emoji-plus} ``|
|`睡着`{:.emoji-plus}   `` `睡着`{:.emoji-plus} ``|`思考`{:.emoji-plus}   `` `思考`{:.emoji-plus} ``|
|`偷笑`{:.emoji-plus}   `` `偷笑`{:.emoji-plus} ``|`吐血`{:.emoji-plus}   `` `吐血`{:.emoji-plus} ``|
|`微笑`{:.emoji-plus}   `` `微笑`{:.emoji-plus} ``|`委屈`{:.emoji-plus}   `` `委屈`{:.emoji-plus} ``|
|`无奈`{:.emoji-plus} `` `无奈`{:.emoji-plus} ``|`笑哭`{:.emoji-plus} `` `笑哭`{:.emoji-plus} ``|
|`斜眼笑`{:.emoji-plus}   `` `斜眼笑`{:.emoji-plus} ``|`疑问`{:.emoji-plus}   `` `疑问`{:.emoji-plus} ``|
|`晕`{:.emoji-plus}   `` `晕`{:.emoji-plus} ``|`再见`{:.emoji-plus}   `` `再见`{:.emoji-plus} ``|
|`抓狂`{:.emoji-plus}   `` `抓狂`{:.emoji-plus} ``|`doge`{:.emoji-plus}   `` `doge`{:.emoji-plus} ``|
