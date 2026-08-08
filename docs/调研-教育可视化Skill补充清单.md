# 教育可视化 Skill 补充调研清单

> 本文档是《调研-教育可视化Skill全面清单.md》的补充，针对历史时间线、Three.js、3Dmol.js、JSXGraph、p5.js 五大技术方向进行深度扩展，并新增 27 个可产品化的前端可视化库。
>
> **补充调研日期**: 2026-08-06
> **新增方向总数**: 102 个（P0 级 48 个，P1 级 42 个，P2 级 12 个）
> **新增可视化库**: 27 个

---

## 一、历史时间线可视化（14 个新方向）

### 主流时间线前端库

| 库名 | GitHub Star | 许可证 | CDN 可用 | 核心特点 |
|------|------------|--------|---------|---------|
| frappe-gantt | 6,075 | MIT | 是 | 甘特图，任务依赖，多视图模式 |
| markwhen | 4,862 | MIT | 是 | Markdown 语法→级联时间线，多视图 |
| TimelineJS3 | 3,205 | MPL-2.0 | 是 | 叙事型时间线，媒体嵌入，Google Sheets 数据源 |
| vis-timeline | 2,537 | Apache-2.0/MIT | 是 | 全功能时间轴，多组并行，拖拽缩放 |
| d3-timeline | 1,047 | 未声明 | 是 | D3.js 时间线插件 |
| timeliner | 739 | MIT | 是 | 简单时间线库 |

### 历史时间线开源项目

| 项目 | Star | 许可证 | 描述 |
|------|------|--------|------|
| ybogdanov/history-timeline | 347 | GPL-2.0 | 全球历史名人寿命可视化 |
| alterm4nn/ChronoZoom | 177 | — | 137 亿年宇宙演化交互式时间线 |
| LingDong-/grand-timeline | 116 | — | 30800 位中国古代人物统一时间线 |
| wenzhenl/wikitimeline | 57 | MIT | Wikipedia 词条→交互式时间线 |

### P0 级方向

#### HT1. 中外对照交互式时间轴

| 字段 | 内容 |
|------|------|
| **方向名称** | 中外对照交互式时间轴 |
| **知识点** | 同一时间维度下中国与世界重大历史事件并置对比 |
| **推荐技术栈** | vis-timeline（CDN）+ vis DataSet |
| **已有开源参考** | vis-timeline (2,537 Star, Apache-2.0/MIT); TimelineJS3 (3,205 Star, MPL-2.0) |
| **教学痛点** | 传统教学按国别线性叙述，学生缺乏"同期横向对比"能力 |
| **Skill 可行性** | 极高 — vis-timeline 原生支持多 group 并行，JSON 数据驱动 |
| **建议优先级** | **P0** |

#### HT2. 朝代疆域演变动画地图

| 字段 | 内容 |
|------|------|
| **方向名称** | 朝代疆域演变动画地图 |
| **知识点** | 中国历代疆域版图动态变化，都城迁移，行政区划演变 |
| **推荐技术栈** | D3.js + SVG 路径 morph + vis-timeline（时间轴联动） |
| **已有开源参考** | wjt0321/china-history-river (MIT); ziyetsui/china-history-atlas |
| **教学痛点** | 静态地图无法呈现疆域动态变化过程 |
| **Skill 可行性** | 高 — SVG 路径 morph + 时间轴联动，需准备各朝代疆域 SVG 路径数据 |
| **建议优先级** | **P0** |

#### HT3. AI 驱动历史事件→交互式时间线生成器

| 字段 | 内容 |
|------|------|
| **方向名称** | AI 驱动历史事件→交互式时间线生成器 |
| **知识点** | 自然语言历史描述→结构化事件→交互式时间线 |
| **推荐技术栈** | markwhen (MIT, 文本转时间线) + AI 生成 JSON |
| **已有开源参考** | markwhen (4,862 Star, MIT); wikitimeline (57 Star, MIT); GenAI_LLM_timeline (952 Star) |
| **教学痛点** | 教师手工整理历史事件时间线耗时巨大 |
| **Skill 可行性** | 极高 — markwhen 的 Markdown 语法是 LLM 输出的天然格式，AI 生成 markwhen 文本→前端自动渲染 |
| **建议优先级** | **P0** |

### P1 级方向

