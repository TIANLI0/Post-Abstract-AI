# Post-Abstract-AI

<p align="center">
  <img src="/img/logo.png" />
  <br>
  <br>
  适用于绝大多数博客的文章摘要生成器
  <br>
  <a href="https://flowus.cn/zhheo/share/3d6d616b-e183-436e-8e3e-2b177f99e941">官方文档</a> · <a href="https://summary.zhheo.com/">管理后台</a>
</p>

[随机访问已经支持TianliGPT的博客](https://summary.zhheo.com/static/matrix.html)

最近研究AI在博客和文章领域的应用，发现AI摘要是一个很不错的方向，研究了很久给搞出来了。在这篇文章中，我将帮助大家如何让你的博客接入TianliGPT。

![](/img/workflows.png)

## 什么是TianliGPT

TianliGPT是一个专业的文字摘要生成工具，你可以将需要提取摘要的文本内容发送给TianliGPT，稍等一会他就可以给你发送一个基于这段文本内容的摘要。

- 实时生成的摘要
- 自动生成，无需人工干预
- 一次生成，再次生成无需消耗key
- 包含文字审核过滤，适用于中国大陆
- 支持中国大陆访问

## 如何部署TianliGPT

我们可以通过在网页中嵌入TianliGPT的服务支持，让TianliGPT能够获取到你需要提交的内容。

1. 你需要在博客后面位置引入js和css（**引入在网站的任意位置**）

```html
<link rel="stylesheet" href="https://cdn1.tianli0.top/gh/zhheo/Post-Abstract-AI@0.15.2/tianli_gpt.css">
<script>
let tianliGPT_postSelector = '#post #article-container';
let tianliGPT_key = '5Q5mpqRK5DkwT1X9Gi5e';
</script>
<script src="https://cdn1.tianli0.top/gh/zhheo/Post-Abstract-AI@0.15.2/tianli_gpt.min.js"></script>
```

2. 我们需要更改一些参数来让这个模型运作起来。

`tianliGPT_postSelector`和`tianliGPT_key`

### tianliGPT_postSelector

这个参数是填写你的博客文章所在的元素属性的选择器，在生成提交的文本时，只会将这个选择器对应的元素内的文本进行提交，并且在这个选择器对应的元素上放插入AI摘要。如果你使用的是Butterfly主题，那么为`#post #article-container`。

这里列出一些常见博客主题的选择器值（部分未经过测试，如果有问题欢迎反馈）：

| 主题名称             | tianliGPT_postSelector         | tianliGPT_postURL | 备注 |
| -------------------- | ------------------------ | --- | --- |
| [hexo-theme-butterfly](https://flowus.cn/zhheo/share/927667b2-ba27-42b1-98f2-8fb184720ed2) | #post #article-container | 无需添加 | 无 |
| [hexo-theme-fluid](https://flowus.cn/zhheo/share/a8c7101e-9b06-4ec8-9063-0fe3eef31f5c) | #board .post-content | 无需添加 | 无 |
| hexo-theme-next      | #posts .post-body        | 无需添加 | 无 |
| hexo-theme-stellar | .md-text.content.post | 无需添加 | 无 |
| hexo-theme-volantis | #post #post-body | 无需添加 | 无 |
| hugo-theme-DoIt | .page.single:not(.special) .content | 无需添加 | 无 |
| halo-theme-xue | #container .article-content #lightGallery | 无需添加 | 无 |
| [wordpress: argon](https://flowus.cn/08d8f6e4-d487-40b9-951e-8c0c3df7506f) | #post_content | 无需添加 | 无 |
| wordpress: 7B2 | #primary-home .entry-content | 修改里面的域名：`b2.7b2.com/*.html` | 无 |
| wordpress：pix | .single-content | `https://*/*.html` | 无 |
| wordpress: Sakurairo | .post .entry-content | 无需添加 | 无 |
| [wordpress: 子比主题](https://flowus.cn/88b69f42-e0f7-482c-9941-24a06c97d6d0) | .single-post .wp-posts-content | 无需添加 | 无 |
| wordpress: CorePress | .post-content-content | 无需添加 | 无 |
| wordpress: OneNav | .post-template-default .panel-body | 无需添加 | 无 |
| valaxy-theme-yun | .content .markdown-body | `*/posts/*` | 无 |
| typecho-bearsimple | #post-content #bearsimple-images | 无需添加 | 无 |
| typecho-bearhoney | .post-content-block .content | 无需添加 | 无 |
| typecho-handsome | #postpage #md_handsome_origin | 无需添加 | 无 |
| [typecho-joe](/issues/27) | .joe_post .joe_detail__article | 无需添加 | 无 |
| [typecho-void](/issues/32) | .articleBody | 无需添加 | 无 |

如果你没有在上面看到你的主题，查看[通用教程](https://flowus.cn/zhheo/7a353126-f225-4e5c-8c11-f5adefe85b7f)，手把手教你如何使用前端选择器。

**如果你写了你的主题适配教程，欢迎在issues里投稿，我会收录到官方文档中，帮助更多的小伙伴搭建。**

### tianliGPT_key

到[爱发电](https://afdian.net/item/f18c2e08db4411eda2f25254001e7c00)中购买，10元5万字符（限时折扣9元）。请求过的内容再次请求不会消耗key，可以无限期使用。

- 相比实时请求openai，使用tianliGPT可以让你请求过的内容不再消耗key，适合生产环境。
- 相比实时请求openai，使用tianliGPT可以在国内更快速的获取摘要。
- 符合中国大陆法律法规。
- key消耗完毕，已经请求过的内容仍然可以继续请求，避免了被恶意请求造成的资金损失和业务停摆。

购买完成后，进入管理后台：https://summary.zhheo.com/

登录后点击右上角的“添加新网站”，输入密钥即可

即可绑定成功。

## 高级技巧

更多的参数变量详见[高级文档](https://flowus.cn/9be089e8-667e-4b0e-93c3-ad69697ce673)

例如关闭文字动画、限制每次提交最大字数等。

## 升级版本

升级版本方式：只需要将js和css链接中的`@0.5`这种的版本号更改为最新的版本即可。

![](/img/update.png)

最新版本的位置：

![](/img/update2.png)

## 开发团队

后端开发：[@Tianli](https://github.com/Tianli0)

产品设计与前端开发：[@张洪Heo](https://github.com/zhheo)

## 技术支持请联系

zhheo@qq.com

点击链接加入讨论子频道【TianliGPT 问题交流】：https://pd.qq.com/s/7cx85i9l0

针对此项目的任何技术支持与关于API的相关问题，可以联系此邮箱，会在24小时内回复。

## 更多支持TianliGPT的项目

[Post-Summary-AI](https://github.com/qxchuckle/Post-Summary-AI) - 轻笑开发的博客摘要生成工具

[hexo-ai-excerpt](https://github.com/rootlexblog/hexo-ai-excerpt) - 在本地部署时添加AI摘要
