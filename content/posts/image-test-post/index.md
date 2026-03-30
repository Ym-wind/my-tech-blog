---
title: "我的第一篇带图博客"
description: "这是一篇测试 Stack 主题 Page Bundles 图片管理功能的文章。" # 加上描述更专业
date: 2026-03-30T12:00:00+08:00
draft: false # 记得把这里改成 false，否则首页看不到！
categories:
    - "教程"
tags:
    - "Hugo"
    - "Image"

# ⚠️ 核心配置：指定文章的宽屏头图！
image: "cover.jpg" # 直接写文件名即可，因为它跟 .md 在同个文件夹
---

### 1. 文章头图

上面的图片就是我们在配置区指定的 `image` 头图，它会在首页卡片和文章顶部显示。

### 2. 文章内插图

你也可以在 Markdown 的内容区，像使用普通图片一样插入它：

![我是一张内插图](cover.jpg)

### 3. 公式测试

顺手再测试一下我们之前的公式渲染，看看背景有没有消失：

$$\tau_m \frac{dU(t)}{dt} = -(U(t) - U_{rest}) + R I(t)$$

写完了，快去预览一下吧！