| 编号 | 方向名称 | 核心技术 | 简述 |
|------|---------|---------|------|
| HT4 | 历史人物生卒时间轴与关系网络 | vis-timeline + D3 力导向图 | 人物生卒年 + 关系网络联动 |
| HT5 | 战争/战役进程时空叙事地图 | Leaflet + D3 + vis-timeline | 行军路线、关键节点时间-空间双维度叙事 |
| HT6 | 宇宙/人类通史缩放时间轴 | D3 对数刻度 + 缩放交互 | 从大爆炸到现代的对数刻度缩放 |
| HT7 | 科技发展史时间轴 | vis-timeline 多 group | 按技术领域分组并行展示 |
| HT8 | 文明对比并行时间轴 | vis-timeline 多 group | 多古文明同一时间轴并行对比 |
| HT9 | 丝绸之路/文明交流路线动态地图 | Leaflet + D3 路径动画 | 传播路线动态绘制 + 节点标注 |
| HT10 | 历史人物传记时间线 | TimelineJS3 | 叙事型，支持图片/视频/音频嵌入 |
| HT11 | 多维度历史事件筛选交互时间轴 | vis-timeline + 筛选 UI | 按政治/经济/文化/科技/军事维度筛选 |

### P2 级方向

| 编号 | 方向名称 | 核心技术 | 简述 |
|------|---------|---------|------|
| HT12 | Wikipedia/文本→时间线自动转换器 | markwhen + AI 文本解析 | 输入词条 URL→自动生成时间线 |
| HT13 | 甘特图式历史事件进程模拟器 | frappe-gantt | 展示历史进程的并行性和重叠期 |
| HT14 | 深时地质年代对数时间轴 | D3 对数刻度 | 地球 46 亿年地质年代 + 生命演化 |

### 关键发现

- **markwhen 是 AI 驱动时间线的最佳载体** — 其 Markdown 文本格式是 LLM 输出的天然格式，AI 生成 markwhen 文本→前端自动渲染，实现"输入历史事件→自动生成交互式时间线"的完整闭环
- **vis-timeline 是教育时间线的瑞士军刀** — 多 group 并行、范围事件、缩放拖拽、动态筛选，Apache-2.0/MIT 双许可 + CDN 可用
- **中国历史方向开源生态薄弱** — grand-timeline (古人全表, 116 Star) 和 china-history-river 是稀有参考，存在巨大空白

---

## 二、Three.js 教育应用（31 个新方向）

### 核心生态数据

| 项目 | Star | 许可证 | 教育用途 |
|------|------|--------|---------|
| three.js | 114,289 | MIT | 3D 渲染核心引擎 |
| cannon-es | 2,046 | MIT | 3D 物理引擎（cannon.js 维护版） |
| MathBox | 1,492 | MIT | 数学 3D 可视化（基于 Three.js） |
| solar-system-threejs | 409 | Apache-2.0 | 太阳系按比例建模 |

### P0 级方向（12 个）

| 编号 | 方向名称 | 学科 | 核心技术 | 教学痛点 |
|------|---------|------|---------|---------|
| T3D-1 | 参数曲面可视化 | 数学 | ParametricGeometry + lil-gui | 学生无法理解 u/v 参数如何映射到 3D 曲面 |
| T3D-2 | 3D 函数图像 z=f(x,y) | 数学 | MathBox (CDN) | 教材 2D 图无法展示函数曲面立体形态 |
| T3D-3 | 电磁场 3D 可视化 | 物理 | Three.js 着色器 + 粒子系统 | 电场线/磁力线是 3D 矢量场，2D 截面无法展示空间分布 |
| T3D-4 | 力的合成与分解 3D | 物理 | ArrowHelper + DragControls | 3D 空间中的力分解需要空间想象 |
| T3D-5 | 简谐振动与波动 3D | 物理 | 顶点着色器动画 | 波的传播是时空动态过程 |
| T3D-6 | 月相变化 3D | 天文/地理 | 球体 + DirectionalLight + 轨道动画 | 月相成因涉及日-地-月三体空间关系 |
| T3D-7 | 日食月食 3D | 天文/地理 | ShadowMap + 本影/半影锥体 | 三体在一条直线上的空间关系 |
| T3D-8 | 蛋白质折叠 3D | 生物 | 3Dmol.js cartoon/surface | 蛋白质 3D 折叠结构无法用 2D 图表达 |
| T3D-9 | 分子振动模式 3D | 化学 | 3Dmol.js frames 动画 | 分子振动是 3D 动态过程 |
| T3D-10 | 晶体对称操作 3D | 化学/数学 | 矩阵变换 + 对称元素可视化 | 32 种点群难以记忆，2D 投影无法展示旋转轴/镜面 |
| T3D-11 | 化学键与分子几何 (VSEPR) | 化学 | 3Dmol.js 球棍模型 | 分子 3D 构型需要空间想象 |
| T3D-12 | 大气层结构 3D | 地理 | 分层半透明球体 + 温度曲线 | 大气垂直分层结构和温度变化趋势 |

