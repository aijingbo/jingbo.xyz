# 工作流 C：课件库与 Demo 内页

> 涉及文件：`demos.html`、`index.html`、`skills.html`、`skills/*.html`（20个）、`demos/*/index.html`（70+个）、`demos/*.html`（2个）
> 预计耗时：60-90 分钟

---

## C1. 全站导航添加"首页"

### 当前状态

所有页面的导航栏均缺少"首页"入口，用户进入内页后无法直接返回首页（只能点左上角 Logo）。

| 页面 | 当前导航 | 需要添加 |
|------|---------|---------|
| `index.html` | 课件库 / 技能库 / 关于 | 首页（active）放在最前 |
| `demos.html` | 课件库(active) / 技能库 / 关于 | 首页放在最前 |
| `skills.html` | 课件库 / 技能库(active) / 关于 | 首页放在最前 |
| `skills/*.html` (20个) | 课件库 / 技能库(active) / 关于 | 首页放在最前 |
| `demos/*/index.html` (70+个) | 各自的 `demo-navbar` 结构 | 在 Logo 后或学科标签前添加"首页"链接 |

### 修改方式

#### 1. index.html（首页）

```html
<div class="navbar-links">
  <a href="index.html" class="active">首页</a>
  <a href="demos.html">课件库</a>
  <a href="skills.html">技能库</a>
  <a href="#about">关于</a>
</div>
```

#### 2. demos.html / skills.html

```html
<div class="navbar-links">
  <a href="index.html">首页</a>
  <a href="demos.html" class="active">课件库</a>  <!-- demos.html 中 active 在此 -->
  <a href="skills.html">技能库</a>
  <a href="index.html#about">关于</a>
</div>
```

#### 3. skills/*.html（技能展示页）

```html
<div class="navbar-links">
  <a href="../index.html">首页</a>
  <a href="../demos.html">课件库</a>
  <a href="../skills.html" class="active">技能库</a>
  <a href="../index.html#about">关于</a>
</div>
```

#### 4. demos/*/index.html（Demo 内页）

Demo 内页使用 `demo-navbar` 结构，需要在导航中添加首页入口。

当前结构：
```html
<header class="demo-navbar" id="demoNavbar">
  <div class="demo-nav-left">
    <a href="/" class="demo-nav-logo">景礴学院</a>
    <span class="demo-nav-divider"></span>
    <a href="/demos.html" class="demo-nav-subject">数学</a>
  </div>
  ...
</header>
```

修改为：
```html
<header class="demo-navbar" id="demoNavbar">
  <div class="demo-nav-left">
    <a href="/index.html" class="demo-nav-logo">景礴学院</a>
    <span class="demo-nav-divider"></span>
    <a href="/index.html" class="demo-nav-home">首页</a>
    <span class="demo-nav-divider"></span>
    <a href="/demos.html" class="demo-nav-subject">数学</a>
  </div>
  ...
</header>
```

### 执行方式

由于涉及 70+ 个 Demo 文件，建议用脚本批量修改：

```bash
# 批量在 demo-navbar 中添加首页链接
# 使用 sed 或 Python 脚本处理
```

注意：Demo 文件中有两种路径风格：
- 绝对路径：`href="/demos.html"`（大部分 Demo）
- 相对路径：`href="../demos.html"`（需检查）

统一使用绝对路径 `href="/index.html"` 即可（Cloudflare Pages 部署后根路径访问正常）。

---

## C2. Demo"下载 Skill"按钮指向对应技能展示页

### 当前状态

所有 Demo 页面的"下载 Skill"按钮都指向 `/skills.html`（技能库列表页）。

```html
<a href="/skills.html" class="demo-btn-download">
  <svg>...</svg>
  <span>下载 Skill</span>
</a>
```

### 修改要求

每个 Demo 的"下载 Skill"按钮应指向该 Demo 所属的 Skill 展示页。例如：
- 傅里叶级数 Demo → `/skills/jingbo-edu-math-magazine-lecture-v0.1.html`
- DNA 双螺旋 Demo → `/skills/jingbo-edu-3d-bio-structure-v0.1.html`

### Demo → Skill 映射

根据 `skills.html` 中的 20 个 Skill 数据和 `docs/04-Skill生成/Demo-Skill映射表.md`，构建完整映射：

