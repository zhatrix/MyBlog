---
title: 部署免费无限制图床
# author: zhatrix
date: 2024-02-04
# categories: [免费]
tags: ["技术", "图床", "telegraph", "cloudflare"]
---
## 部署过程：

### 1.下载安装node 和  wrangler


```
npm install wrangler --save-dev
```

### 2.下载cf-image-hosting

```
git clone https://github.com/ifyour/cf-image-hosting.git
cd cf-image-hosting
```

### 2.运行以下命令完成部署：

```
npm install
npm run dev
npm run deploy
```

### 3.在cloudflare绑定域名
workers&pages -> Triggers -> Custom Domains -> Add a custom domain
![image](https://image.zhatrix.com/file/7accbca6e5372f391f41d.png)

### 4.使用图床
![image](https://image.zhatrix.com/file/9108fb73c92f2be10bc81.png)

### 5.感谢
1.感谢cf-image-hosting作者提供的集成，GitHub地址：[cf-image-hosting](https://github.com/ifyour/cf-image-hosting)
2.感谢Telegraph和Cloudflare提供的服务

### Change Log

2024-02-04 创建