### P1 级方向（17 个）

| 编号 | 方向名称 | 学科 | 核心技术 |
|------|---------|------|---------|
| T3D-13 | 拓扑结构（莫比乌斯环/克莱因瓶） | 数学 | ParametricGeometry + DoubleSide |
| T3D-14 | 向量场 3D 可视化 | 数学 | MathBox `<vector>` + 粒子流线 |
| T3D-15 | 高维投影几何（超立方体） | 数学 | 4D→3D 投影矩阵 + 线框 |
| T3D-16 | 刚体转动/角动量 | 物理 | cannon-es 物理引擎 |
| T3D-17 | 流体力学模拟 | 物理 | GPU 粒子系统 (GPGPU) |
| T3D-18 | 光的干涉与衍射 3D | 物理 | 着色器波叠加计算 |
| T3D-19 | 星座 3D | 天文 | 粒子系统 + 真实恒星坐标 |
| T3D-20 | 银河系结构 3D | 天文 | GPU 粒子 + 螺旋星系程序化生成 |
| T3D-21 | 神经元结构 3D | 生物 | TubeGeometry 分形分支 |
| T3D-22 | 病毒结构 3D | 生物 | IcosahedronGeometry + 3Dmol.js PDB |
| T3D-23 | 细胞结构 3D | 生物 | ClippingPlane + CSS2DRenderer |
| T3D-24 | 反应过渡态 3D | 化学 | 3Dmol.js frames 插值 + 能量曲线 |
| T3D-25 | 机械结构/齿轮传动 | 工程 | ExtrudeGeometry + 运动学约束 |
| T3D-26 | 桥梁力学/桁架 | 工程 | 线段几何 + ArrowHelper + cannon-es |
| T3D-27 | 四冲程发动机 | 工程 | ClippingPlane + 活塞/气门动画 |
| T3D-28 | 火山结构/喷发 | 地理 | 剖切地形 + 粒子系统（岩浆） |
| T3D-29 | 地震波传播 | 地理 | 球面波前扩散 + 地球分层模型 |

### P2 级方向（2 个）

| 编号 | 方向名称 | 学科 | 核心技术 |
|------|---------|------|---------|
| T3D-30 | 建筑结构力学 | 工程 | 简化有限元 + 应力颜色映射 |
| T3D-31 | 水循环 3D | 地理 | 3D 地球 + 多种粒子效果 |

### 技术栈推荐

```html
<!-- 核心 Three.js -->
<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.160.0/examples/js/controls/OrbitControls.js"></script>
<!-- 数学可视化 -->
<script src="https://cdn.jsdelivr.net/npm/mathbox@latest/build/bundle/mathbox.js"></script>
<!-- 分子/蛋白质可视化 -->
<script src="https://3Dmol.org/build/3Dmol-min.js"></script>
<!-- 物理引擎 -->
<script src="https://cdn.jsdelivr.net/npm/cannon-es@0.20.0/dist/cannon-es.js"></script>
<!-- UI 控制面板 -->
<script src="https://cdn.jsdelivr.net/npm/lil-gui@0.19.2/dist/lil-gui.umd.min.js"></script>
```

---

## 三、3Dmol.js 驱动的化学可视化（16 个新方向）

### 3Dmol.js 核心能力

- **许可证**: BSD
- **CDN**: `https://3Dmol.org/build/3Dmol-min.js`
- **支持格式**: pdb, sdf, mol2, xyz, cif, cdjson, mmtf 等
- **高级功能**: `addSurface()` (VDW/SAS/SES 表面)、`addIsosurface()` (等值面)、`vibrate()` (振动动画)、`addModelsAsFrames()` (多帧轨迹)、`setClickable()` (原子点击)、`linkViewer()` (多视窗同步)、`addUnitCell()`/`replicateUnitCell()` (晶胞扩展)、`$3Dmol.download("pdb:XXXX")` (直接从 RCSB 获取)

### 关键辅助库

| 库名 | 许可证 | 用途 |
|------|--------|------|
| RDKit.js (WASM) | BSD-3-Clause | SMILES 解析、2D 结构生成、3D 构象生成、CIP 规则计算 |
| Mol* | MIT | 下一代分子可视化（RCSB PDB 官方使用） |
| PubChem PUG REST API | 免费 | 通过 CID 获取 3D SDF 结构 |

### P0 级方向（9 个）

