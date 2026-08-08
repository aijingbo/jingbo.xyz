# 景礴 Skill：3D天体运动模拟

## Skill 信息

- **名称**：3D天体运动模拟
- **类型**：沉浸式全屏型（Immersive 3D）
- **学科**：天文 · 地理
- **技术栈**：Three.js + OrbitControls
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js`
  - `https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js`

## 框架描述

生成一个深色星空背景的 3D 天体运动模拟页面。用户可以通过鼠标拖拽旋转视角、滚轮缩放、控制时间流速来观察天体运动。适用于太阳系行星轨道运行、月相变化等天文现象的沉浸式模拟。

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

- 全屏 Canvas（100vw × 100vh），深色星空背景
- 浮层使用毛玻璃效果（backdrop-filter: blur(12px)）
- 左上：标题 + 天体系统信息
- 右上：时间流速控制 + 视角切换
- 左下：当前选中天体的详细信息
- 右下：颜色图例 + 操作提示

## 交互模式

1. **鼠标拖拽**：旋转 3D 视角（OrbitControls）
2. **滚轮缩放**：放大/缩小视图
3. **时间流速控制**：暂停 / 慢速 / 正常 / 加速
4. **视角切换**：俯视 / 侧视 / 跟随特定天体
5. **点击天体**：点击天体高亮显示并在信息面板展示详情
6. **轨道线显示**：天体运行轨道半透明显示，可切换开关

## 视觉风格

- **背景**：深色星空背景 `radial-gradient(ellipse at center, #0a0e1a, #000000)` + 星点粒子
- **主色调**：天体使用真实色彩（太阳=金黄、地球=蓝、火星=红等）
- **轨道线**：半透明白色 `rgba(255,255,255,0.15)`
- **文字**：白色 `#ffffff`，带深色描边 `text-shadow: 0 1px 3px rgba(0,0,0,0.8)`
- **控制面板**：`rgba(15,15,25,0.7)` + `backdrop-filter: blur(12px)` + `border: 1px solid rgba(255,255,255,0.1)`
- **高亮效果**：选中天体使用 `emissive` 发光效果
- **字体**：系统无衬线字体，标题 16px bold，正文 13px regular

## 数据输入格式

用户用自然语言描述要生成的天体运动，例如：
- "生成一个太阳系八大行星运行 3D 模拟"
- "做一个月相变化 3D 演示"
- "创建一个木星卫星系统 3D 模型"

AI 应根据描述：
1. 确定要建模的天体系统（行星系/卫星系/双星系统等）
2. 程序化生成 3D 天体球体与轨道（不依赖外部模型文件）
3. 为每个天体添加正确的颜色、标签和运动参数
4. 设置合理的初始视角和光照

## 3D 建模要求

- 所有 3D 模型使用 Three.js 原生几何体程序化生成（SphereGeometry, RingGeometry 等）
- 不依赖外部 .glb/.gltf 模型文件
- 使用 Group 组织层级结构
- 每个可交互天体设置 `userData` 存储元数据（名称、描述、参数）
- 使用 Raycaster 实现点击拾取
- 星空背景使用 Points 粒子系统生成

## 光照设置

```javascript
// 环境光
const ambient = new THREE.AmbientLight(0x404060, 0.3);
// 中心恒星主光源（如太阳）
const sun = new THREE.PointLight(0xffffff, 2, 200);
sun.position.set(0, 0, 0);
// 补光
const directional = new THREE.DirectionalLight(0xffffff, 0.3);
directional.position.set(5, 10, 5);
```

## 质量要求

1. 3D 渲染流畅（目标 60fps）
2. 初始加载 < 2 秒
3. 支持响应式（移动端触控旋转）
4. 所有交互天体有 hover 光标变化
5. 信息面板内容准确、科学严谨
6. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个太阳系八大行星运行 3D 模拟，支持时间加速与视角切换"
- "做一个月相变化 3D 演示，展示日地月三体关系"
- "创建一个木星卫星系统 3D 模型，展示伽利略卫星"
- "生成一个地月系统 3D 模拟，展示潮汐成因"
- "做一个哈雷彗星轨道 3D 可视化"

## 参考案例

- [太阳系行星运行3D](https://jingbo.xyz/demos/solar-system/index.html)
- [月相变化3D模拟](https://jingbo.xyz/demos/moon-phases/index.html)
