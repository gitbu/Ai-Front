---
title: html2canvas
date: 2019-12-05 19:34:12
categories:
- 前端截图
tags: 
- "前端截图"
---
# [html2canvas](https://html2canvas.hertzen.com/)

## 简介

`html2canvas`是一个基于`DOM`的屏幕截图脚本，它可以根据页面上的可用信息构建屏幕截图，因此可能无法准确生成实际的屏幕截图。

## 原理

* 遍历所需截图节点内的`DOM`元素

* 读取这些元素的属性并重新构建页面

  `ps:` 它实际上并不是截取页面的屏幕快照，而是根据它从DOM读取的属性来构建页面的表示形式。

  `warn:`它只能正确呈现它理解的`CSS`属性。详见[features](http://html2canvas.hertzen.com/features)

## 使用

1. 安装 `npm install --save html2canvas`

2. 开始截图

   ```js
   html2canvas(document.body).then(function(canvas) {
       document.body.appendChild(canvas);
   });
   ```

3. 截图配置项

| `Name`                   | `Default`                 | `Description`                                                |
| :----------------------- | :------------------------ | :----------------------------------------------------------- |
| `allowTaint`             | `false`                   | 是否允许跨域图像污染画布                                     |
| `backgroundColor`        | `#ffffff`                 | 画布背景色，如果未在`DOM`中指定，设置`null`为透明            |
| `canvas`                 | `null`                    | 现有的`canvas`元素可用作绘图的基础                           |
| `foreignObjectRendering` | `false`                   | 是否在浏览器支持的情况下使用`ForeignObject`渲染              |
| `imageTimeout`           | `15000`                   | 加载图像的超时时间（以毫秒为单位）。设置为`0`时禁用超时。    |
| `ignoreElements`         | `(element) => false`      | 判定函数，可以删除渲染中匹配的元素。                         |
| `logging`                | `true`                    | 启用日志记录以进行调试                                       |
| `onclone`                | `null`                    | 克隆文档以进行渲染时调用的回调函数可用于修改将要渲染的内容，而不会影响原始源文档。 |
| `proxy`                  | `null`                    | `Url`转到代理上 ，用于加载跨源图像。如果留空，则不会加载跨原始图像。 |
| `removeContainer`        | `true`                    | 是否要清理`html2canvas临时创建的`克隆的DOM`元素              |
| `scale`                  | `window.devicePixelRatio` | 用于渲染的比例，默认为浏览器设备像素比率                     |
| `useCORS`                | `false`                   | 用来设置是否允许使用跨域的图片进行访问                       |
| `width`                  | `Element width`           | `canvas`的宽度                                               |
| `height`                 | `Element height`          | `canvas`的高度                                               |
| `x`                      | `Element x-offset`        | 裁剪画布`x`坐标                                              |
| `y`                      | `Element y-offset`        | 裁剪画布`y`坐标                                              |
| `scrollX`                | `Element scrollX`         | 渲染元素`x`方向的滚动位置(例如，如果`Element`使用`position: fixed` ) |
| `scrollY`                | `Element scrollY`         | 渲染元素`y`方向的滚动位置(例如，如果`Element`使用`position: fixed` ) |
| `windowWidth`            | `Window.innerWidth`       | 渲染元素时使用的窗口宽度，这可能会影响媒体查询之类的东西     |
| `windowHeight`           | `Window.innerHeight`      | 染时使用的窗口高度 Element ，这可能会影响媒体查询等内容      |

## 问题解决

### 图片跨域问题