| 编号 | 方向名称 | 知识点 | 核心 API | 教学痛点 |
|------|---------|--------|---------|---------|
| C3D-1 | 分子静电势表面可视化 | 静电势、分子极性、反应位点预测 | `addSurface` + `VolumeData` + `Gradient.RWB` | "静电势"抽象概念难以建立空间直觉 |
| C3D-2 | 分子几何测量工具 | 键长/键角/二面角 | `setClickable` + 原生数学 + `addLabel` | 学生无法实际测量，只能记忆数值 |
| C3D-3 | 分子振动与红外光谱动画 | 简正振动、红外活性、官能团吸收 | `vibrate` + `animate` + Chart.js | 振动模式是 3D 动态过程，教材只有静态箭头 |
| C3D-4 | 有机反应机理 3D 过渡态 | SN1/SN2/E1/E2、Walden 翻转 | `addModelsAsFrames` + `addArrow` | SN2 背面进攻和 E2 反式共平面需 3D 理解 |
| C3D-5 | 手性分子 R/S 构型探索 | 手性、对映异构体、CIP 规则 | `linkViewer` + RDKit.js | "镜像但不重合"关系需 3D 操作 |
| C3D-6 | HOMO/LUMO 分子轨道 | 前线轨道理论、轨道对称性 | `addIsosurface` + cube 文件 | 分子轨道"形状"是最难理解的概念 |
| C3D-7 | 蛋白质结构 3D 浏览器 | 二级/三级/四级结构 | `$3Dmol.download("pdb:")` + cartoon | 蛋白质 3D 折叠结构无法用 2D 图表达 |
| C3D-8 | SMILES→2D→3D 构造器 | SMILES、构象异构体 | RDKit.js + 3Dmol.js | 学生输入 SMILES 后无法立即看到 3D 结构 |
| C3D-9 | 3D 分子主动学习答题 | 官能团识别、杂化判断 | `setClickable` + `addPropertyLabels` | 传统教学缺乏互动性 |

### P1 级方向（6 个）

| 编号 | 方向名称 | 知识点 | 核心 API |
|------|---------|--------|---------|
| C3D-10 | 配位化合物与晶体场分裂 | d 轨道分裂、高/低自旋 | `addArrow` + Chart.js |
| C3D-11 | 核酸 3D 结构与碱基配对 | DNA 双螺旋、大沟小沟 | PDB 下载 + 标注 |
| C3D-12 | X 射线衍射原理 | 布拉格定律、晶面间距 | `addUnitCell` + `replicateUnitCell` |
| C3D-13 | NMR 化学位移关联 | 屏蔽/去屏蔽效应 | `mapAtomProperties` + 数据表 |
| C3D-14 | 分子动力学轨迹播放 | 构象变化、RMSD | `addModelsAsFrames` + `animate` |
| C3D-15 | 多模型对比与叠合 | 分子叠合、构象异构体 | `linkViewer` + RDKit.js |

### P2 级方向（1 个）

| 编号 | 方向名称 | 知识点 | 核心 API |
|------|---------|--------|---------|
| C3D-16 | 高分子/聚合物结构 | 链构象、交联网络 | `addModel` + 手动构建 |

### 数据获取方案

```javascript
// 从 RCSB PDB 获取蛋白质结构
$3Dmol.download("pdb:1MO8", viewer, {}, function() { viewer.render(); });

// 从 PubChem 获取分子 3D 结构
fetch("https://pubchem.ncbi.nlm.nih.gov/rest/pug/compound/cid/2244/record/SDF?record_type=3d")

// RDKit.js 从 SMILES 生成 3D 构象
const mol = RDKit.get_mol(smiles);
const molBlock = mol.get_molblock(); // 传递给 3Dmol.js addModel(data, "sdf")
```

---

## 四、JSXGraph 几何作图与讲题（9 个新方向）

### JSXGraph 生态基线

- **仓库**: github.com/jsxgraph/jsxgraph — LGPL-3.0 与 MIT 双许可（选 MIT 可完全商用）
- **CDN**: `cdn.jsdelivr.net/npm/jsxgraph`
- **官方示例**: 247 个（jsxgraph.org/share）
- **关键能力**: JessieCode（几何构造 DSL）、动画系统（moveTo/visit）、3D 视图、MathJax 公式渲染
- **辅助库**: Mafs (MIT, React 数学可视化); Inter-GPS (MIT, 几何题符号推理求解器，Geometry3K 数据集 3002 道题)

### P0 级方向（6 个）

#### JXG-1. 尺规作图步骤动画化

