# 景礴 Skill：3D物质微观结构

## Skill 信息

- **名称**：3D物质微观结构
- **类型**：沉浸式全屏型（Immersive 3D）
- **学科**：化学 · 物理
- **技术栈**：Three.js + 3Dmol.js + OrbitControls
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js`
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js`
  - `https://cdn.jsdelivr.net/npm/3dmol@1.4.0/build/3Dmol-min.js`

## 框架描述

生成一个深色沉浸式全屏 3D 可视化页面，用于探索物质微观结构。用户可以通过鼠标拖拽旋转、滚轮缩放、点击部件高亮来交互式探索分子、晶体、原子结构。适用于分子球棍模型、晶体晶胞结构、原子电子轨道等任何需要 3D 空间理解的化学/物理概念。

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
- 左上：标题 + 结构参数信息
- 右上：显示模式切换 + 动画控制（播放/暂停/速度）
- 左下：当前选中部件的详细信息
- 右下：颜色图例 + 操作提示

## 交互模式

1. **鼠标拖拽**：旋转 3D 模型（OrbitControls）
2. **滚轮缩放**：放大/缩小视图
3. **点击高亮**：点击原子或化学键，高亮显示并在信息面板展示详情
4. **显示模式切换**：球棍模型 / 空间填充 / 线框模型 / 电子云
5. **自动旋转**：可开启/关闭自动旋转
6. **能级跃迁动画**：对于原子结构，支持电子能级跃迁动画演示

## 视觉风格

- **背景**：深色径向渐变 `radial-gradient(ellipse at center, #0a0e1a, #000000)`
- **主色调**：青色系 `#06b6d4`（主结构）、紫色 `#a855f7`（辅助结构）
- **强调色**：根据元素类型定义（如 H=白/O=红/N=蓝/C=灰/Cl=绿/Na=紫）
- **文字**：白色 `#ffffff`，带深色描边 `text-shadow: 0 1px 3px rgba(0,0,0,0.8)`
- **控制面板**：`rgba(15,15,25,0.7)` + `backdrop-filter: blur(12px)` + `border: 1px solid rgba(255,255,255,0.1)`
- **高亮效果**：选中部件使用 `emissive` 发光效果
- **字体**：系统无衬线字体，标题 16px bold，正文 13px regular

## 数据输入格式

用户用自然语言描述要生成的微观结构，例如：
- "生成一个水分子 3D 结构"
- "做一个氯化钠晶体晶胞 3D 模型"
- "创建一个碳原子电子轨道 3D 可视化"

AI 应根据描述：
1. 确定要建模的微观结构（分子/晶体/原子）
2. 程序化生成 3D 几何体（不依赖外部模型文件）
3. 为每个部件添加正确的颜色、标签和交互
4. 设置合理的初始视角和光照

## 3D 建模要求

- 所有 3D 模型使用 Three.js 原生几何体程序化生成（SphereGeometry, CylinderGeometry 等）
- 不依赖外部 .glb/.gltf 模型文件
- 使用 Group 组织层级结构
- 每个可交互部件设置 `userData` 存储元数据（名称、描述、功能）
- 使用 Raycaster 实现点击拾取

## 光照设置

```javascript
// 环境光
const ambient = new THREE.AmbientLight(0x404060, 0.5);
// 主光源
const directional = new THREE.DirectionalLight(0xffffff, 0.8);
directional.position.set(5, 10, 5);
// 补光
const point = new THREE.PointLight(0x06b6d4, 0.5, 50);
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

- "生成一个水分子 3D 结构，支持旋转和原子标注"
- "做一个氯化钠晶体晶胞 3D 模型，展示晶胞结构"
- "创建一个碳原子电子轨道 3D 可视化，展示能级跃迁"
- "生成一个甲烷分子球棍模型，支持显示模式切换"
- "做一个金刚石晶体结构 3D 浏览器"

## 参考案例

- [3D分子结构交互查看器](https://jingbo.xyz/demos/3d-molecule-viewer/index.html)
- [晶体结构3D探索](https://jingbo.xyz/demos/crystal-structure/index.html)
- [原子结构模型3D](https://jingbo.xyz/demos/atomic-structure/index.html)
- [电子云与轨道3D](https://jingbo.xyz/demos/electron-cloud-orbitals/index.html)
- [杂化轨道与成键3D](https://jingbo.xyz/demos/hybrid-orbitals-bonding/index.html)
- [VSEPR分子几何预测](https://jingbo.xyz/demos/vsepr-molecular-geometry/index.html)
