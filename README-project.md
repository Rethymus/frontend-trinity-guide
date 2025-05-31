# 完整案例实战
*Complete Project Practice*

[← 上一章：响应式布局](README-responsive.md) | [返回主文档](README.md)

## 📋 目录
- [项目概述](#项目概述)
- [技术架构](#技术架构)
- [项目结构](#项目结构)
- [核心功能实现](#核心功能实现)
- [代码实现](#代码实现)
- [版本对比](#版本对比)
- [部署与优化](#部署与优化)
- [扩展功能](#扩展功能)
- [总结与反思](#总结与反思)

## 项目概述

### 🎯 项目目标
构建一个现代化的个人作品展示网站，集成主题切换、响应式布局、表单交互和动态效果等功能，展示前端三剑客（HTML+CSS+JS）的综合应用。

### ✨ 核心功能
- **主题切换系统**：明暗主题无缝切换
- **响应式布局**：适配不同设备屏幕
- **动态导航**：平滑滚动与高亮显示
- **交互表单**：联系方式收集与验证
- **数据管理**：作品信息的增删改查
- **视觉效果**：CSS动画与JS交互结合

## 技术架构

### 🏗️ 架构设计
```
前端架构
├── 表现层 (HTML)
│   ├── 语义化结构
│   ├── SEO优化标签
│   └── 无障碍访问支持
├── 样式层 (CSS)
│   ├── CSS变量主题系统
│   ├── Flexbox/Grid布局
│   ├── 响应式媒体查询
│   └── 动画与过渡效果
└── 逻辑层 (JavaScript)
    ├── DOM操作与事件处理
    ├── 主题状态管理
    ├── 数据存储与检索
    └── 用户交互响应
```

### 🔄 数据流
```
用户操作 → 事件监听 → 状态更新 → DOM渲染 → 视觉反馈
```

## 项目结构

```
portfolio-website/
├── index.html              # 主页面
├── css/
│   ├── main.css            # 主样式文件
│   ├── themes.css          # 主题变量定义
│   └── responsive.css      # 响应式样式
├── js/
│   ├── main.js             # 主要逻辑
│   ├── theme-switcher.js   # 主题切换功能
│   ├── portfolio.js        # 作品管理功能
│   └── form-handler.js     # 表单处理功能
└── assets/
    ├── images/             # 图片资源
    └── icons/              # 图标文件
```

## 核心功能实现

### 🌓 主题切换系统

#### 实现原理
1. **CSS变量定义**：使用`:root`定义主题色彩变量
2. **状态管理**：JavaScript维护当前主题状态
3. **动态切换**：通过修改CSS类名实现主题切换
4. **持久化存储**：记住用户的主题偏好

#### 关键技术点
```css
/* CSS变量主题系统 */
:root {
  --primary-color: #007bff;
  --background-color: #ffffff;
  --text-color: #333333;
  --card-background: #f8f9fa;
}

[data-theme="dark"] {
  --primary-color: #4dabf7;
  --background-color: #1a1a1a;
  --text-color: #ffffff;
  --card-background: #2d2d2d;
}
```

### 📱 响应式布局策略

#### 断点设计
- **移动端**：< 768px
- **平板端**：768px - 1024px  
- **桌面端**：> 1024px

#### 布局技术
- **CSS Grid**：整体页面布局
- **Flexbox**：组件内部布局
- **媒体查询**：响应式适配

### 🎨 动画效果系统

#### 动画类型
1. **页面加载动画**：渐入效果
2. **主题切换动画**：平滑过渡
3. **交互反馈动画**：悬停效果
4. **滚动触发动画**：元素出现动画

## 代码实现

### HTML结构设计

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>个人作品集 - 前端开发者</title>
    <link rel="stylesheet" href="css/main.css">
    <link rel="stylesheet" href="css/themes.css">
    <link rel="stylesheet" href="css/responsive.css">
</head>
<body>
    <!-- 导航栏 -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <div class="nav-brand">
                <h2>Portfolio</h2>
            </div>
            <ul class="nav-menu" id="nav-menu">
                <li class="nav-item">
                    <a href="#home" class="nav-link">首页</a>
                </li>
                <li class="nav-item">
                    <a href="#about" class="nav-link">关于</a>
                </li>
                <li class="nav-item">
                    <a href="#projects" class="nav-link">项目</a>
                </li>
                <li class="nav-item">
                    <a href="#contact" class="nav-link">联系</a>
                </li>
            </ul>
            <!-- 主题切换按钮 -->
            <button class="theme-toggle" id="theme-toggle" aria-label="切换主题">
                <span class="theme-icon">🌙</span>
            </button>
            <!-- 移动端菜单按钮 -->
            <div class="hamburger" id="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- 主要内容区域 -->
    <main>
        <!-- 首页部分 -->
        <section id="home" class="hero">
            <div class="hero-content">
                <h1 class="hero-title">前端开发者</h1>
                <p class="hero-subtitle">专注于创造优美的用户体验</p>
                <button class="cta-button" onclick="scrollToSection('projects')">
                    查看作品
                </button>
            </div>
            <div class="hero-animation">
                <div class="floating-elements">
                    <div class="element html">HTML</div>
                    <div class="element css">CSS</div>
                    <div class="element js">JS</div>
                </div>
            </div>
        </section>

        <!-- 关于部分 -->
        <section id="about" class="about">
            <div class="container">
                <h2 class="section-title">关于我</h2>
                <div class="about-content">
                    <div class="about-text">
                        <p>我是一名热爱前端开发的工程师，专注于HTML、CSS、JavaScript的深度应用...</p>
                    </div>
                    <div class="skills">
                        <div class="skill-item">
                            <span class="skill-name">HTML/CSS</span>
                            <div class="skill-bar">
                                <div class="skill-progress" data-progress="90"></div>
                            </div>
                        </div>
                        <div class="skill-item">
                            <span class="skill-name">JavaScript</span>
                            <div class="skill-bar">
                                <div class="skill-progress" data-progress="85"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 项目展示部分 -->
        <section id="projects" class="projects">
            <div class="container">
                <h2 class="section-title">我的项目</h2>
                <div class="project-controls">
                    <button class="btn btn-primary" onclick="showAddProjectForm()">
                        添加项目
                    </button>
                    <div class="project-filters">
                        <button class="filter-btn active" data-filter="all">全部</button>
                        <button class="filter-btn" data-filter="web">网站</button>
                        <button class="filter-btn" data-filter="app">应用</button>
                    </div>
                </div>
                <div class="projects-grid" id="projects-grid">
                    <!-- 项目卡片将通过JS动态生成 -->
                </div>
            </div>
        </section>

        <!-- 联系表单部分 -->
        <section id="contact" class="contact">
            <div class="container">
                <h2 class="section-title">联系我</h2>
                <form class="contact-form" id="contact-form">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="name">姓名 *</label>
                            <input type="text" id="name" name="name" required>
                            <span class="error-message" id="name-error"></span>
                        </div>
                        <div class="form-group">
                            <label for="email">邮箱 *</label>
                            <input type="email" id="email" name="email" required>
                            <span class="error-message" id="email-error"></span>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="subject">主题</label>
                        <input type="text" id="subject" name="subject">
                    </div>
                    <div class="form-group">
                        <label for="message">消息 *</label>
                        <textarea id="message" name="message" rows="5" required></textarea>
                        <span class="error-message" id="message-error"></span>
                    </div>
                    <button type="submit" class="btn btn-primary">发送消息</button>
                </form>
            </div>
        </section>
    </main>

    <!-- 项目添加/编辑模态框 -->
    <div class="modal" id="project-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modal-title">添加项目</h3>
                <button class="modal-close" onclick="closeProjectModal()">&times;</button>
            </div>
            <form class="modal-form" id="project-form">
                <div class="form-group">
                    <label for="project-title">项目标题 *</label>
                    <input type="text" id="project-title" name="title" required>
                </div>
                <div class="form-group">
                    <label for="project-description">项目描述</label>
                    <textarea id="project-description" name="description" rows="3"></textarea>
                </div>
                <div class="form-group">
                    <label for="project-category">项目类别</label>
                    <select id="project-category" name="category">
                        <option value="web">网站</option>
                        <option value="app">应用</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="project-url">项目链接</label>
                    <input type="url" id="project-url" name="url">
                </div>
                <div class="modal-actions">
                    <button type="button" class="btn btn-secondary" onclick="closeProjectModal()">
                        取消
                    </button>
                    <button type="submit" class="btn btn-primary">保存</button>
                </div>
            </form>
        </div>
    </div>

    <!-- JavaScript文件引入 -->
    <script src="js/main.js"></script>
    <script src="js/theme-switcher.js"></script>
    <script src="js/portfolio.js"></script>
    <script src="js/form-handler.js"></script>
</body>
</html>
```

### CSS样式实现

#### 主题变量与基础样式
```css
/* themes.css - 主题系统 */
:root {
    /* 明亮主题 */
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --success-color: #28a745;
    --warning-color: #ffc107;
    --danger-color: #dc3545;
    
    --background-color: #ffffff;
    --surface-color: #f8f9fa;
    --card-background: #ffffff;
    --text-primary: #212529;
    --text-secondary: #6c757d;
    --text-muted: #868e96;
    
    --border-color: #dee2e6;
    --shadow-light: 0 2px 4px rgba(0,0,0,0.1);
    --shadow-medium: 0 4px 8px rgba(0,0,0,0.15);
    --shadow-heavy: 0 8px 16px rgba(0,0,0,0.2);
    
    --border-radius: 8px;
    --transition-speed: 0.3s;
}

[data-theme="dark"] {
    /* 暗黑主题 */
    --primary-color: #4dabf7;
    --secondary-color: #adb5bd;
    --success-color: #51cf66;
    --warning-color: #ffd43b;
    --danger-color: #ff6b6b;
    
    --background-color: #121212;
    --surface-color: #1e1e1e;
    --card-background: #2d2d2d;
    --text-primary: #ffffff;
    --text-secondary: #b3b3b3;
    --text-muted: #888888;
    
    --border-color: #444444;
    --shadow-light: 0 2px 4px rgba(0,0,0,0.3);
    --shadow-medium: 0 4px 8px rgba(0,0,0,0.4);
    --shadow-heavy: 0 8px 16px rgba(0,0,0,0.5);
}

/* 主题切换动画 */
* {
    transition: background-color var(--transition-speed) ease,
                color var(--transition-speed) ease,
                border-color var(--transition-speed) ease,
                box-shadow var(--transition-speed) ease;
}
```

#### 布局与组件样式
```css
/* main.css - 主要样式 */
/* 基础重置 */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    line-height: 1.6;
    color: var(--text-primary);
    background-color: var(--background-color);
    overflow-x: hidden;
}

/* 导航栏 */
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: var(--card-background);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid var(--border-color);
    z-index: 1000;
    transition: all var(--transition-speed) ease;
}

.nav-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 70px;
}

.nav-brand h2 {
    color: var(--primary-color);
    font-weight: 700;
}

.nav-menu {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav-link {
    text-decoration: none;
    color: var(--text-primary);
    font-weight: 500;
    padding: 0.5rem 1rem;
    border-radius: var(--border-radius);
    transition: all var(--transition-speed) ease;
    position: relative;
}

.nav-link:hover,
.nav-link.active {
    color: var(--primary-color);
    background-color: var(--surface-color);
}

/* 主题切换按钮 */
.theme-toggle {
    background: none;
    border: 2px solid var(--border-color);
    border-radius: 50%;
    width: 45px;
    height: 45px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    transition: all var(--transition-speed) ease;
}

.theme-toggle:hover {
    border-color: var(--primary-color);
    transform: rotate(180deg);
}

/* 首页英雄区域 */
.hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    background: linear-gradient(135deg, var(--background-color) 0%, var(--surface-color) 100%);
    overflow: hidden;
}

.hero-content {
    text-align: center;
    z-index: 2;
    animation: fadeInUp 1s ease-out;
}

.hero-title {
    font-size: clamp(2.5rem, 5vw, 4rem);
    font-weight: 700;
    margin-bottom: 1rem;
    background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.hero-subtitle {
    font-size: 1.25rem;
    color: var(--text-secondary);
    margin-bottom: 2rem;
}

.cta-button {
    background: var(--primary-color);
    color: white;
    border: none;
    padding: 1rem 2rem;
    font-size: 1.1rem;
    border-radius: var(--border-radius);
    cursor: pointer;
    transition: all var(--transition-speed) ease;
    box-shadow: var(--shadow-medium);
}

.cta-button:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-heavy);
}

/* 浮动动画元素 */
.hero-animation {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
}

.floating-elements {
    position: relative;
    width: 100%;
    height: 100%;
}

.element {
    position: absolute;
    padding: 0.5rem 1rem;
    background-color: var(--card-background);
    border: 2px solid var(--border-color);
    border-radius: var(--border-radius);
    font-weight: 600;
    animation: float 6s ease-in-out infinite;
    box-shadow: var(--shadow-light);
}

.element.html {
    top: 20%;
    left: 10%;
    color: #e34c26;
    border-color: #e34c26;
    animation-delay: 0s;
}

.element.css {
    top: 60%;
    right: 10%;
    color: #1572b6;
    border-color: #1572b6;
    animation-delay: 2s;
}

.element.js {
    bottom: 20%;
    left: 20%;
    color: #f7df1e;
    border-color: #f7df1e;
    animation-delay: 4s;
}

/* 项目网格 */
.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
}

.project-card {
    background-color: var(--card-background);
    border-radius: var(--border-radius);
    padding: 1.5rem;
    box-shadow: var(--shadow-light);
    transition: all var(--transition-speed) ease;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInUp 0.6s ease-out forwards;
}

.project-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-heavy);
}

.project-card h3 {
    color: var(--primary-color);
    margin-bottom: 0.5rem;
}

.project-card p {
    color: var(--text-secondary);
    margin-bottom: 1rem;
}

.project-actions {
    display: flex;
    gap: 0.5rem;
    justify-content: flex-end;
}

/* 表单样式 */
.contact-form {
    max-width: 600px;
    margin: 0 auto;
    background-color: var(--card-background);
    padding: 2rem;
    border-radius: var(--border-radius);
    box-shadow: var(--shadow-medium);
}

.form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
}

.form-group {
    margin-bottom: 1.5rem;
}

.form-group label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: 500;
    color: var(--text-primary);
}

