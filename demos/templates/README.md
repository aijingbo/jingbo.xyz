# Demo 详情页框架系统

> 所有 Demo 详情页的通用外壳 + 四种呈现框架模板

## 文件结构

```
assets/css/
  design-system.css      ← 基础设计系统（CSS 变量、按钮、标签、卡片等）
  demo-framework.css     ← Demo 详情页框架样式（依赖 design-system.css）

demos/templates/
  framework-1-immersive.html    ← 框架一：沉浸式全屏型
  framework-2-magazine.html     ← 框架二：杂志讲解型
  framework-3-interactive.html  ← 框架三：交互工具型
  framework-4-narrative.html    ← 框架四：时空叙事型
  README.md                     ← 本文档
```

## 快速开始

1. **复制对应框架的模板文件**到你的 Demo 目录
2. **引入两个 CSS 文件**：
   ```html
   <link rel="stylesheet" href="/assets/css/design-system.css" />
   <link rel="stylesheet" href="/assets/css/demo-framework.css" />
   ```
3. **替换占位内容**为你的实际 Demo 内容
4. 每个 Demo 是独立的单文件 HTML，第三方库用 CDN

---

## 通用外壳

所有框架共享统一的顶部导航栏，由 `.demo-navbar` 提供。

### 导航栏结构

```html
<header class="demo-navbar" id="demoNavbar">
  <!-- 左侧：返回 + Logo -->
  <div class="demo-nav-left">
    <a href="/demos.html" class="demo-back-link">
      <svg>...</svg> 返回
    </a>
    <span class="demo-nav-divider"></span>
    <a href="/" class="demo-nav-logo">景礴</a>
  </div>
  <!-- 中间：标题 -->
  <div class="demo-nav-center">Demo 标题</div>
  <!-- 右侧：学科标签 + 下载按钮 -->
  <div class="demo-nav-right">
    <span class="tag tag-math">数学</span>
    <a href="/skills.html" class="demo-btn-download">
      <svg>...</svg> <span>下载 Skill</span>
    </a>
  </div>
</header>
```

### 深色模式（沉浸式）

给导航栏添加 `immersive` 类即可切换深色模式：

```html
<header class="demo-navbar immersive">
```

### 滚动收缩效果

```javascript
const navbar = document.getElementById('demoNavbar');
window.addEventListener('scroll', () => {
  navbar.classList.toggle('scrolled', window.scrollY > 10);
});
```

### 底部信息条（可选）

```html
<footer class="demo-info-bar">
  <div class="demo-info-left">
    <span class="demo-info-title">skill-name</span>
    <span class="demo-tech-tag">技术栈</span>
  </div>
  <div class="demo-info-right">
    <a href="..." class="demo-info-link">相关链接</a>
  </div>
</footer>
```

> 如果使用了底部信息条，需在 `<body>` 上添加 `has-info-bar` 类，
> 浮动控件会自动上移避开信息条。

---

## 四种框架

### 框架一：沉浸式全屏型

**适用**：3D 分子、DNA、太阳系、晶体结构等空间结构类

**特点**：全屏画布、深色背景、UI 极简半透明

**关键类**：
- `body.has-info-bar` — 有底部信息条时添加
- `.framework-immersive` — 框架容器
- `.demo-canvas-full` — 全屏画布容器
- `.demo-floating-panel` — 半透明浮动面板（左上/右上）
- `.demo-floating-group` + `.demo-floating-left/right` — 浮动按钮组
- `.demo-icon-btn` — 圆形图标按钮（支持 `data-tooltip`）
- `.demo-scene-hint` — 操作提示文字
- `.demo-mode-switcher` + `.demo-mode-btn` — 模式切换器

**模板参考**：`framework-1-immersive.html`

---

### 框架二：杂志讲解型

**适用**：几何证明、历史时间轴、傅里叶讲解等知识讲解类

**特点**：左右分栏（40% 文字 + 60% 可视化），步骤导航

**关键类**：
- `.framework-magazine` — 框架容器
- `.magazine-layout` — 左右分栏网格
- `.magazine-article` — 左侧文章区
- `.magazine-kicker` — 小标题标签（mono 字体）
- `.magazine-title` — 大标题（衬线字体）
- `.magazine-step-indicator` — 步骤导航
- `.magazine-step-dot` — 步骤圆点（`.active` / `.completed`）
- `.magazine-step-content` — 步骤内容（支持 fade 过渡）
- `.magazine-proof-step` — 证明步骤块
- `.magazine-theorem-box` — 定理高亮框
- `.magazine-visual` — 右侧可视化区
- `.magazine-visual-wrapper` — 可视化画布容器（带边框）

**模板参考**：`framework-2-magazine.html`

---

### 框架三：交互工具型

**适用**：圆锥曲线、抛体运动、排序算法等参数调节类

**特点**：上下分栏（画布 80% + 控制面板 20%），精密仪器感

**关键类**：
- `body.has-info-bar` — 有底部信息条时添加
- `.framework-interactive` — 框架容器（flex 纵向）
- `.interactive-main` — 主区域（含 padding-top 避开导航栏）
- `.interactive-canvas-area` — 画布区（flex:1）
- `.interactive-data-display` — 数据显示卡片（右上浮动）
- `.interactive-control-panel` — 控制面板（固定高度）
- `.control-sliders` — 滑块组容器
- `.control-slider-group` — 单个滑块组
- `.control-slider` — 自定义样式滑块
- `.control-buttons` — 按钮组容器
- `.control-btn` — 功能按钮（支持 `.active`）
- `.control-btn-play` — 播放按钮（大号圆形）

