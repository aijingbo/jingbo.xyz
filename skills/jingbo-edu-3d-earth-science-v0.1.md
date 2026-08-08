# 景礴 Skill：3D地球科学探索

## Skill 信息

- **名称**：3D地球科学探索
- **类型**：沉浸式全屏型（Immersive 3D）
- **学科**：地理
- **技术栈**：Three.js + OrbitControls
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js`
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js`

## 框架描述

生成一个深色背景的 3D 地球科学可视化页面。用户可以通过鼠标拖拽旋转地球、滚轮缩放、切换剖面视图、控制动画播放来交互式探索地球科学现象。适用于地球公转与四季成因、板块构造与地震机制等地理现象的沉浸式模拟。

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

- 全屏 Canvas（100vw × 100vh），深色太空背景
- 浮层使用毛玻璃效果（backdrop-filter: blur(12px)）
- 左上：标题 + 地球科学主题信息
- 右上：剖面切换 + 层级显示 + 动画控制
- 左下：当前选中区域的详细信息
- 右下：颜色图例 + 操作提示

## 交互模式

1. **鼠标拖拽**：旋转 3D 地球（OrbitControls）
2. **滚轮缩放**：放大/缩小视图
3. **半剖视图切换**：将地球切开一半，展示内部圈层结构
4. **层级显示切换**：逐层显示/隐藏地壳、地幔、地核等圈层
5. **动画播放控制**：播放/暂停/速度，控制公转或板块运动动画
6. **点击区域显示信息**：点击板块或圈层，高亮显示并在信息面板展示详情

## 视觉风格

- **背景**：深色太空背景 `radial-gradient(ellipse at center, #0a0e1a, #000000)`
- **主色调**：地球使用真实纹理色彩（海洋蓝、陆地绿/棕）
- **板块色彩**：六大板块用不同颜色区分（太平洋=橙、亚欧=红、印度洋=黄、非洲=绿、美洲=蓝、南极洲=紫）
- **文字**：白色 `#ffffff`，带深色描边 `text-shadow: 0 1px 3px rgba(0,0,0,0.8)`
- **控制面板**：`rgba(15,15,25,0.7)` + `backdrop-filter: blur(12px)` + `border: 1px solid rgba(255,255,255,0.1)`
- **高亮效果**：选中区域使用 `emissive` 发光效果
- **字体**：系统无衬线字体，标题 16px bold，正文 13px regular

## 数据输入格式

用户用自然语言描述要生成的地球科学现象，例如：
- "生成一个地球公转与四季成因 3D 演示"
- "做一个板块构造与地震 3D 探索"
- "创建一个地球内部圈层结构 3D 模型"

AI 应根据描述：
1. 确定要建模的地球科学主题（公转四季/板块构造/内部圈层等）
2. 程序化生成 3D 地球及相关结构（不依赖外部模型文件）
3. 为每个部件添加正确的颜色、标签和交互
4. 设置合理的初始视角和光照

## 3D 建模要求

- 所有 3D 模型使用 Three.js 原生几何体程序化生成（SphereGeometry, RingGeometry 等）
- 不依赖外部 .glb/.gltf 模型文件
- 使用 Group 组织层级结构
- 每个可交互部件设置 `userData` 存储元数据（名称、描述、参数）
- 使用 Raycaster 实现点击拾取
- 半剖视图通过修改几何体或裁剪平面实现

## 光照设置

```javascript
// 环境光
const ambient = new THREE.AmbientLight(0x404060, 0.4);
// 主光源（模拟太阳）
const directional = new THREE.DirectionalLight(0xffffff, 1.0);
directional.position.set(10, 5, 10);
// 补光
const point = new THREE.PointLight(0x06b6d4, 0.3, 50);
point.position.set(-5, -5, 5);
```

## 质量要求

1. 3D 渲染流畅（目标 60fps）
2. 初始加载 < 2 秒
3. 支持响应式（移动端触控旋转）
4. 所有交互部件有 hover 光标变化
5. 信息面板内容准确、科学严谨
6. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个地球公转与四季成因 3D 演示，展示黄赤交角与太阳直射点移动"
- "做一个板块构造与地震 3D 探索，展示六大板块分布与运动"
- "创建一个地球内部圈层结构 3D 模型，支持半剖视图与逐层显示"
- "生成一个地球自转与昼夜交替 3D 演示"
- "做一个海陆水循环 3D 可视化"

## 参考案例

- [地球公转与四季3D](https://jingbo.xyz/demos/earth-seasons/index.html)
- [板块构造与地震3D](https://jingbo.xyz/demos/plate-tectonics/index.html)
- [地球地形3D](https://jingbo.xyz/demos/earth-terrain-3d/index.html)
