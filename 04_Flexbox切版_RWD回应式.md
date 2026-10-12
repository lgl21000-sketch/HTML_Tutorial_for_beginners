# Flexbox & Grid

* HTML 预设是垂直排列（块级元素每个占一排）。如果需要在一排中排列多个区块，有以下方法：

1. **定义在子元素**
   - 行内元素：`<span>`， `<a>`
   - 行内区块：`<div style="display: inline-block">`

2. **定义在父容器（推荐）**
   - Flexbox（弹性盒布局）: 把 **父容器** 设为 `display: flex;`     一维布局首选
   - CSS Grid（网格布局）: 把 **父容器** 设为 `display: grid;`      二维网格首选

*  CSS Flexbox
    ```css
    .parent {
    display: flex;
    gap: 16px;                        /* 区块之间的间距 */
    justify-content: space-between;   /* 主轴方向（默认水平）对齐：两端对齐、居中等 */
    align-items: center;              /* 交叉轴方向（默认垂直）对齐 */
    } 
    .child {
    width: 30%;                       /* 固定或百分比宽度， 或者使用 flex: 1; 自动拉伸平分剩余空间 */
    height: 100px;
    }
    ```

*  CSS Grid
    ```css
    .parent {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 划分 3 个等宽列（1fr 代表一份剩余空间） */
    gap: 16px;
    }
    ```

---------------------------------------------------------

# Responsive Web Design

* 用RWD使网页在不同大小的屏幕上都能显示

- 缩小区块宽度
    ```css
    .setwidth {
        width: 100%;
        max-width: 1000px;              /* 屏幕大时最多 1000px，屏幕小时自动缩小为 100% 避免溢出 */
    }
    @media(max-width:800px){
        .setwidth{
            width:500px                 /* 屏幕宽度小于800px时，区块类setwidth宽度缩小至500px */
        }
    }
    ```

- 多区块行换行: 把 **父容器** 设为 `flex-wrap: wrap;`
    ```css
    .parent {
    display: flex;
    } 
    .child {
    width: 30%;       
    }
    @media(max-width:800px){
        .parent {
            display: flex;
            flex-wrap: wrap;            /* 屏幕宽度小于800px时，换行*/
        } 
        .child {
            width: 90%;                 /* 区块宽度增加（每行区块数量减少了）*/
        }  
    }
    ```

- 内容换行: 显示或隐藏换行标签<br/>
    ```html
    <div id="test">xxxxx<br/>yyyyyy</div>
    ```
    ```css
    #test br{display:none}
    @media(max-width:800px){
        #test br{display:block}         /* 屏幕宽度小于800px时，换行*/
    }
    ```

- 预设多种版面，用显示和隐藏来切换
    ```html
    <div class="Mac">Mac</div>
    <div class="iPad">iPad</div>
    <div class="iPhone">iPhone</div>
    ```
    ```css
    .Mac{display:block}
    .iPad{display:none}
    .iPhone{display:none}
    @media(max-width: 1200px){
        .Mac{display:none}
        .iPad{display:block}
        .iPhone{display:none}
    }
    @media(max-width: 500px){
        .Mac{display:none}
        .iPad{display:none}
        .iPhone{display:block}
    }
    ```

---------------------------------------------------------

# 练习 3
科技产品推广单页（Product Showcase）
1. 页面结构与内容（HTML）
请直接复制以下 HTML 内容作为练习基础，不要修改标签结构：
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <title>TechVision - 智能眼镜</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- 顶栏/设备版面（用 RWD 显隐切换） -->
  <header class="header">
    <div class="Mac">💻 当前正在使用 Mac / 桌面大屏版面浏览</div>
    <div class="iPad">📱 当前正在使用 iPad / 平板版面浏览</div>
    <div class="iPhone">📲 当前正在使用 iPhone / 手机版面浏览</div>
  </header>

  <!-- 核心介绍区（要求使用 Flexbox） -->
  <section class="hero-section">
    <div class="hero-card">
      <h3>轻盈设计</h3>
      <p>仅重 45g，全天候无感佩戴，采用钛合金流线型框架。</p>
    </div>
    <div class="hero-card">
      <h3>高清显示</h3>
      <p>双眼 4K Micro-OLED 屏幕，带来极致震撼的视觉享受。</p>
    </div>
    <div class="hero-card">
      <h3>长久续航</h3>
      <p>搭配智能充电盒，最高可提供 24 小时连续使用时间。</p>
    </div>
  </section>

  <!-- 特性网格区（要求使用 CSS Grid） -->
  <section class="feature-grid">
    <div class="feature-item">核心功能 1：实时 AI 翻译</div>
    <div class="feature-item">核心功能 2：AR 导航指引</div>
    <div class="feature-item">核心功能 3：空间音频体验</div>
  </section>

  <!-- 内容与断行控制区 -->
  <footer class="footer-text">
    <p>联系我们：<br/>support@techvision.com</p>
  </footer>

</body>
</html>
```

2. CSS 编写要求
请在 style.css 中编写样式，逐一满足以下 5 个知识点考核要求：

考核点 1：父容器布局——Flexbox 与子元素分配
    对 .hero-section 启用 Flexbox 布局：
        设置区块之间的间距为 16px（使用 gap）。
        设置主轴方向为两端对齐（justify-content）。
        设置交叉轴居中对齐（align-items）。

    对 .hero-card 设置：
        初始宽度占父容器的 30%，高度 120px。

考核点 2：父容器布局——CSS Grid
    对 .feature-grid 启用 Grid 布局：
        使用 repeat() 函数和 1fr 单位将该网格划分为 3 个等宽列。
        设置网格间距为 16px。

考核点 3：RWD 宽度拉伸与最大宽度限制
    给 .hero-section 和 .feature-grid 统一设置：
        宽度为 100%。
        最大宽度限制为 1000px（max-width），并在页面中水平居中（提示：margin: 0 auto）。

考核点 4：RWD 媒体查询与 Flexbox 多区块换行
    编写媒体查询，当屏幕宽度大于 501px 且小于等于 800px 时（即 @media (max-width: 800px)）：
        Flex 换行：让 .hero-section 允许换行（flex-wrap: wrap），同时将子区块 .hero-card 的宽度调整为 45%。
        文本断行控制：默认情况下隐藏 .footer-text br（显示为一行 联系我们：support@techvision.com）；当屏幕小于等于 800px 时，将 <br/> 显示出来使内容分行。

考核点 5：RWD 预设多种版面显示与隐藏切换
    默认状态（桌面屏/Mac）：
        .Mac 显示为块级元素（display: block）。
        .iPad 和 .iPhone 隐藏（display: none）。
    平板屏（max-width: 1200px 且大于 500px）：
        仅 .iPad 显示，其余隐藏。
    手机屏（max-width: 500px）：
        仅 .iPhone 显示，其余隐藏。
    额外要求：在手机屏下，让 .hero-card 的宽度增加至 100%（单列排列）。

3. 自检清单
完成代码后，你可以拖动浏览器窗口宽度，检查是否达到以下效果：
    [ ] 大屏（>1200px）时，顶部显示 Mac 提示，中段为 3 列 Flex 卡片和 3 列 Grid 网格。
    [ ] 中屏（<=800px）时，顶部显示 iPad 提示，Flex 卡片变为每行 2 个，底部邮箱地址自动折行。
    [ ] 小屏（<=500px）时，顶部显示 iPhone 提示，Flex 卡片变为单列占满全宽（100%）

参考答案：Examples/
    练习3_flexbox_RWD.html 练习3_flexbox_RWD.css