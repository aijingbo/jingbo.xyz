# 景礡之道 — EduViz Lab

> 教科书的严谨遇上博物馆的精致——每一页都是一个可以触摸的知识展品。

教育可视化个人网站，提供交互式学科 Demo 和可下载的 Trae Skill。

## 内容

### 学科 Demo（12 个）

| 编号 | 名称 | 学科 | 状态 |
|------|------|------|------|
| M1 | 正四棱锥线面角 | 数学 3D | ✅ |
| M2 | 椭圆数量积范围 | 数学 2D | 开发中 |
| M3 | 三角函数变换器 | 数学 2D | 开发中 |
| P1 | 小孔成像仿真 | 物理 2D+3D | 开发中 |
| P2 | 抛体运动轨迹 | 物理 2D | 开发中 |
| P3 | 太阳系 3D 交互 | 物理 3D | 开发中 |
| C1 | 甲烷燃烧 | 化学 3D | ✅ |
| C2 | 酯化反应 | 化学 3D | 开发中 |
| B1 | 人体器官系统 | 生物 3D | 开发中 |
| B2 | 细胞器探索 | 生物 2D | 开发中 |
| H1 | 丝绸之路交互 | 历史 2D | 开发中 |
| X1 | 概念可视化动画 | 跨学科 | 开发中 |

### Trae Skill（7 个）

| Skill | 功能 | 状态 |
|-------|------|------|
| edu-solid-geometry | 立体几何 → 3D 交互解题网页 | 开发中 |
| edu-analytic-geometry | 解析几何 → 2D 交互解题网页 | 开发中 |
| edu-chem-reaction | 化学反应 → 3D 分子动画网页 | 开发中 |
| edu-physics-simulation | 物理仿真 → 交互实验网页 | 开发中 |
| edu-biology-explorer | 生物结构 → 交互探索网页 | 开发中 |
| edu-history-timeline | 历史事件 → 交互时间轴地图 | 开发中 |
| edu-function-visualizer | 函数 → 交互变换器网页 | 开发中 |

## 技术栈

- **前端**：纯 HTML/CSS/JS，无构建依赖
- **3D 渲染**：Three.js（CDN）
- **2D 渲染**：Canvas 2D
- **数学公式**：KaTeX / MathJax（CDN）
- **设计系统**：统一 CSS 变量 + 学科强调色

## 目录结构

```
jingbo.xyz/
├── index.html              ← 展示网站主页
├── assets/
│   ├── css/                ← 设计系统样式
│   ├── js/                 ← 交互脚本
│   └── img/                ← Demo 缩略图
├── demos/                  ← 12 个学科 Demo
├── skills/                 ← 7 个 Skill 下载包
└── README.md
```

## 部署

- **平台**：Cloudflare Pages
- **方式**：GitHub 仓库连接，自动部署
- **域名**：jingbo.xyz

## 许可

个人教育用途，所有 Demo 和 Skill 供教育工作者免费使用。
