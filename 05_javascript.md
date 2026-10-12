# Javascript
> **什么是 JavaScript？**  
> 如果 HTML 是骨架，CSS 是皮肤，JavaScript 就是网页的**大脑和肌肉**。它赋予网页交互能力（如点击按钮弹出弹窗、动态修改文字、联网获取数据）。

---------------------------------------------------------

## 定义与引入
* 写在 `<script>` 标签内，`<script>`放在`<body>`标签里
* 或写在单独文件里例如xxx.js，通过 `<script src="xxx.js"></script>` 引入。
* 用;分隔指令
* 大小写有区别

<html>
    <head>
    </head>
    <body>
        <script>
            console.log("Hello World");console.log("Hi")
        </script>
    </body>
</html>

---------------------------------------------------------

## 基础语法与变量

* javascript注解
- 单行 //
- 多行 /*     */

* 定义变量与常量：
  - `const`：定义常量（值不能被修改，如库名）。
  - `let`：定义变量（值可以随时改变，现代 JS 推荐替代旧的 `var`）。

* 数据类型datatype
number, "string", bool(true小写, false小写), undefined, null, Object

* 运算
+, -, *, /, %(取余数)
+=, -=...
>=, ==...
&&, ||

---------------------------------------------------------

## 流程控制
* 条件判断 (if...else)：
    ```javascript
    let score = 85;
    if (score > 90) {
        console.log("优秀");          // console.log 相当于print,显示在页面console(按F12选择console栏)
    } else if (score >= 60) {
        console.log("及格");
    } else {
        console.log("不及格");
    }
    ```

* 循环 (for)：
    ```javascript
    for(let n=0; n<3; n++){
        if(n==1){
            continue;           //跳入下一循环
        }
        if(n==2){
            break;              //跳出循环
        }
    }
    ```

* 循环 (while)：
    while(){}

* 函数
    ```javascript
    let test=function(x){console.log(x);return x}       // 传统函数
    y=test(5);
    let addArrow = (n1, n2) => n1 + n2;                 // 箭头函数（更简洁的写法）
    ```

* Object
    ```javascript
    let obj=new Object()
    obj.x=3;                    //object property
    obj.test=function(){        //object method
        this.x++;               //this代表这个Object
    };
    ```

* 用JSON建立Object JavaScript Object Notation
    - 直接在内部定义，无需使用obj.
    - 分隔属性用,而不是;
    - 赋值用:而不是=
    ```javascript
    let obj={
        x:3,
        test:function(){},
    }
    ```javascript

* Array
    ```javascript
    let a=new Array[]
    let a=[]
    let a=[1,2,3]
    a.push(newitem)
    console.log(a[0])
    a.length
    ```

---------------------------------------------------------

## DOM 操作与核心对象 (Window / Document)
* HTML Element
- 每个HTML标签在js引擎中都有对应的Object，称为HTML Element
- 把HTML的Object串联在一起就是物件结构HTML DOM(Document Object Model) => document

* important Objects
- window —— 浏览器窗口（全局对象）
    全局作用域, e.g. window.alert()
    控制浏览器窗口, e.g. window.open() window.resizeTo()
    全局定时器, e.g. setTimeout、setInterval
    包含其他核心对象, e.g. window.document、window.screen
    window.innerWidth, window.innerHeight, window.prompt("input","default"), window.alert("msg")
- document —— 网页文档（DOM 树）
    document.getElementById('id')：获取页面元素
    document.createElement('div')：动态创建元素
    document.title, document.body, document.querySelector
- screen —— 用户的物理屏幕
    window.screen.width / window.screen.height, window.screen.availWidth / window.screen.availHeight

* 获取HTML中每个标签物件的方法
- 直接获取: body, title
    document.body
- 使用querzSelector方法query id
    <div id="divid">
    ```javascript
    let divElement = document.querySelector("#divid")
    let divElement = document.getElementById("divid")       // getElementById不需要在id前加#
    ```

* 使用标签object
    document.body.innerHTML 标签内容
    document.body.className 标签class
    document.body.id 标签id
    document.body.style.fontSize="15px"
    document.body.style.color="red"