| 字段 | 内容 |
|------|------|
| **方向名称** | 尺规作图步骤动画化 |
| **知识点** | 角平分线、垂直平分线、过点作垂线/平行线、三角形外接圆/内切圆、正多边形作图 |
| **推荐技术栈** | JSXGraph (CDN) + GSAP (步骤动画编排) + MathJax |
| **已有开源参考** | JSXGraph 官方示例 "Spirograph - geometric construction"、"Ellipse: pin and string method" |
| **教学痛点** | 黑板作图一次性无法回放；"为什么这样作"的逻辑无法动态展示 |
| **Skill 可行性** | 高 — JSXGraph 原生支持所有尺规构造原语 + 动画 API |
| **建议优先级** | **P0** |

#### JXG-2. 几何变换动态演示

| 字段 | 内容 |
|------|------|
| **方向名称** | 几何变换动态演示 |
| **知识点** | 平移、旋转、缩放、反射/轴对称、中心对称、复合变换、变换矩阵 |
| **推荐技术栈** | JSXGraph `board.create('transform')` + 滑块控件 + MathJax |
| **已有开源参考** | JSXGraph 官方示例 "Reflection of a Triangle"、"Two reflections: intersecting/parallel lines"、"Matrix multiplication" |
| **教学痛点** | 复合变换的顺序不可交换性静态无法展示 |
| **Skill 可行性** | 高 — Transform API 原生支持所有变换类型及复合 |
| **建议优先级** | **P0** |

#### JXG-3. 三角形四心与九点圆动态演示

| 字段 | 内容 |
|------|------|
| **方向名称** | 三角形四心与九点圆 |
| **知识点** | 重心、垂心、内心、外心、欧拉线、九点圆 |
| **推荐技术栈** | JSXGraph 拖拽顶点 + 实时计算交点 + MathJax |
| **已有开源参考** | JSXGraph 官方示例 "Centroid of triangle"、"Euler line"、"Circumcircles of subtriangles" |
| **教学痛点** | 欧拉线的存在性是震撼性结论但课本只有静态图 |
| **Skill 可行性** | 高 — 已有重心、外接圆、欧拉线示例可复用 |
| **建议优先级** | **P0** |

#### JXG-4. 圆的性质动态证明

| 字段 | 内容 |
|------|------|
| **方向名称** | 圆的性质动态证明 |
| **知识点** | 圆周角定理、圆内接四边形、切线性质、切线长定理、圆幂定理 |
| **推荐技术栈** | JSXGraph `board.create('circle')` + glider + 角度实时测量 |
| **已有开源参考** | JSXGraph 官方示例 "Thales' theorem"、"Tangents on circle"、"Five Circle Theorem"、"Circle inversion" |
| **教学痛点** | "同弧"概念学生常混淆；圆幂定理三种形式统一性课本割裂呈现 |
| **Skill 可行性** | 高 — 官方示例最密集的方向，实现成本最低 |
| **建议优先级** | **P0** |

#### JXG-5. 几何证明题可视化（讲题核心场景）

| 字段 | 内容 |
|------|------|
| **方向名称** | 几何证明题可视化 |
| **知识点** | 全等三角形证明、相似三角形判定、勾股定理证明、综合定理应用 |
| **推荐技术栈** | JSXGraph + JessieCode (AI 生成构造脚本) + MathJax + 步骤导航 UI |
| **已有开源参考** | JSXGraph 官方示例 "Ceva's/Menelaus's/Desargues's/Pappus 定理"; Inter-GPS (MIT, Geometry3K 数据集 3002 道题) |
| **教学痛点** | **最大痛点** — 黑板画图静态，辅助线"为什么这样添"的逻辑无法回放 |
| **Skill 可行性** | 层 1 (模板法): 高 — 预设经典题型模板，教师选题型+输入参数；层 2 (全 AI): 中 — LLM 生成 JessieCode + 形式化校验 |
| **建议优先级** | **P0 (层 1) / P1 (层 2)** |

**AI 讲题技术路径**: 输入题目文字 → AI 解析为几何元素 JSON → 生成 JessieCode → JSXGraph 渲染 → 逐步动画作图 + 证明文字同步。JessieCode 语法接近数学描述（`A = point(1,2); l = line(A,B)`），LLM 生成比底层 JS API 更可控。

#### JXG-6. 动态几何（轨迹/最值/存在性问题）