.form-group input,
.form-group textarea,
.form-group select {
    width: 100%;
    padding: 0.75rem;
    border: 2px solid var(--border-color);
    border-radius: var(--border-radius);
    background-color: var(--background-color);
    color: var(--text-primary);
    font-size: 1rem;
    transition: all var(--transition-speed) ease;
}

.form-group input:focus,
.form-group textarea:focus,
.form-group select:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
}

.error-message {
    color: var(--danger-color);
    font-size: 0.875rem;
    margin-top: 0.25rem;
    display: block;
}

/* 模态框 */
.modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 2000;
    opacity: 0;
    transition: opacity var(--transition-speed) ease;
}

.modal.show {
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 1;
}

.modal-content {
    background-color: var(--card-background);
    border-radius: var(--border-radius);
    padding: 0;
    max-width: 500px;
    width: 90%;
    max-height: 90vh;
    overflow-y: auto;
    transform: scale(0.7);
    transition: transform var(--transition-speed) ease;
}

.modal.show .modal-content {
    transform: scale(1);
}

/* 动画定义 */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes float {
    0%, 100% {
        transform: translateY(0px);
    }
    50% {
        transform: translateY(-20px);
    }
}

@keyframes pulse {
    0% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.05);
    }
    100% {
        transform: scale(1);
    }
}

