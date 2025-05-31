# 基础语法整合应用
*HTML+CSS+JS Foundation*

[← 返回主文档](README.md) | [下一章：表单交互设计 →](README-form.md)

## 📋 本章概览

本章将系统介绍HTML、CSS、JavaScript的基础语法，并通过实际代码示例展示三种技术的协作应用。

## 🏗️ HTML 结构基础

### 语义化标签应用

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>语义化网页结构</title>
</head>
<body>
    <header>
        <h1>网站标题</h1>
        <nav>导航菜单</nav>
    </header>
    
    <main>
        <article>
            <h2>文章标题</h2>
            <p>文章内容段落</p>
        </article>
        
        <aside>侧边栏内容</aside>
    </main>
    
    <footer>页脚信息</footer>
</body>
</html>
```

### 常用标签分类

| 类型 | 标签 | 用途 | 示例 |
|------|------|------|------|
| 文本 | `h1-h6`, `p`, `span` | 标题与段落 | `<h1>主标题</h1>` |
| 格式 | `b`, `i`, `u`, `s` | 文本样式 | `<b>粗体文本</b>` |
| 列表 | `ul`, `ol`, `li` | 有序/无序列表 | `<ul><li>项目</li></ul>` |
| 媒体 | `img`, `audio`, `video` | 多媒体内容 | `<img src="pic.jpg" alt="图片">` |
| 链接 | `a` | 超链接 | `<a href="url">链接文本</a>` |

## 🎨 CSS 样式控制

### 选择器优先级与应用

```css
/* 1. 通用选择器 - 优先级最低 */
* {
    font-family: 'KaiTi';
    box-sizing: border-box;
}

/* 2. 元素选择器 */
h2 {
    color: aqua;
    margin: 16px 0;
}

/* 3. 类选择器 */
.highlight {
    background-color: yellow;
    padding: 4px 8px;
}

/* 4. ID选择器 - 优先级高 */
#header {
    color: red;
    font-size: 35px;
}

/* 5. 组合选择器 */
.father > .son {          /* 子元素选择器 */
    color: red;
}

.father p {               /* 后代选择器 */
    color: brown;
    font-size: large;
}

h3 + p {                  /* 相邻兄弟选择器 */
    background-color: red;
}

/* 6. 伪类选择器 */
#element:hover {
    background-color: blueviolet;
    transition: background-color 0.3s ease;
}
```

### 盒模型与布局

```css
.layout-demo {
    /* 盒模型组成 */
    width: 300px;           /* 内容宽度 */
    height: 200px;          /* 内容高度 */
    padding: 20px;          /* 内边距 */
    border: 5px solid blue; /* 边框 */
    margin: 10px;           /* 外边距 */
    
    /* 边框样式详解 */
    border-style: solid dashed dotted double; /* 上右下左 */
    border-width: 5px 10px 15px 20px;
    border-color: red green blue yellow;
}

/* 浮动布局 */
.container {
    background-color: aquamarine;
    height: 150px;
    border: 3px solid burlywood;
    overflow: hidden; /* 清除浮动方法1 */
}

.left-float {
    width: 100px;
    height: 100px;
    background-color: yellowgreen;
    float: left;
}

.right-float {
    width: 100px;
    height: 100px;
    background-color: yellow;
    float: right;
}

/* 清除浮动方法2：伪元素 */
.container::after {
    content: "";
    display: table;
    clear: both;
}
```

## ⚡ JavaScript 交互逻辑

### 基础语法结构

```javascript
// 1. 变量声明（推荐使用let/const）
let userName = "张三";
const maxAttempts = 3;

// 2. 条件判断
let time = new Date().getHours();
if (time < 12) {
    console.log("早上好");
} else if (time < 18) {
    console.log("下午好");
} else {
    console.log("晚上好");
}

// 3. 循环结构
console.log("=== For循环 ===");
for (let i = 0; i < 5; i++) {
    console.log(`第${i + 1}次循环`);
}

console.log("=== While循环 ===");
let count = 1;
while (count <= 3) {
    console.log(`计数：${count}`);
    count++;
}

// 4. Switch语句
switch (new Date().getDay()) {
    case 1:
        console.log("周一");
        break;
    case 2:
        console.log("周二");
        break;
    default:
        console.log("其他日期");
}
```

### 函数定义与作用域

```javascript
// 1. 基础函数
function greet() {
    console.log("Hello World!");
}

// 2. 带参数函数
function greetUser(name) {
    console.log(`Hello, ${name}!`);
}

// 3. 带返回值函数
function calculateSum(a, b) {
    return a + b;
}

// 4. 作用域演示
let globalVar = "全局变量";

function scopeDemo() {
    let localVar = "局部变量";
    console.log("函数内访问全局变量:", globalVar);
    console.log("函数内访问局部变量:", localVar);
}