| 字段 | 内容 |
|------|------|
| **方向名称** | 动态几何（轨迹/最值/存在性问题） |
| **知识点** | 轨迹问题、最值问题（将军饮马）、存在性问题 |
| **推荐技术栈** | JSXGraph `glider` + `trace`/`locus` + 动画 + 数值面板 |
| **已有开源参考** | JSXGraph 官方示例 "Trace curve: parabola"、"Parabola as locus curve"、"Cycloid"、"Glider on axes" |
| **教学痛点** | 中考/高考压轴题，学生无法预判动点轨迹 |
| **Skill 可行性** | 高 — glider + trace + locus 机制天然适配 |
| **建议优先级** | **P0** |

### P1 级方向（3 个）

| 编号 | 方向名称 | 知识点 | 核心技术 |
|------|---------|--------|---------|
| JXG-7 | 立体几何三视图 | 三视图生成与对应、空间直线与平面关系 | JSXGraph 3D 视图 + 可选 Three.js |
| JXG-8 | 解析几何位置关系 | 直线与圆位置关系、圆锥曲线性质参数化 | JSXGraph functiongraph + implicitcurve + 滑块 |
| JXG-9 | 向量几何 | 向量加减、点乘叉乘几何意义、向量分解 | JSXGraph arrow + polygon + 自定义投影 |

### AI 驱动"讲题"渐进式落地策略

| 阶段 | 策略 | 可行性 | 说明 |
|------|------|--------|------|
| Phase 1 | 模板法 (P0) | 100% 可控 | 覆盖 20-30 种经典题型，教师选模板+输入参数→确定性生成作图+证明动画 |
| Phase 2 | 半 AI (P1) | 高 | LLM 解析题目→识别题型→匹配模板→填充参数。LLM 仅做分类和参数提取 |
| Phase 3 | 全 AI (P2) | 中 | LLM 生成 JessieCode + 形式化校验 + 自动作图。需结合 Inter-GPS 式符号推理 |

---

## 五、p5.js 教育应用（32 个新方向）

### p5.js 生态数据

- **GitHub**: 23.8K Star, LGPL
- **CDN**: `cdn.jsdelivr.net/npm/p5`
- **教育生态**: The Nature of Code (2024 版, 1.8K Star, CC BY-NC); The Coding Train (200+ 编程挑战, MIT); p5.brush (696 Star); p5.collide2D (590 Star); p5play (733 Star); ml5.js (6.6K Star)

### P0 级方向（15 个）

| 编号 | 方向名称 | 学科 | 核心技术 | 教学痛点 |
|------|---------|------|---------|---------|
| P5-1 | 双摆混沌系统 | 物理 | RK4 积分 + 相空间图 | 确定性系统产生不可预测行为 |
| P5-2 | 弹簧振子与耦合振子 | 物理 | 胡克定律 + p5.sound 可听化 | 简正模态抽象难懂 |
| P5-3 | Perlin 噪声流场生成艺术 | 创意编程 | p5.js 内置 `noise()` | 噪声函数数学原理抽象 |
| P5-4 | 粒子系统与生成艺术 | 创意编程 | 粒子类 + blendMode | OOP 概念在传统教学中枯燥 |
| P5-5 | 康威生命游戏与元胞自动机 | 生物/CS | 纯 Canvas 网格渲染 | "简单规则产生复杂行为"需动态演示 |
| P5-6 | 捕食者-猎物模型 (Lotka-Volterra) | 生物 | Euler 积分 ODE + 种群曲线 | 微分方程组解析解过于抽象 |
| P5-7 | 群体行为与 Boids 模型 | 生物/CS | 三规则 + 空间分区优化 | "涌现"行为是"整体大于部分之和"最佳案例 |
| P5-8 | 遗传算法与进化模拟 | 生物/CS | 适应度函数 + 选择/交叉/变异 | 进化的"代际"概念需要可视化 |
| P5-9 | 向量场与相空间可视化 | 数学 | 箭头绘制 + 粒子流线 + RK4 | 课本箭头图信息密度低 |
| P5-10 | 傅里叶级数与变换可视化 | 数学 | p5.sound 内置 FFT + 旋转向量叠加 | "任意周期函数=正弦波叠加"极度依赖可视化 |
| P5-11 | 音频频谱实时可视化 | 音乐/物理 | p5.sound FFT + 麦克风输入 | 学生看不到"声音长什么样" |
| P5-12 | 排序算法可视化 | CS | 柱状图 + 颜色标记 | 算法执行过程在代码中不可见 |
| P5-13 | 路径查找算法可视化 | CS | 网格 + 优先队列 + 搜索波纹 | A* 搜索过程需要动画展示 |
| P5-14 | 交互式创意编程入门画板 | 创意编程 | p5.js + p5.brush | 编程入门"第一小时"极其关键 |
| P5-15 | 落沙模拟 | 物理/CS | 像素级网格 + 规则系统 | 不同材料的物理规则差异缺乏演示 |