/* 工具类 */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
}

.section-title {
    font-size: 2.5rem;
    font-weight: 700;
    text-align: center;
    margin-bottom: 3rem;
    color: var(--text-primary);
}

.btn {
    padding: 0.5rem 1rem;
    border: none;
    border-radius: var(--border-radius);
    cursor: pointer;
    font-size: 0.9rem;
    font-weight: 500;
    transition: all var(--transition-speed) ease;
    text-decoration: none;
    display: inline-block;
    text-align: center;
}

.btn-primary {
    background-color: var(--primary-color);
    color: white;
}

.btn-secondary {
    background-color: var(--secondary-color);
    color: white;
}

.btn-danger {
    background-color: var(--danger-color);
    color: white;
}

.btn:hover {
    transform: translateY(-1px);
    box-shadow: var(--shadow-medium);
}
```

#### 响应式设计
```css
/* responsive.css - 响应式样式 */
/* 平板设备 */
@media (max-width: 1024px) {
    .nav-container {
        padding: 0 1rem;
    }
    
    .hero-title {
        font-size: 3rem;
    }
    
    .projects-grid {
        grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
        gap: 1.5rem;
    }
    
    .container {
        padding: 0 1rem;
    }
}

/* 移动设备 */
@media (max-width: 768px) {
    /* 导航栏移动端适配 */
    .nav-menu {
        position: fixed;
        top: 70px;
        left: -100%;
        width: 100%;
        height: calc(100vh - 70px);
        background-color: var(--card-background);
        flex-direction: column;
        justify-content: start;
        align-items: center;
        padding-top: 2rem;
        transition: left var(--transition-speed) ease;
    }
    
    .nav-menu.active {
        left: 0;
    }
    
    .hamburger {
        display: flex;
        flex-direction: column;
        cursor: pointer;
        gap: 4px;
    }
    
    .hamburger span {
        width: 25px;
        height: 3px;
        background-color: var(--text-primary);
        transition: all var(--transition-speed) ease;
    }
    
    .hamburger.active span:nth-child(1) {
        transform: rotate(45deg) translate(5px, 5px);
    }
    
    .hamburger.active span:nth-child(2) {
        opacity: 0;
    }
    
    .hamburger.active span:nth-child(3) {
        transform: rotate(-45deg) translate(7px, -6px);
    }
    
    /* 内容适配 */
    .hero-title {
        font-size: 2.5rem;
    }
    
    .hero-subtitle {
        font-size: 1.1rem;
    }
    
    .projects-grid {
        grid-template-columns: 1fr;
        gap: 1rem;
    }
    
    .form-row {
        grid-template-columns: 1fr;
    }
    
    .modal-content {
        width: 95%;
        margin: 1rem;
    }
    
    .section-title {
        font-size: 2rem;
    }
    
    /* 隐藏桌面端显示的汉堡菜单 */
    .hamburger {
        display: none;
    }
}