* 事件处理
- 常见事件类型: onclick, onmouseover, onmouseout, onmousedown, onmouseup
- 在那个标签？什么事件类型？对应处理函数？
<div onclick="clicked(this)">                               //在这里this代表div标签
<script>
    let clicked = function(ele){ele.innerHTML="clicked"}    //在这里ele代表被传入的参数，这里是div标签(this)
</script>

* 箭头函数处理this
- 简单 输入参数=>输出
- 没有this, this属于上一层含this的函数
    ```javascript
    let add=(n1, n2)=>{return n1+n2}
    let add=(n1, n2)=> n1+n2
    let add=function(n1,n2){
        return n1+n2;
    }
    ```

* 联网
- 取得文字
    ```javascript
    fetch(URL).then(
        function(response){
            return response.text();
        }
    ).then(
        function(data){
            console.log(data)
        }
    )
    ```
- 取得JSON
    ```javascript
    fetch(URL).then(
        function(response){
            return response.json();
        }
    ).then(
        function(data){
            console.log(data);
        }
    )
    ```

---------------------------------------------------------

## 数组解构、剩余运算与深浅拷贝
* 结构赋值，拆分array分别赋值
```javascript
let [x, y, z] = [1,2,3];
let [x, y=0, z=5] = [1,1];         //x=1, y=1, z=5(default)
let myobject={x:1, y:2};
let {x, y}=myobject;             //x=1, y=2
let x,y;
({x,y}=myobject);
let {x:newx, y:newy}=myobject   //newx=1, newy=2
```

* 其余运算，用...
- 必须放在最后
```javascript
let [x, y,...z] = [1,2,3,4,5]   //x=1, y=2, z=[3,4,5]
let myobj={x:1,y:2,z:3}
let {x,...zz}=myobj             //x=1, zz={y:2,z:3}
```

* 模组引用，将javascript分别存于不同文件
- 不同模组间通过import引用
- html用type,src引用
    ```javascript   //functionmodule.js
    let print=function(msg){
        console.log(msg)
    }
    export default print;

                    //input.js
    import print from './functionmodule.js';
    print(test)
    ```
    ```html 
    <script type="module" src="input.js"></script>
    ```

* 代理物件Proxy，拦截并定制对象的操作（比如当别人访问某个不存在或虚拟的属性时，自动帮他计算拼接出来）。
```javascript
let customer={firstname:"Anna", middlename:"Hills", lastname:"River"}
let myproxy= new Proxy(
    customer, 
    {
        get:function(target, property){
            if(property==="fullname"){
                return target.firstname+target.middlename+target.lastname
            }else{
                return target[property]
            }
        }
    }
)
console.log(myproxy.fullname)       //AnnaHillsRiver
console.log(myproxy.firstname)      //Anna
console.log(myproxy.lastname)       //River
```

* object指向，浅拷贝，深拷贝
- object没有拷贝只有建立一个新的变量指向原来的object
    ```javascript
    let a={x:1,y:2}
    let b=a
    b.x=5
    console.log(a.x)      //a.x==5
    ```
- object拷贝(浅拷贝，只有第一层被拷贝)
    ```javascript
    let a={x:1,y:2,c:[1,1,1]}
    let b={...a}
    b.x=2                 //a.x remains 1  
    b.c[1]=0              //a.c[0] changed to 0, array not copied
    ```
- object拷贝(深拷贝，所有层被拷贝)
    ```javascript
    let str=JSON.stringify(a)
    let b=JSON.parse(str)
    ```

---------------------------------------------------------

# 实战练习大纲4：“个人在线图书管理与统计系统”
一、 网页 HTML 结构要求 (index.html 骨架)
请设计一个布局清晰、语义化的单页面应用，页面中必须包含以下结构区块：

顶部导航/头部 (<header>)

一个主标题（如：<h1>个人在线图书管理与统计系统</h1>）。

一个副标题或标语（如：<p>掌握前端核心技术，管理你的数字书房</p>）。

第一部分：系统概览与环境面板 (<section id="env-panel">)

一个卡片容器，用来展示浏览器窗口与物理屏幕信息（利用你的笔记中的 window 和 screen 对象）。

需包含具体的文本占位符，例如：视口宽度、屏幕宽度、系统版本常量等。

