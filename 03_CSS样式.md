# CSS简介，语法
> **什么是 CSS？**  
> 如果 HTML 是毛坯房的砖瓦，CSS 就是精装修。它专门负责网页的颜色、排版、字体和视觉特效。
* HTML用于处理页面主要结构
* CSS用于处理排版和样式细节

---------------------------------------------------------

## CSS定义

* CSS 通过标签的style属性定义
    - 语法结构: 名称:内容
    - 可同时定义多个，用;隔开
    <div style="color:red;font-weight:bold;font-size:16px">content</div>

* 预设CSS样式
    - 有的标签有预设样式
    <h3>预设加粗，放大</h3>
    - 有的标签没有预设样式，需要通过style定义
    <div>没有预设</div>


* 常用文字样式
color:red                   color:#0000ff
font-weight:normal          font-weight:bold
font-size:16px
text-decoration:underline   text-decoration:line-through
text-align:left             text-align:center

* 常用显示模式属性
display: block;：   块级模式（独占一行，如 <div>, <h1>）。
display: inline;：  行内模式（一行可以排多个，如 <span>, <a>）。
display: none;：    隐藏元素（在页面上完全消失）。

* CSS 注释的写法
CSS 的注释采用斜杠加星号的形式，支持单行或多行：
/* 这是一个 CSS 注释 */
/* 
  这也是一个多行注释，
  可以用来写比较详细的区块说明
*/

---------------------------------------------------------

## CSS Box Model 区块模式

* 每个标签占一个方形区块， 内嵌的标签一个区块=内嵌于另一个区块

- 尺寸 width, height（预设宽度和父标签一样，预设高度随内容缩放，百分比=父标签百分比）
    <div style="width:500px;height:300px">
    <div style="width:50%;height:50%">

- 填充 padding
    <div style="padding:10px">
    <div style="padding-left:10px">
    <div style="padding-bottom:10px">

- 边距 margin
    <div style="margin-bottom:10px">
    <div style="margin-top:10px">

- 边框 border
    <div style="border:0px">
    <div style="border:1px solid red">
    <div style="border:3px dashed blue">

- 背景色 background-color
    ```html
    <div style="background-color:blue">
        content with blue background color
        <span style="background-color:red">
            content with red backgound color
        </span>
        content with blue background color
    </div>
    ```

---------------------------------------------------------

## CSS 选择器

* 3种CSS引入方式

    - 行内样式（Inline Style）
        <div style="color:red">

    - 内部样式表（Internal Style Sheet）写在 HTML head 的 <style></style> 标签里
        ```html
        <head>
            <style>.colorclass{color:red}</style>
        </head>
        <body>            
            <div class="colorclass"></div>
        </body>
        ```    

    - 外部样式表（External Style Sheet）：写在独立的 .css 文件里，通过 <link> 标签引入
        ```css  /* style.css文件 */ 
        .colorclass{color:red}
        ```

        ```html  <!-- html文件 -->
        <head>
            <link rel="stylesheet" type="text/css" href="style.css">
        </head>
        <body>            
            <div class="colorclass"></div>
        </body>
        ```

* 3种方法引用样式
    - 用class类，用id，用标签
    <style>
        .colorclass{color:red}  /* 用class类，以.开头 */
        #colorid{color:blue}    /* 用id，以#开头 */
        span{}                  /* 用标签 */
    </style>

    <div class="colorclass"></div>  <!-- 在标签内定义class类 -->
    <div id="colorid"></div>        <!-- 在标签内定义id -->
    <span></span>                   <!-- 标签名称 -->

* 后代选择器（Descendant Selector）
    <style>
        .colorclass p{color:red}    /* 表示选中 class colorclass 内部所有的 <p> 标签 */
        header ul{}                 /* 表示选中 <header> 内部所有的 <ul> 标签 */
    </style>

    <header>
        no style
        <ul>
            <li>with style</li>
        </ul>
    </header>
    <main>
        <article class="colorclass">
            no style
            <h1></h1>
            <p>with style</p>
        </article>
    </main>

---------------------------------------------------------

# 练习 2
练习任务：编写“个人技术博客”页面
请创建一个 HTML 文件，将以下给出的具体内容用正确的 HTML 标签包裹并组装起来：