@media (max-width: 768px) {
    .hamburger {
        display: flex;
    }
}

/* 小屏幕设备 */
@media (max-width: 480px) {
    .nav-container {
        padding: 0 0.5rem;
    }
    
    .hero-title {
        font-size: 2rem;
    }
    
    .cta-button {
        padding: 0.75rem 1.5rem;
        font-size: 1rem;
    }
    
    .contact-form {
        padding: 1rem;
    }
    
    .project-card {
        padding: 1rem;
    }
}

/* 高分辨率屏幕优化 */
@media (min-width: 1400px) {
    .container {
        max-width: 1400px;
    }
    
    .hero-title {
        font-size: 5rem;
    }
    
    .projects-grid {
        grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
    }
}

/* 打印样式 */
@media print {
    .navbar,
    .theme-toggle,
    .hamburger,
    .modal,
    .project-actions {
        display: none;
    }
    
    body {
        background-color: white;
        color: black;
    }
    
    .hero {
        min-height: auto;
        padding: 2rem 0;
    }
}
```

### JavaScript核心功能

#### 主题切换系统
```javascript
// theme-switcher.js - 主题切换功能
class ThemeSwitcher {
    constructor() {
        this.themeToggle = document.getElementById('theme-toggle');
        this.themeIcon = this.themeToggle.querySelector('.theme-icon');
        this.currentTheme = this.getStoredTheme() || 'light';
        this.init();
    }

