---
title: 重建博客
subtitle: 重新更新博客
date: 2026-02-10
tags: ["blog", "技术"]
---

2017年的时候使用jekell搭建了这个博客，但是后续因为寡妇王的问题，图片就无法显示了，后面多次想解决一次，但碍于时间和水平问题，一直没处理，这次下定决心，必须重建博客，也接这个机会让AI帮忙搞定。

这次使用的框架是Hugo，主题是Beautiful Hugo，依旧使用GitHub的免费空间。

官方仓库[halogenica/beautifulhugo: Theme for the Hugo static website generator](https://github.com/halogenica/beautifulhugo)，按照仓库的readme依次操作即可。

这里有几个点要注意，如果是使用官方推荐的配置，但又想用中文作为编码，一定要在配置上添加
`hasCJKLanguage = true`
否则中文统计的字数完全不对，并且会导致首页显示的文章概览出现问题，请务必注意，我在这个上折腾了大半天才发现。

然后再就是，如果想要把GitHub作为图床，需要设置一下图片的存放位置，无法跟文本文件放在同一目录下。
当然这个问题，也让AI给了几个解决方案，你可以自己参考使用，理论上都是可以解决的：

方案 1：Page Bundle
  优点：
  - 文章和图片组织在一起，结构清晰
  - 图片路径最简单，只需文件名
  - Hugo 官方推荐方式
  缺点：
  - 需要为每篇文章创建目录
  - 多篇文章共用图片会重复
  目录结构
  content/posts/
  └── 2020-03-01-文章1/
      ├── index.md                          # 文章内容
      ├── 截屏2020-03-0113.53.34.png       # 图片文件
      ├── 截屏2020-03-0114.00.25.png
      ├── 截屏2020-03-0114.01.26.png
      ├── 截屏2020-03-0114.02.39.png
      ├── 截屏2020-03-0114.05.06.png
      └── 截屏2020-03-0114.43.20.png
  
方案 2：Static 目录方式（推荐用于共享图片）
  将图片放在 /static/img/posts/ 目录，使用绝对路径引用。
  Static 目录方式
    文件结构：
    static/
    └── img/
        └── posts/
            ├── 截屏2.png
            └── ...
    在文章中引用：
    ![描述](/img/posts/截屏2.png)
  
    优点：
    - 多篇文章可以共享同一张图片
    - 图片路径固定，不受文章位置影响
    - 便于集中管理图片
  
    缺点：
    - 需要使用绝对路径
    - 图片和文章分离，不够直观
    
方案 3：保持 posts/assets，配置 Hugo

  修改文章引用路径，统一使用相对于 content 目录的路径。

  在文章中引用：
  ![描述](/posts/assets/截屏1.png)
  或者移动 assets 到 static：
  
方案 4：统一移到 Static

  将所有 posts/assets 移到 static/posts/assets：
  在文章中引用：
  ![描述](/posts/assets/截屏1.png)

方案 5：混合方案（最实用）

  根据图片使用情况分别处理：

  单篇文章专用图片 → Page Bundle
  posts/
  └── 2020-03-01-文章/
      ├── index.md
      └── 图片.png
  引用：![](图片.png)

  多篇文章共用图片 → Static 目录
  static/img/posts/
  └── 共享图片.png
  引用：![](/img/posts/共享图片.png)