### P1 级方向（12 个）

| 编号 | 方向名称 | 学科 | 核心技术 |
|------|---------|------|---------|
| P5-16 | 洛伦兹吸引子 | 物理/数学 | WEBGL 3D 轨迹 + 参数调节 |
| P5-17 | 三体问题 | 物理/天文 | 引力计算 + 数值积分 |
| P5-18 | Worley 噪声与自然纹理 | 生成艺术 | Worley 噪声 + d3-delaunay |
| P5-19 | 贝塞尔曲线 | 数学 | p5.js 内置 `bezier()` + de Casteljau |
| P5-20 | Voronoi 图与 Delaunay 三角剖分 | 数学/CS | d3-delaunay + 点画艺术 |
| P5-21 | 声波艺术与音频驱动生成艺术 | 音乐/艺术 | p5.sound + p5.brush |
| P5-22 | 波函数坍缩 (WFC) | CS/艺术 | 约束传播 + 瓦片模型 |
| P5-23 | Marching Squares 等值线 | CS/数学 | 16 种情况查找表 + Metaballs |
| P5-24 | 气候数据螺旋可视化 | 地球科学 | 极坐标 + 温度数据 JSON |
| P5-25 | 风场可视化 | 气象学 | Perlin 噪声风场 + 粒子追踪 |
| P5-26 | 神经网络可视化教学 | CS/AI | ml5.js + 权重可视化 |
| P5-27 | 蒙特霍尔问题 | 数学 | 模拟运行 + 统计图表 |

### P2 级方向（5 个）

| 编号 | 方向名称 | 学科 | 核心技术 |
|------|---------|------|---------|
| P5-28 | 软体物理模拟 | 物理 | 质点-弹簧系统 + toxiclibs.js |
| P5-29 | 数学大理石纹理 | 艺术/数学 | 矢量场变形算法 |
| P5-30 | Apollonian 填充图 | 数学 | 笛卡尔圆定理递归 |
| P5-31 | 自回避行走 | 数学/物理 | 回溯算法可视化 |
| P5-32 | Ulam 素数螺旋 | 数学 | 素数判定 + 螺旋排列 |

### p5.js 独特优势总结

1. **创意编程 + 物理仿真 + 生成艺术的交叉领域**是 p5.js 无可替代的生态位
2. **即时视觉反馈**：代码修改→画布更新延迟几乎为零
3. **从入门到进阶的平滑曲线**：从"画一个圆"到"神经网络训练"
4. The Coding Train 提供 200+ 个编程挑战的完整代码 (MIT 许可)，Nature of Code 全书在线免费阅读

---

## 六、新增前端可视化库产品化评估（27 个库）

### 第一梯队（必须做成产品，8 个）

| 库名 | Star | 许可证 | CDN | 教育核心价值 |
|------|------|--------|-----|-------------|
| **ECharts** | ~61K | Apache-2.0 | 是 | 中文教育图表首选，内置主题系统，ECharts GL 支持 3D |
| **Mermaid.js** | ~89K | MIT | 是 | AI 驱动的文本图表生成（流程图/时序图/甘特图/类图/思维导图），LLM 直接生成 |
| **Leaflet.js** | 45.4K | BSD-2 | 是 | 地理教育唯一轻量选择 (40KB)，无需 API Key |
| **mathlive** | ~800+ | MIT | 是 | 数学公式交互编辑器，填补已收录库的输入层空白 |
| **CodeMirror** | ~26K | MIT | 是 | 代码教育基础设施，轻量 100KB |
| **Babylon.js** | ~23K | Apache-2.0 | 是 | 3D/VR 教育全面引擎，内置 Havok 物理引擎 |
| **A-Frame** | ~16K | MIT | 是 | VR 教育最低门槛，HTML 标签式语法 |
| **Cesium.js** | ~13K | Apache-2.0 | 是 | 3D 地球/地理科学教育唯一选择 |

### 第二梯队（高价值，6 个）

| 库名 | Star | 许可证 | 教育核心价值 |
|------|------|--------|-------------|
| **Vega/Vega-Lite** | ~10K/4.5K | BSD-3 | 声明式可视化语法，AI 可直接生成 JSON 规范 |
| **Lottie** | ~30K | MIT | 设计师动画教育链路（After Effects→JSON→Web） |
| **VexFlow** | ~4K | MIT | 乐谱渲染，音乐教育视觉层核心 |
| **Vis.js** | ~14K | Apache-2.0/MIT | 知识图谱/网络可视化教育 |
| **Cytoscape.js** | ~10K | MIT | 图论/生物网络学术级工具（Oxford Bioinformatics 发表） |
| **Prism.js** | ~12K | MIT | 代码教学内容展示标配 |

