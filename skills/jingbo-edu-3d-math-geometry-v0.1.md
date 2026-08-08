# 景礴 Skill：3D数学几何探索

## Skill 信息

- **名称**：3D数学几何探索
- **类型**：沉浸式全屏型（Immersive 3D）
- **学科**：数学
- **技术栈**：Three.js + OrbitControls
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js`
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js`

## 框架描述

生成一个深色沉浸式全屏 3D 可视化页面，用于探索数学几何体的空间结构与截面。用户可以通过鼠标拖拽旋转、滚轮缩放、调节截面参数来交互式探索圆锥截面、多面体截面、立体几何等数学概念。适用于任何需要 3D 空间理解的数学几何可视化。

## 布局规范

```
┌─────────────────────────────────────────┐
│  [标题浮层]              [控制面板浮层]    │
│                                          │
│                                          │
│           全屏 3D 画布                    │
│        (Three.js WebGL Canvas)           │
│                                          │
│                                          │
│  [信息面板浮层]          [图例浮层]       │
└─────────────────────────────────────────┘
```

- 全屏 Canvas（100vw × 100vh），深色背景
- 浮层使用毛玻璃效果（backdrop-filter: blur(12px)）
- 左上：标题 + 几何参数信息
- 右上：显示模式切换 + 截面控制（角度/位置/透明度）
- 左下：当前截面形状信息（椭圆/抛物线/双曲线等）
- 右下：颜色图例 + 操作提示

## 交互模式

1. **鼠标拖拽**：旋转 3D 几何体（OrbitControls）
2. **滚轮缩放**：放大/缩小视图
3. **截面切割**：调节截面参数，实时切割几何体显示截面形状
4. **显示模式切换**：完整结构 / 仅截面 / 透视图 / 线框模式
5. **自动旋转**：可开启/关闭自动旋转
6. **参数调节**：截面角度、位置、透明度等参数实时调整

## 视觉风格

- **背景**：深色径向渐变 `radial-gradient(ellipse at center, #0a0e1a, #000000)`
- **主色调**：紫色系 `#6366f1`（主结构）、青色 `#06b6d4`（截面）
- **强调色**：根据具体几何体定义（截面椭圆=琥珀色、抛物线=绿色、双曲线=红色）
- **文字**：白色 `#ffffff`，带深色描边 `text-shadow: 0 1px 3px rgba(0,0,0,0.8)`
- **控制面板**：`rgba(15,15,25,0.7)` + `backdrop-filter: blur(12px)` + `border: 1px solid rgba(255,255,255,0.1)`
- **高亮效果**：选中截面使用 `emissive` 发光效果
- **字体**：系统无衬线字体，标题 16px bold，正文 13px regular

## 数据输入格式

用户用自然语言描述要生成的数学几何可视化，例如：
- "生成一个圆锥截面3D演示，一刀切出椭圆抛物线双曲线"
- "做一个正多面体截面探索工具"
- "创建一个立体几何三视图演示"

AI 应根据描述：
1. 确定要建模的数学几何体
2. 程序化生成 3D 几何体（不依赖外部模型文件）
3. 为截面切割功能添加参数控制
4. 设置合理的初始视角和光照

## 3D 建模要求

- 所有 3D 模型使用 Three.js 原生几何体程序化生成（ConeGeometry, BoxGeometry, IcosahedronGeometry 等）
- 不依赖外部 .glb/.gltf 模型文件
- 使用 Group 组织层级结构
- 截面使用 ClippingPlanes 或自定义平面切割实现
- 每个可交互部件设置 `userData` 存储元数据（名称、形状类型、参数）
- 使用 Raycaster 实现点击拾取

## 光照设置

```javascript
// 环境光
const ambient = new THREE.AmbientLight(0x404060, 0.5);
// 主光源
const directional = new THREE.DirectionalLight(0xffffff, 0.8);
directional.position.set(5, 10, 5);
// 补光
const point = new THREE.PointLight(0x6366f1, 0.5, 50);
point.position.set(-5, -5, 5);
```

## 质量要求

1. 3D 渲染流畅（目标 60fps）
2. 初始加载 < 2 秒
3. 支持响应式（移动端触控旋转）
4. 所有交互部件有 hover 光标变化
5. 截面计算准确、数学严谨
6. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个圆锥截面3D演示，一刀切出椭圆抛物线双曲线"
- "做一个正多面体截面探索工具"
- "创建一个立体几何三视图演示"
- "生成一个圆柱截面3D探索，展示不同角度切割的截面形状"
- "做一个正四面体与正八面体的截面对比"

## 参考案例

- [圆锥截面3D交互](https://jingbo.xyz/demos/conic-section-3d/index.html)
- [多面体截面探索](https://jingbo.xyz/demos/polyhedron-cross-section/index.html)
- [立体几何视图](https://jingbo.xyz/demos/M1-solid-geometry.html)