**模板参考**：`framework-3-interactive.html`

---

### 框架四：时空叙事型

**适用**：历史路线、战役进程、丝绸之路等地图 + 时间类

**特点**：左右分栏（地图 70% + 时间轴 30%），联动交互

**关键类**：
- `.framework-narrative` — 框架容器
- `.narrative-main` — 主区域（grid 70%/30%）
- `.narrative-map-area` — 地图区域
- `.narrative-info-card` — 信息卡片（左下浮动，支持 `.hidden`）
- `.narrative-timeline-panel` — 时间轴面板
- `.narrative-timeline-header` — 时间轴标题区
- `.narrative-timeline-list` — 事件列表（有竖线）
- `.timeline-event` — 事件项（支持 `.active`）
- `.timeline-event-dot` — 事件圆点
- `.narrative-timeline-footer` — 底部播放控件
- `.narrative-play-btn` — 播放按钮
- `.narrative-progress` / `.narrative-progress-bar` — 进度条

**交互模式**：
- 点击时间轴事件 → 地图高亮对应标记 + 更新信息卡片
- 点击地图标记 → 时间轴跳转
- 播放按钮 → 自动按顺序切换

**模板参考**：`framework-4-narrative.html`

---

## 设计规范

### 配色

| 模式 | 背景 | 文字 | 强调 |
|------|------|------|------|
| 浅色 | `#faf8f5` 暖米白 | `#1a1a1a` 深炭灰 | `#c2410c` 赤陶色 |
| 深色（沉浸式） | `#0a0a0f` 深灰近黑 | `#e5e5e5` 浅灰 | `#c2410c` 赤陶色 |

学科色仅用于小面积标记，参见 `design-system.css` 中的 `--accent-*` 变量。

### 字体

| 用途 | 字体 | CSS 变量 |
|------|------|----------|
| 标题 | Noto Serif SC | `--font-serif` |
| 正文 | Noto Sans SC | `--font-sans` |
| 数据/代码 | JetBrains Mono | `--font-mono` |

### 控件圆角

| 控件 | 圆角 | CSS 变量 |
|------|------|----------|
| 按钮 | 6px | `--radius` |
| 标签 | 药丸形 | `--radius-full` |
| 卡片 | 12px | `--radius-card` |
| 图标按钮 | 圆形 | `--radius-full` |

### 响应式断点

- `1024px`：杂志型切单列、叙事型切上下、导航栏标题隐藏
- `768px`：控制面板转纵向、浮动面板隐藏、信息条精简
- `480px`：按钮组换行

---

## CSS 类名索引

### 通用外壳
`demo-navbar` · `demo-navbar.immersive` · `demo-navbar.scrolled`
`demo-nav-left` · `demo-nav-center` · `demo-nav-right`
`demo-back-link` · `demo-nav-logo` · `demo-nav-divider`
`demo-btn-download`

### 信息条
`demo-info-bar` · `demo-info-bar.immersive`
`demo-info-left` · `demo-info-center` · `demo-info-right`
`demo-info-title` · `demo-tech-tag` · `demo-info-link`

### 浮动组件
`demo-floating-group` · `demo-floating-left` · `demo-floating-right`
`demo-icon-btn` · `demo-icon-btn.light` · `demo-icon-btn.active`
`demo-floating-panel` · `demo-floating-panel.light`
`demo-panel-title` · `demo-panel-divider` · `demo-panel-info`
`demo-mode-switcher` · `demo-mode-btn`
`demo-scene-hint` · `demo-loading`

### 框架一
`framework-immersive` · `demo-canvas-full`

### 框架二
`framework-magazine` · `magazine-layout`
`magazine-article` · `magazine-article-header`
`magazine-kicker` · `magazine-title` · `magazine-subtitle`
`magazine-body` · `magazine-step-content`
`magazine-step-indicator` · `magazine-step-dots` · `magazine-step-dot`
`magazine-step-label` · `magazine-step-nav`
`magazine-visual` · `magazine-visual-wrapper` · `magazine-visual-caption`
`magazine-proof-step` · `magazine-proof-num` · `magazine-proof-text`
`magazine-theorem-box` · `magazine-theorem-title` · `magazine-theorem-text`

### 框架三
`framework-interactive` · `interactive-main`
`interactive-canvas-area` · `interactive-data-display`
`interactive-control-panel` · `control-sliders` · `control-buttons`
`control-slider-group` · `control-slider-header`
`control-slider-label` · `control-slider-value` · `control-slider`
`control-btn` · `control-btn.active` · `control-btn-play`
`data-row` · `data-label` · `data-value`

### 框架四
`framework-narrative` · `narrative-main`
`narrative-map-area` · `narrative-info-card`
`narrative-info-year` · `narrative-info-title` · `narrative-info-desc`
`narrative-timeline-panel` · `narrative-timeline-header`
`narrative-timeline-title` · `narrative-timeline-subtitle`
`narrative-timeline-list` · `timeline-event`
`timeline-event-dot` · `timeline-event-content`
`timeline-event-year` · `timeline-event-title` · `timeline-event-desc`
`narrative-timeline-footer` · `narrative-play-btn`
`narrative-progress` · `narrative-progress-bar`

---

*最后更新：2026-08-06*