    init() {
        // 设置初始主题
        this.setTheme(this.currentTheme);
        
        // 绑定切换事件
        this.themeToggle.addEventListener('click', () => {
            this.toggleTheme();
        });
        
        // 监听系统主题变化
        this.watchSystemTheme();
    }

    toggleTheme() {
        const newTheme = this.currentTheme === 'light' ? 'dark' : 'light';
        this.setTheme(newTheme);
        
        // 添加切换动画效果
        this.animateThemeSwitch();
    }

    setTheme(theme) {
        this.currentTheme = theme;
        document.documentElement.setAttribute('data-theme', theme);
        this.updateThemeIcon(theme);
        this.storeTheme(theme);
        
        // 触发主题变更事件
        window.dispatchEvent(new CustomEvent('themechange', {
            detail: { theme }
        }));
    }

    updateThemeIcon(theme) {
        this.themeIcon.textContent = theme === 'light' ? '🌙' : '☀️';
    }

    animateThemeSwitch() {
        // 创建切换动画效果
        const overlay = document.createElement('div');
        overlay.style.cssText = `
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: ${this.currentTheme === 'dark' ? '#000' : '#fff'};
            opacity: 0;
            pointer-events: none;
            z-index: 9999;
            transition: opacity 0.3s ease;
        `;
        
        document.body.appendChild(overlay);
        
        // 触发动画
        requestAnimationFrame(() => {
            overlay.style.opacity = '0.3';
            setTimeout(() => {
                overlay.style.opacity = '0';
                setTimeout(() => {
                    document.body.removeChild(overlay);
                }, 300);
            }, 150);
        });
    }