| Skill ID | Skill 展示页 | 包含的 Demo（demos/ 目录下） |
|----------|-------------|---------------------------|
| 3d-bio-structure | jingbo-edu-3d-bio-structure-v0.1.html | dna-double-helix, cell-structure, cell-division-3d, blood-circulation-3d, human-organs |
| 3d-micro-structure | jingbo-edu-3d-micro-structure-v0.1.html | 3d-molecule-viewer, atomic-structure, crystal-structure, electron-cloud-orbitals, hybrid-orbitals-bonding, vsepr-molecular-geometry |
| 3d-celestial-motion | jingbo-edu-3d-celestial-motion-v0.1.html | solar-system, moon-phases |
| 3d-earth-science | jingbo-edu-3d-earth-science-v0.1.html | earth-seasons, plate-tectonics, earth-terrain-3d |
| 3d-math-geometry | jingbo-edu-3d-math-geometry-v0.1.html | polyhedron-cross-section, conic-section-3d |
| math-magazine-lecture | jingbo-edu-math-magazine-lecture-v0.1.html | fourier-series, pythagorean-proof, bayes-theorem, calculus-limits-derivatives, derivative-secant-tangent, riemann-sum-integral, taylor-series-expansion |
| advanced-calculus | jingbo-edu-advanced-calculus-v0.1.html | (与 math-magazine-lecture 有重叠，需确认) |
| probability-stats-viz | jingbo-edu-probability-stats-viz-v0.1.html | buffon-needle-clt |
| physics-astronomy-lecture | jingbo-edu-physics-astronomy-lecture-v0.1.html | time-dilation, electricity-history, big-bang-theory |
| chemistry-lecture | jingbo-edu-chemistry-lecture-v0.1.html | periodic-table-history, chemical-equilibrium |
| life-science-lecture | jingbo-edu-life-science-lecture-v0.1.html | evolution-evidence, photosynthesis, immune-system |
| humanities-lecture | jingbo-edu-humanities-lecture-v0.1.html | climate-stripes, supply-demand, tang-poetry-golden-age, cosmic-human-timeline |
| math-graph-tool | jingbo-edu-math-graph-tool-v0.1.html | conic-sections, trig-wave-generator, function-plotter, fractal-geometry-generator, compound-interest-calculator, unit-circle-trig, linear-transform-matrix |
| trig-circle-viz | jingbo-edu-trig-circle-viz-v0.1.html | (可能已合并到 math-graph-tool) |
| linear-algebra-viz | jingbo-edu-linear-algebra-viz-v0.1.html | (可能已合并到 math-graph-tool) |
| physics-experiment-sim | jingbo-edu-physics-experiment-sim-v0.1.html | projectile-motion, circuit-simulation, lever-pulley, lens-imaging-simulator, simple-harmonic-motion, damped-harmonic-motion, electric-field-lines, lens-mirror-optics, circuit-builder-current |
| cs-algorithm-viz | jingbo-edu-cs-algorithm-viz-v0.1.html | sorting-algorithms, binary-tree-visualization, caesar-cipher-cryptography |
| biochem-model-sim | jingbo-edu-biochem-model-sim-v0.1.html | mendelian-genetics, chemical-equilibrium-sim, population-growth-model |
| art-music-creative | jingbo-edu-art-music-creative-v0.1.html | color-theory, piano-scale-sound-wave |
| history-map-narrative | jingbo-edu-history-map-narrative-v0.1.html | libai-life-journey, silk-road-trade, pacific-war-timeline, age-of-exploration, buddhism-spread-china, industrial-revolution, long-march-route, china-world-timeline, dynasty-territory-evolution |

### 还需检查的 Demo

以下 Demo 目录可能存在但未在上表中列出，需要确认归属：
- `demos/C1-methane-combustion.html`
- `demos/M1-solid-geometry.html`
- `demos/protein-synthesis-animation/`
- `demos/human-anatomy-3d/`
- `demos/photosynthesis/`（可能与 life-science-lecture 重复）
- 其他未列出的 Demo

### 执行方式

1. **构建完整映射表**：遍历 `demos/` 目录下所有 Demo，根据其内容和所属 Skill 确定映射
2. **批量修改**：用 Python 脚本读取每个 Demo HTML，将 `href="/skills.html"` 替换为对应的 `href="/skills/jingbo-edu-*.html"`
3. **验证**：随机检查几个 Demo，确认"下载 Skill"按钮指向正确的技能展示页

### Python 脚本参考

```python
import os, re

# Demo 路径 → Skill 展示页 URL 的映射
demo_to_skill = {
    'demos/fourier-series/index.html': '/skills/jingbo-edu-math-magazine-lecture-v0.1.html',
    'demos/dna-double-helix/index.html': '/skills/jingbo-edu-3d-bio-structure-v0.1.html',
    # ... 完整映射
}

for demo_path, skill_url in demo_to_skill.items():
    with open(demo_path, 'r', encoding='utf-8') as f:
        content = f.read()
    content = content.replace('href="/skills.html"', f'href="{skill_url}"')
    with open(demo_path, 'w', encoding='utf-8') as f:
        f.write(content)
```

---

## 执行顺序

1. C1-1：修改 index.html 导航（约 5 分钟）
2. C1-2：修改 demos.html 导航（约 5 分钟）
3. C1-3：修改 skills.html 导航（约 5 分钟）
4. C1-4：修改 20 个技能展示页导航（约 15 分钟，可脚本批量处理）
5. C1-5：修改 70+ 个 Demo 内页导航（约 20 分钟，需脚本批量处理）
6. C2：构建 Demo→Skill 映射并批量修改下载按钮（约 30 分钟）
7. 本地预览验证

## 验证清单

- [ ] 所有页面导航栏第一个链接为"首页"
- [ ] 首页链接在 index.html 上为 active 状态
- [ ] Demo 内页 `demo-navbar` 中有首页入口
- [ ] 傅里叶级数 Demo 的"下载 Skill"指向 math-magazine-lecture 展示页
- [ ] DNA 双螺旋 Demo 的"下载 Skill"指向 3d-bio-structure 展示页
- [ ] 随机抽查 5 个 Demo，"下载 Skill"均指向正确的技能展示页
- [ ] 所有导航链接可正常跳转
