# 景礴 Skill：数学图形工具

## Skill 信息

- **名称**：数学图形工具
- **类型**：交互工具型（Interactive Tool）
- **学科**：数学
- **技术栈**：Canvas + JSXGraph
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/jsxgraph/distrib/jsxgraphcore.js`
  - `https://cdn.jsdelivr.net/npm/jsxgraph/distrib/jsxgraph.css`

## 框架描述

生成交互式参数化数学图形工具页面。左侧或顶部参数控制面板（滑块、输入框），右侧实时可视化区域。用户调节参数立即看到图形变化。适用于圆锥曲线、三角波形、函数绘图、分形几何、复利计算等任何需要参数化可视化的数学概念。

## 布局规范

```
┌─────────────────────────────────────────┐
│  [标题栏]                                │
├──────────────┬──────────────────────────┤
│              │                          │
│  参数控制面板  │      实时可视化画布        │
│  (滑块/输入框) │    (Canvas / JSXGraph)   │
│              │                          │
│  [参数显示]   │      [坐标轴/图形]        │
│              │      [实时数据反馈]       │
└──────────────┴──────────────────────────┘
```

- 左侧参数面板（固定宽度 280-320px），暖色浅底
- 右侧可视化画布自适应剩余空间
- 参数面板包含：滑块、数字输入框、下拉选择、颜色选择
- 可视化区域：坐标系、实时图形、数据标注

## 交互模式

1. **滑块调节**：拖动滑块，参数实时变化，图形同步更新
2. **输入框输入**：精确输入参数值，回车确认
3. **函数表达式输入**：输入数学表达式实时解析绘制
4. **缩放与平移**：鼠标滚轮缩放坐标系，拖拽平移
5. **实时数据反馈**：当前参数值、坐标、计算结果显示在面板

## 视觉风格

- **背景**：暖色浅底 `linear-gradient(135deg,#f0e8e0,#e6d8cc)`
- **主色调**：绿色系 `#059669`（交互工具标识）
- **参数面板**：`rgba(255,255,255,0.85)` + 柔和边框
- **可视化画布**：白色背景，浅灰网格线
- **强调色**：根据具体图形定义（圆锥曲线红、三角函数蓝等）
- **字体**：系统无衬线字体，标题 16px bold，参数标签 13px

## 数据输入格式

用户用自然语言描述要生成的数学图形工具，例如：
- "生成一个圆锥曲线动态轨迹工具"
- "做一个三角函数波形发生器"
- "创建一个分形几何生成器"

AI 应根据描述：
1. 确定要生成的数学图形类型
2. 设计合适的参数控制项（滑块范围、步进、输入项）
3. 实现参数到图形的实时映射
4. 添加坐标轴、标注、实时数据反馈

## 参数控制要求

- 所有滑块使用原生 `<input type="range">`，支持步进和范围设置
- 参数变化触发 `requestAnimationFrame` 重绘，保证流畅
- 关键参数实时显示当前数值
- 支持参数预设（一键恢复默认值）

## 渲染要求

```javascript
// 参数变化实时重绘
function onParamChange() {
  requestAnimationFrame(draw);
}
// 清除画布并重绘
function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  drawGrid();
  drawGraph();
  drawLabels();
}
```

## 质量要求

1. 参数调节响应 < 16ms（目标 60fps）
2. 初始加载 < 1 秒
3. 支持响应式（移动端纵向布局）
4. 所有滑块和输入框有清晰标签
5. 数学计算准确、严谨
6. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个圆锥曲线动态轨迹工具，离心率滑块控制椭圆到双曲线"
- "做一个三角函数波形发生器，振幅频率相位实时调节"
- "创建一个分形几何生成器，曼德博集合与科赫雪花"
- "生成一个函数图像绘制器，支持输入表达式实时绘制"
- "做一个复利计算器，本金利率年限参数化"

## 参考案例

- [圆锥曲线动态轨迹生成器](https://jingbo.xyz/demos/conic-sections/index.html)
- [三角函数波形发生器](https://jingbo.xyz/demos/trig-wave-generator/index.html)
- [函数图像绘制器](https://jingbo.xyz/demos/function-plotter/index.html)
- [分形几何生成器](https://jingbo.xyz/demos/fractal-geometry-generator/index.html)
- [复利计算器与财富增长](https://jingbo.xyz/demos/compound-interest-calculator/index.html)
- [单位圆与三角函数](https://jingbo.xyz/demos/unit-circle-trig/index.html)
- [线性变换矩阵可视化](https://jingbo.xyz/demos/linear-transform-matrix/index.html)