    getStoredTheme() {
        try {
            return localStorage.getItem('portfolio-theme');
        } catch (e) {
            return null;
        }
    }

    storeTheme(theme) {
        try {
            localStorage.setItem('portfolio-theme', theme);
        } catch (e) {
            console.warn('无法保存主题设置');
        }
    }

    watchSystemTheme() {
        if (window.matchMedia) {
            const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
            mediaQuery.addEventListener('change', (e) => {
                if (!this.getStoredTheme()) {
                    this.setTheme(e.matches ? 'dark' : 'light');
                }
            });
        }
    }
}

// 初始化主题切换器
document.addEventListener('DOMContentLoaded', () => {
    new ThemeSwitcher();
});
```

#### 作品管理系统
```javascript
// portfolio.js - 作品管理功能
class PortfolioManager {
    constructor() {
        this.projects = this.loadProjects();
        this.currentFilter = 'all';
        this.editingProject = null;
        this.init();
    }

    init() {
        this.renderProjects();
        this.bindEvents();
        this.initAnimations();
    }

    bindEvents() {
        // 筛选按钮事件
        document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                this.setFilter(e.target.dataset.filter);
            });
        });

        // 项目表单提交
        document.getElementById('project-form').addEventListener('submit', (e) => {
            e.preventDefault();
            this.handleProjectSubmit(e);
        });

        // 模态框关闭事件
        document.addEventListener('click', (e) => {
            if (e.target.classList.contains('modal')) {
                this.closeProjectModal();
            }
        });
    }

    loadProjects() {
        try {
            const stored = localStorage.getItem('portfolio-projects');
            return stored ? JSON.parse(stored) : this.getDefaultProjects();
        } catch (e) {
            return this.getDefaultProjects();
        }
    }

    saveProjects() {
        try {
            localStorage.setItem('portfolio-projects', JSON.stringify(this.projects));
        } catch (e) {
            console.warn('无法保存项目数据');
        }
    }

    getDefaultProjects() {
        return [
            {
                id: 1,
                title: '响应式企业网站',
                description: '使用HTML5、CSS3和JavaScript开发的现代化企业展示网站',
                category: 'web',
                url: '#',
                image: 'assets/images/project1.jpg',
                technologies: ['HTML5', 'CSS3', 'JavaScript'],
                createdAt: new Date().toISOString()
            },
            {
                id: 2,
                title: '任务管理应用',
                description: '基于本地存储的任务管理工具，支持增删改查操作',
                category: 'app',
                url: '#',
                image: 'assets/images/project2.jpg',
                technologies: ['JavaScript', 'LocalStorage', 'CSS Grid'],
                createdAt: new Date().toISOString()
            }
        ];
    }

    renderProjects() {
        const container = document.getElementById('projects-grid');
        const filteredProjects = this.currentFilter === 'all' 
            ? this.projects 
            : this.projects.filter(p => p.category === this.currentFilter);

        container.innerHTML = filteredProjects.map(project => `
            <div class="project-card" data-category="${project.category}">
                <div class="project-image">
                    <img src="${project.image}" alt="${project.title}" onerror="this.style.display='none'">
                </div>
                <div class="project-content">
                    <h3>${project.title}</h3>
                    <p>${project.description}</p>
                    <div class="project-technologies">
                        ${project.technologies.map(tech => `<span class="tech-tag">${tech}</span>`).join('')}
                    </div>
                </div>
                <div class="project-actions">
                    ${project.url !== '#' ? `<a href="${project.url}" target="_blank" class="btn btn-primary btn-sm">查看</a>` : ''}
                    <button onclick="portfolioManager.editProject(${project.id})" class="btn btn-secondary btn-sm">编辑</button>
                    <button onclick="portfolioManager.deleteProject(${project.id})" class="btn btn-danger btn-sm">删除</button>
                </div>
            </div>
        `).join('');

        // 触发入场动画
        this.animateProjectCards();
    }

    setFilter(filter) {
        this.currentFilter = filter;
        
        // 更新按钮状态
        document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.classList.toggle('active', btn.dataset.filter === filter);
        });
        
        this.renderProjects();
    }

    showAddProjectForm() {
        this.editingProject = null;
        document.getElementById('modal-title').textContent = '添加项目';
        document.getElementById('project-form').reset();
        this.showProjectModal();
    }

    editProject(id) {
        this.editingProject = this.projects.find(p => p.id === id);
        if (this.editingProject) {
            document.getElementById('modal-title').textContent = '编辑项目';
            this.populateProjectForm(this.editingProject);
            this.showProjectModal();
        }
    }

    deleteProject(id) {
        if (confirm('确定要删除这个项目吗？')) {
            this.projects = this.projects.filter(p => p.id !== id);
            this.saveProjects();
            this.renderProjects();
            this.showNotification('项目已删除', 'success');
        }
    }

    handleProjectSubmit(e) {
        const formData = new FormData(e.target);
        const projectData = {
            title: formData.get('title'),
            description: formData.get('description'),
            category: formData.get('category'),
            url: formData.get('url') || '#',
            technologies: ['HTML', 'CSS', 'JavaScript'], // 简化处理
            image: 'assets/images/default-project.jpg'
        };

        if (this.editingProject) {
            // 编辑现有项目
            Object.assign(this.editingProject, projectData);
            this.showNotification('项目已更新', 'success');
        } else {
            // 添加新项目
            projectData.id = Date.now();
            projectData.createdAt = new Date().toISOString();
            this.projects.unshift(projectData);
            this.showNotification('项目已添加', 'success');
        }

        this.saveProjects();
        this.renderProjects();
        this.closeProjectModal();
    }

    populateProjectForm(project) {
        document.getElementById('project-title').value = project.title;
        document.getElementById('project-description').value = project.description;
        document.getElementById('project-category').value = project.category;
        document.getElementById('project-url').value = project.url === '#' ? '' : project.url;
    }

    showProjectModal() {
        const modal = document.getElementById('project-modal');
        modal.classList.add('show');
        document.body.style.overflow = 'hidden';
    }

    closeProjectModal() {
        const modal = document.getElementById('project-modal');
        modal.classList.remove('show');
        document.body.style.overflow = '';
        this.editingProject = null;
    }

    animateProjectCards() {
        const cards = document.querySelectorAll('.project-card');
        cards.forEach((card, index) => {
            card.style.animationDelay = `${index * 0.1}s`;
            card.classList.add('animate-in');
        });
    }

    initAnimations() {
        // 滚动触发动画
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('animate-in');
                }
            });
        }, { threshold: 0.1 });

        // 观察所有需要动画的元素
        document.querySelectorAll('.project-card, .section-title').forEach(el => {
            observer.observe(el);
        });
    }

    showNotification(message, type = 'info') {
        // 创建通知元素
        const notification = document.createElement('div');
        notification.className = `notification notification-${type}`;
        notification.textContent = message;
        notification.style.cssText = `
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 1rem 1.5rem;
            background-color: var(--${type === 'success' ? 'success' : 'primary'}-color);
            color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-medium);
            z-index: 3000;
            transform: translateX(100%);
            transition: transform 0.3s ease;
        `;

        document.body.appendChild(notification);

        // 显示动画
        requestAnimationFrame(() => {
            notification.style.transform = 'translateX(0)';
        });

        // 自动消失
        setTimeout(() => {
            notification.style.transform = 'translateX(100%)';
            setTimeout(() => {
                document.body.removeChild(notification);
            }, 300);
        }, 3000);
    }
}