### 第三梯队（有价值但有限制，13 个）

| 库名 | Star | 许可证 | 限制/说明 |
|------|------|--------|----------|
| ApexCharts | ~15K | 收入分级 | 年收入≥$2M 需商业许可 |
| Mapbox GL JS | ~11K | v2+需 Token | 3D 地图但需 API Key |
| VTK.js | ~1.1K | BSD-3 | 医学/工程科学可视化，专业性强 |
| Cannon.js/Ammo.js | ~2.5K/600 | MIT/Zlib | 3D 物理引擎，与 Babylon.js 内置物理重叠 |
| Rapier | ~4K | Apache-2.0 | WASM 物理引擎，性能最佳但引入稍复杂 |
| ABCjs | ~700 | MIT | ABC 记谱法渲染，入门音乐教育 |
| Web Audio API | 原生 | 免费 | 与 Tone.js 互补 |
| mxGraph/draw.io | ~7K/40K+ | Apache-2.0 | 完整图表编辑器，体积大 |
| GoJS | ~8K | 商业 | 交互能力最强但非开源 |
| Observable Plot | ~4K | ISC | 声明式，D3.js 作者出品，小众 |
| PlayCanvas | ~10K | MIT | 偏游戏开发 |
| d3-geo | ~400 | ISC | 与 D3.js 深度绑定 |
| highlight.js | ~23K | BSD | 与 Prism.js 重叠 |

### 教育产品矩阵（协同关系）

```
数学教育链路：mathlive(输入) → KaTeX/MathJax(渲染) → nerdamer(计算) → ECharts/Plotly.js(可视化)
音乐教育链路：VexFlow(乐谱渲染) → Tone.js(音频播放) → Web Audio API(频谱分析)
编程教育链路：CodeMirror(编辑) → Prism.js(展示) → p5.js(创意编程) → D3.js(数据可视化)
3D教育链路：Babylon.js(3D引擎) → Cannon.js/Rapier(物理) → A-Frame(VR) → Cesium.js(地球科学)
地理教育链路：Leaflet(2D地图) → Cesium.js(3D地球) → d3-geo(投影计算)
图表教育链路：ECharts(交互图表) → Vega-Lite(声明式) → D3.js(底层定制)
知识可视化链路：Mermaid(流程图) → Vis.js/Cytoscape.js(网络图) → D3.js(自定义)
```

### 最值得做产品的 5 个库

1. **ECharts** — 中文教育市场首选图表库，Apache 顶级项目
2. **Mermaid.js** — 89K Star，文本驱动图表，AI 时代最有潜力的可视化库
3. **Leaflet.js** — 地理教育唯一轻量选择，45.4K Star
4. **mathlive** — 数学公式交互编辑，当前报告缺失的关键输入层
5. **Babylon.js** — Three.js 的最佳替代/补充，内置物理引擎 + VR 支持

---

## 七、汇总统计

### 方向数量统计

| 技术方向 | P0 级 | P1 级 | P2 级 | 合计 |
|---------|-------|-------|-------|------|
| 历史时间线 | 3 | 8 | 3 | 14 |
| Three.js | 12 | 17 | 2 | 31 |
| 3Dmol.js | 9 | 6 | 1 | 16 |
| JSXGraph | 6 | 3 | 0 | 9 |
| p5.js | 15 | 12 | 5 | 32 |
| **合计** | **45** | **46** | **11** | **102** |

### 新增可视化库统计

| 梯队 | 数量 | 代表库 |
|------|------|--------|
| 第一梯队 | 8 | ECharts, Mermaid.js, Leaflet.js, mathlive, CodeMirror, Babylon.js, A-Frame, Cesium.js |
| 第二梯队 | 6 | Vega-Lite, Lottie, VexFlow, Vis.js, Cytoscape.js, Prism.js |
| 第三梯队 | 13 | ApexCharts, Mapbox GL JS, VTK.js, Cannon.js, Rapier 等 |

### 原报告 + 补充报告总计

| 指标 | 原报告 | 补充报告 | 总计 |
|------|--------|---------|------|
| 可视化方向 | 76 | 102 | **178** |
| P0 级方向 | 35 | 45 | **80** |
| 前端可视化库 | 21 | 27 | **48** |
