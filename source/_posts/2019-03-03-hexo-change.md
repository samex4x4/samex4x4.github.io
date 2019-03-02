---
title: hexo 頁面修改
date: 2019-03-03 00:18:26
tags: 
    - hexo
---

紀錄一些修改的部分

<!--more-->

## 修改主題

```
git clone https://github.com/iissnan/hexo-theme-next themes/next
```
修改_config.yml
theme: next

## 增加頭像

hexo new page "uploads"
將圖片放到 source/uploads 中

修改 themes/next/_config.yml
avatar: /uploads/cat-01.jpg

[參照](https://github.com/iissnan/hexo-theme-next/wiki/%E8%AE%BE%E7%BD%AE%E4%BE%A7%E8%BE%B9%E6%A0%8F%E5%A4%B4%E5%83%8F)

## 修改背景

打開themes/next/sources/css/_schemes/ 找到自己選擇的主題，修改index.styl

[參照](https://sqmwin.github.io/2017/12/31/next-background-image/)

```xml
body {
  background:url(/images/background.jpg);
  background-attachment: fixed;
}
```

## 增加關於我、tag頁面

hexo new page "tags"
hexo new page "about"

[參照](https://github.com/iissnan/hexo-theme-next/wiki/%E5%88%9B%E5%BB%BA%E6%A0%87%E7%AD%BE%E4%BA%91%E9%A1%B5%E9%9D%A2)

修改source/tags/index.md

```
---
title: All tags
date: 2019-03-02 23:51:22
type: "tags"
comments: false
---

```
修改 themes/next/_config.yml
把menu中的about, tags註解打開

```xml
about: /about/ || user
tags: /tags/ || tags
```