scopeDemo();
// console.log(localVar); // 错误：无法在函数外访问局部变量
```

### 事件处理机制

```javascript
// 1. 点击事件
function handleClick() {
    alert("按钮被点击了！");
}

// 2. 表单事件
function handleFocus() {
    console.log("输入框获得焦点");
}

function handleBlur() {
    console.log("输入框失去焦点");
}

// 3. 常用事件类型总结
const eventTypes = {
    mouse: ['click', 'mouseover', 'mouseout'],
    keyboard: ['keydown', 'keyup', 'keypress'],
    form: ['focus', 'blur', 'change', 'submit'],
    window: ['load', 'resize', 'scroll']
};
```

## 🎯 三技术协作示例

### 完整的交互组件

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>计数器组件</title>
    <style>
        .counter-container {
            max-width: 300px;
            margin: 50px auto;
            text-align: center;
            padding: 20px;
            border: 2px solid #007bff;
            border-radius: 8px;
            background-color: #f8f9fa;
        }
        
        .counter-display {
            font-size: 48px;
            font-weight: bold;
            color: #007bff;
            margin: 20px 0;
        }
        
        .counter-btn {
            font-size: 18px;
            padding: 10px 20px;
            margin: 0 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        
        .btn-increase {
            background-color: #28a745;
            color: white;
        }
        
        .btn-decrease {
            background-color: #dc3545;
            color: white;
        }
        
        .counter-btn:hover {
            opacity: 0.8;
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div class="counter-container">
        <h2>计数器演示</h2>
        <div class="counter-display" id="counterValue">0</div>
        <button class="counter-btn btn-increase" onclick="increment()">+1</button>
        <button class="counter-btn btn-decrease" onclick="decrement()">-1</button>
        <button class="counter-btn" onclick="reset()" style="background-color: #6c757d; color: white;">重置</button>
    </div>

    <script>
        let count = 0;
        const display = document.getElementById('counterValue');
        
        function increment() {
            count++;
            updateDisplay();
        }
        
        function decrement() {
            count--;
            updateDisplay();
        }
        
        function reset() {
            count = 0;
            updateDisplay();
        }
        
        function updateDisplay() {
            display.textContent = count;
            
            // 根据数值改变颜色
            if (count > 0) {
                display.style.color = '#28a745';
            } else if (count < 0) {
                display.style.color = '#dc3545';
            } else {
                display.style.color = '#007bff';
            }
        }
    </script>
</body>
</html>
```

## 📊 版本对比与适用场景

### HTML版本演进

| 版本 | 特点 | 适用场景 |
|------|------|----------|
| HTML4 | 基础标签、表格布局 | 传统网页 |
| XHTML | 严格XML语法 | 企业级应用 |
| HTML5 | 语义化标签、多媒体支持 | 现代Web应用 |

### CSS技术选择

| 技术 | 优势 | 劣势 | 使用建议 |
|------|------|------|----------|
| 原生CSS | 直接、轻量 | 维护困难 | 小型项目 |
| CSS预处理器 | 变量、嵌套 | 编译步骤 | 中大型项目 |
| CSS框架 | 快速开发 | 体积较大 | 原型开发 |

### JavaScript应用层次

| 应用类型 | 技术栈 | 复杂度 | 学习建议 |
|----------|--------|--------|----------|
| 基础交互 | 原生JS + DOM | ⭐⭐ | 本章重点 |
| SPA应用 | React/Vue | ⭐⭐⭐⭐ | 进阶学习 |
| 全栈开发 | Node.js | ⭐⭐⭐⭐⭐ | 深度专业 |

## ⚠️ 注意事项

### 常见错误避免

1. **HTML结构错误**
   ```html
   <!-- 错误：标签未闭合 -->
   <p>段落内容
   
   <!-- 正确：标签正确闭合 -->
   <p>段落内容</p>
   ```

2. **CSS选择器冲突**
   ```css
   /* 避免过度使用!important */
   .element {
       color: red !important; /* 不推荐 */
   }
   
   /* 推荐：提高选择器权重 */
   .container .element {
       color: red;
   }
   ```

3. **JavaScript变量提升**
   ```javascript
   // 避免var的变量提升问题
   console.log(x); // undefined，而不是报错
   var x = 5;
   
   // 推荐使用let/const
   console.log(y); // ReferenceError
   let y = 5;
   ```

### 最佳实践

1. **语义化HTML**：使用合适的标签表达内容含义
2. **模块化CSS**：合理组织样式，避免选择器嵌套过深
3. **渐进增强**：确保基础功能在禁用JavaScript时依然可用
4. **性能优化**：压缩代码、减少HTTP请求、优化图片

## 🔗 相关链接

- [表单交互设计 →](README-form.md)
- [动态效果实现 →](README-animation.md)
- [响应式布局 →](README-responsive.md)
- [完整案例实战 →](README-project.md)

---

*掌握这些基础语法后，您就可以开始构建更复杂的Web应用了！*