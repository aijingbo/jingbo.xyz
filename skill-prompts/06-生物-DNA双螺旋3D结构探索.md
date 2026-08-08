# Skill Demo 提示词：DNA 双螺旋 3D 结构探索

## 任务

创建一个单 HTML 文件的教育可视化 Demo，使用 Three.js 程序化生成 DNA 双螺旋 3D 模型，支持交互旋转、缩放、结构标注，帮助学生理解 DNA 的空间构型。

## 技术栈

- **Three.js** (CDN): `https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js`
- **OrbitControls** (CDN): `https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js`
- 纯 CSS 样式，单 HTML 文件

## 功能要求

### 核心功能
1. **DNA 双螺旋 3D 模型**（程序化生成）：
   - 两条互补链的糖-磷酸骨架（彩色管状）
   - 碱基对（A-T, G-C）用彩色棒状连接
   - 正确的螺旋参数：螺距 3.4nm，每圈 10 个碱基对，直径 2nm
   - 碱基颜色：A=红, T=蓝, G=绿, C=黄

2. **结构标注**：
   - 大沟（Major Groove）和小沟（Minor Groove）标注
   - 5'→3' 方向标注（两条链反向平行）
   - 磷酸-脱氧核糖骨架高亮
   - 氢键数量标注（A-T = 2个氢键, G-C = 3个氢键）

3. **交互功能**：
   - 鼠标拖拽旋转
   - 滚轮缩放
   - 自动旋转模式
   - 显示模式切换：
     - 完整结构（默认）
     - 仅骨架
     - 仅碱基对
     - 简化示意（平面化展开）

4. **动画效果**：
   - 解链动画：DNA 从中间解开，展示碱基配对
   - 转录动画：展示 RNA 聚合酶读取过程（简化版）
   - 旋转展示：自动绕轴旋转

5. **信息面板**：
   - DNA 基本参数（螺距、直径、碱基对数）
   - 当前显示模式
   - 碱基配对规则说明
   - 点击碱基显示详细信息

### DNA 生成参数
```javascript
const dnaParams = {
  basePairs: 20,        // 碱基对数量
  helixRadius: 1.0,     // 螺旋半径
  helixRise: 0.34,      // 每个碱基对上升高度
  helixTwist: 36,       // 每个碱基对旋转角度（度）
  backboneRadius: 0.15, // 骨架管半径
  bondRadius: 0.08,     // 氢键棒半径
  baseSequence: "ATCGATCGATCGATCGATCG" // 可自定义序列
};
```

### UI 布局
- 全屏 3D 画布
- 左上角浮层：标题 + DNA 参数信息
- 右上角浮层：显示模式切换 + 动画控制
- 底部浮层：碱基颜色图例 + 操作提示
- 右下角浮层：碱基序列显示（可编辑）

### 视觉风格
- 背景：深色径向渐变（#0a0e1a 中心 → #000000 边缘）
- DNA 骨架：链1 青色（#06b6d4），链2 紫色（#a855f7）
- 碱基：A=红色（#ef4444），T=蓝色（#3b82f6），G=绿色（#22c55e），C=黄色（#eab308）
- 氢键：白色半透明
- 标注线：白色虚线
- 文字标签：白色，带深色描边
- 控制面板：毛玻璃效果（backdrop-filter: blur(10px)）

## 质量要求

1. Three.js 3D 渲染流畅（60fps）
2. DNA 螺旋参数物理正确
3. 自动旋转平滑
4. 显示模式切换有过渡动画
5. OrbitControls 正常工作
6. 中文注释和 UI 文案
7. 单 HTML 文件，不超过 100KB

## 输出

一个完整的 `index.html` 文件，保存到 `/Users/a1/Desktop/jingbo.xyz/demo/06-DNA双螺旋/index.html`