1. 浏览器配置与页面结构
基础 HTML5 结构（<!DOCTYPE html>、<html>、<body>）。

在 <head> 中设置页面标题为：张三的个人技术博客。

2. 页面顶栏（<header> & <nav>）
顶栏容器：使用 <header> 包裹顶栏。

导航栏：在 <header> 中嵌套 <nav>，包含以下 2 个链接（<a>）：

链接 1：名称为 首页，href 为 [https://example.com/home](https://example.com/home)

链接 2：名称为 跳转到表格，href 为 #skills-table（锚点链接）

3. 侧边栏（<aside> & <ul> + <li>）
侧边栏容器：使用 <aside> 包裹侧边栏。

推荐阅读列表：在 <aside> 中放入一个无序列表（<ul>），包含 2 个列表项（<li>）：

列表项 1：HTML5 语义化标签指南

列表项 2：CSS Flexbox 布局入门

4. 核心正文（<main> & <article>）
核心内容容器：使用全页唯一的 <main> 包裹正文。

文章区块：在 <main> 中嵌套一个 <article> 标签。

文章具体内容（全部放在 <article> 内部）：

主标题（<h1>）：我的 Web 前端学习笔记

段落（<p>）：欢迎来到我的博客！今天是我学习 HTML5 的第一天，掌握了许多非常有用的标签。

图片（<img>）：

图片地址（src）：[https://via.placeholder.com/150](https://via.placeholder.com/150)

替换文本（alt）：学习笔记封面图

副标题（<h2>）：今天学习的 3 个核心知识点

有序列表（<ol> + <li>）：放入以下 3 个步骤：

理解网页的语义化结构

掌握 a 标签的锚点跳转

学会使用 table 绘制数据表格

带 ID 的标题（<h2>）：添加属性 id="skills-table"，内容为 我的技能熟练度（作为上面导航链接的跳转目标）。

数据表格（<table>）：包含 2 行 2 列的数据（使用 <tr> 和 <td>）：

第一行：技能 | 熟练度

第二行：HTML5 | 精通

5. 页面页脚（<footer>）
页脚容器：使用 <footer>。

版权声明：在 <footer> 中添加文字：© 2026 张三的个人博客. 版权所有.

6. 加入样式要求。你需要写出 3 个不同的 HTML 文件（对应 3 种 CSS 引入方式）
index1.html：全部使用 行内样式（Inline Style）（即直接在每个标签上加 style="..."）。
index2.html：全部使用 内部样式表（Internal Style Sheet）（在 <head> 里的 <style> 中使用选择器）。
index3.html：使用 外部样式表（External Style Sheet）（通过 <link> 引入 style.css 文件）。

全局/块级元素与盒子模型 (Box Model)：

<header>（顶栏）：背景色设为 #f4f4f4，下边框（border-bottom）设为 2px solid #ccc，内边距（padding）设为 15px，底部外边距（margin-bottom）设为 20px。

<aside>（侧边栏）：宽度设为 250px，背景色设为 #eef6ff，内边距设为 10px，边框设为 1px dashed #99ccff。

<table>（表格）：边框合并设为标准边框，外边距顶部设为 15px，每个单元格（<td> 和 <th>）设置 8px 的内边距和 1px solid #ddd 的边框。

文本样式 (Text Styling)：

主标题 <h1>：字号设为 24px，颜色设为 #333333，对齐方式设为居中（text-align: center）。

导航链接 <a>：去除下划线（text-decoration: none），文字颜色设为 #0066cc，加粗显示（font-weight: bold）。

锚点目标 <h2>（即 id="skills-table"）：文字加上删除线（text-decoration: line-through，用以练习属性）。

后代选择器与显示模式 (Selectors & Display)：

侧边栏里的列表项：要求使用后代选择器（如 aside li），将其文字颜色设为 #555555，字号设为 14px。

隐藏元素：在 <article> 内添加一个 <p class="secret">这是隐藏测试文本</p>，并使用 display: none; 将其隐藏。

参考答案：Examples/
    练习2-1_张三的个人技术博客CSS_inline.html
    练习2-2_张三的个人技术博客CSS_internal_style_sheet.html
    练习2-3_张三的个人技术博客CSS_external_style_sheet.html, 练习2-3_张三的个人技术博客CSS_external_style_sheet.css