第二部分：会员中心与逻辑测试区 (<section id="member-section">)

显示当前会员积分与等级的区域。

一个输入框（<input type="number">）供用户输入积分，以及一个按钮（“计算会员等级”）。

一个用于输出结果的文本区域。

第三部分：图书列表与解构/拷贝演示区 (<section id="book-section">)

一个区域用来展示预设的图书列表（可用 <ul> 或表格呈现）。

三个操作按钮：

“测试数组解构与剩余运算”

“测试对象深浅拷贝”

“测试 Proxy 代理作者名”

一个专属的输出结果展示面板（<div id="demo-result">）。

第四部分：云端远程公告板 (Fetch 联网区) (<section id="net-section">)

一个按钮：“获取最新云端公告”。

一个用于展示联网状态或远程返回数据的文本框/段落。

页脚 (<footer>)

版权信息，其中年份和作者名需要通过 JS 动态渲染。

二、 CSS 样式美化要求 (<style> 或外部样式)
为了让网页看起来像一个真正的现代管理后台，请用 CSS 实现以下视觉效果：

整体布局：

页面整体背景色使用柔和的浅灰色（如 #f0f2f5）。

主体内容最大宽度限制为 800px，居中显示，具有合适的内外边距。

卡片式设计 (Card Layout)：

每一个 <section> 或功能区块都要设计成“卡片”样式：白色背景、圆角（border-radius: 8px）、轻微的阴影（box-shadow）。

卡片内部要有舒适的内边距（padding: 20px）和块间距（margin-bottom: 20px）。

交互反馈与色彩：

按钮（<button>）要有明确的视觉样式：主色调（如蓝紫色 #4f46e5）、白色文字、圆角、鼠标悬停（:hover）时背景色加深或有轻微上移的动画效果。

输入框要有统一的内边距和边框圆角。

针对不同的状态（如高亮、警告、成功提示）设计不同的文字颜色类（如 .highlight { color: #e11d48; font-weight: bold; }）。

三、 JavaScript 核心功能要求 (<script type="module">)
请在页面中编写 JavaScript 代码，必须完整覆盖你笔记中的以下知识点：

基础语法与变量：

用 const 定义图书馆名称常量，用 let 定义初始积分为 50 的变量。

使用单行 // 和多行 /* */ 注释对代码模块进行说明。

流程控制与函数：

编写 checkLevel(score) 函数，用 if...else 根据积分返回等级（新手会员、中级会员、高级会员）。

编写一个 for 循环，结合 continue 和 break 在控制台打印特定逻辑。

编写一个箭头函数用于计算两本书的价格总和。

数组与解构赋值：

定义图书数组：let books = [{title: "JavaScript深入浅出", price: 88}, {title: "HTML/CSS精粹", price: 45}, {title: "前端工程化", price: 95}];

使用数组解构赋值（带默认值）提取前两本书的价格。

使用剩余运算 ... 将第一本书分出，其余书存入 otherBooks 变量。

深浅拷贝与 Proxy 代理：

对 books[0] 进行浅拷贝（用扩展运算符 {...}），并尝试修改其属性观察原对象变化；随后利用 JSON.parse(JSON.stringify(...)) 实现深拷贝。

创建一个作者对象 let author = {firstName: "Alan", middleName: "Mathison", lastName: "Turing"}，并为其编写一个 Proxy：当访问 myProxy.fullName 时，自动返回拼接好的全名。

DOM 操作与 Window/Screen：

在页面加载时，通过 window.innerWidth、window.screen.width 以及 document.querySelector 将视口宽度和屏幕宽度渲染到第一部分的面板中。

为各个按钮绑定事件，当用户点击时，动态修改对应区域的 innerHTML、className 或 style 属性（例如改变文字颜色、背景色）。

异步联网 (Fetch)：

点击“获取最新云端公告”按钮时，使用 fetch() 请求公开接口 [https://jsonplaceholder.typicode.com/posts/3](https://jsonplaceholder.typicode.com/posts/3)。

使用 .then() 和 .json() 处理响应，并将获取到的 title 实时显示在网页的公告板区域中。


参考答案：Examples/练习4_个人在线图书管理与统计系统.html