// 全局变量，供HTML调用
let portfolioManager;

// 初始化作品管理器
document.addEventListener('DOMContentLoaded', () => {
    portfolioManager = new PortfolioManager();
});

// 全局函数，供HTML调用
function showAddProjectForm() {
    portfolioManager.showAddProjectForm();
}

function closeProjectModal() {
    portfolioManager.closeProjectModal();
}
```

#### 表单处理与验证
```javascript
// form-handler.js - 表单处理功能
class FormHandler {
    constructor() {
        this.contactForm = document.getElementById('contact-form');
        this.init();
    }

    init() {
        this.bindEvents();
        this.initValidation();
    }

    bindEvents() {
        this.contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            this.handleContactSubmit(e);
        });

        // 实时验证
        this.contactForm.querySelectorAll('input, textarea').forEach(field => {
            field.addEventListener('blur', () => {
                this.validateField(field);
            });

            field.addEventListener('input', () => {
                this.clearFieldError(field);
            });
        });
    }

    initValidation() {
        this.validators = {
            name: {
                required: true,
                minLength: 2,
                pattern: /^[a-zA-Z\u4e00-\u9fa5\s]+$/,
                message: '请输入有效的姓名'
            },
            email: {
                required: true,
                pattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
                message: '请输入有效的邮箱地址'
            },
            message: {
                required: true,
                minLength: 10,
                message: '消息内容至少需要10个字符'
            }
        };
    }

    validateField(field) {
        const validator = this.validators[field.name];
        if (!validator) return true;

        const value = field.value.trim();
        const errorElement = document.getElementById(`${field.name}-error`);

        // 必填验证
        if (validator.required && !value) {
            this.showFieldError(field, errorElement, '此字段为必填项');
            return false;
        }

        // 最小长度验证
        if (validator.minLength && value.length < validator.minLength) {
            this.showFieldError(field, errorElement, `至少需要${validator.minLength}个字符`);
            return false;
        }

        // 正则验证
        if (validator.pattern && !validator.pattern.test(value)) {
            this.showFieldError(field, errorElement, validator.message);
            return false;
        }

        // 验证通过
        this.clearFieldError(field);
        return true;
    }

    showFieldError(field, errorElement, message) {
        field.classList.add('error');
        if (errorElement) {
            errorElement.textContent = message;
        }
    }

    clearFieldError(field) {
        field.classList.remove('error');
        const errorElement = document.getElementById(`${field.name}-error`);
        if (errorElement) {
            errorElement.textContent = '';
        }
    }

    validateForm() {
        let isValid = true;
        const fields = this.contactForm.querySelectorAll('input[required], textarea[required]');
        
        fields.forEach(field => {
            if (!this.validateField(field)) {
                isValid = false;
            }
        });

        return isValid;
    }

    async handleContactSubmit(e) {
        if (!this.validateForm()) {
            this.showFormMessage('请检查并填写所有必填字段', 'error');
            return;
        }

        const submitButton = this.contactForm.querySelector('button[type="submit"]');
        const originalText = submitButton.textContent;

        try {
            // 显示加载状态
            submitButton.textContent = '发送中...';
            submitButton.disabled = true;

            // 获取表单数据
            const formData = new FormData(this.contactForm);
            const contactData = {
                name: formData.get('name'),
                email: formData.get('email'),
                subject: formData.get('subject'),
                message: formData.get('message'),
                timestamp: new Date().toISOString()
            };

            // 模拟发送过程
            await this.simulateEmailSend(contactData);

            // 保存到本地存储（实际项目中应该发送到服务器）
            this.saveContactMessage(contactData);

            // 显示成功消息
            this.showFormMessage('消息发送成功！我会尽快回复您。', 'success');
            this.contactForm.reset();

        } catch (error) {
            this.showFormMessage('发送失败，请稍后重试。', 'error');
            console.error('Contact form error:', error);
        } finally {
            // 恢复按钮状态
            submitButton.textContent = originalText;
            submitButton.disabled = false;
        }
    }

    async simulateEmailSend(data) {
        // 模拟网络请求延迟
        return new Promise((resolve) => {
            setTimeout(resolve, 1500);
        });
    }

    saveContactMessage(data) {
        try {
            const messages = JSON.parse(localStorage.getItem('contact-messages'