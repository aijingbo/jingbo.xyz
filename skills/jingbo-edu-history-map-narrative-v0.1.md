# 景礴 Skill：历史地图叙事器

## Skill 信息

- **名称**：历史地图叙事器
- **类型**：时空叙事型（Narrative Map）
- **学科**：历史
- **技术栈**：Leaflet + D3.js + vis-timeline
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/leaflet@1.9.4/dist/leaflet.css`
  - `https://cdn.jsdelivr.net/npm/leaflet@1.9.4/dist/leaflet.js`
  - `https://cdn.jsdelivr.net/npm/d3@7/dist/d3.min.js`
  - `https://cdn.jsdelivr.net/npm/vis-timeline@7.7.3/styles/vis-timeline-graph2d.min.css`
  - `https://cdn.jsdelivr.net/npm/vis-timeline@7.7.3/standalone/umd/vis-timeline-graph2d.min.js`

## 框架描述

生成一个地图与时间轴联动的时空叙事页面，用于讲述历史人物生平、贸易路线、战争进程、文化传播等具有时空维度的历史叙事。上方或左侧为可拖拽的时间轴，中间为地图区域（事件标记 + 路线动画），点击事件节点弹出详情卡片。路线随时间推移逐步绘制，形成"边走边讲"的叙事节奏。适用于李白人生旅程、丝绸之路、长征路线、大航海时代等任何需要时空联动的历史叙事场景。

## 布局规范

```
┌─────────────────────────────────────────┐
│  [时间轴条]  ◄━━━━━━━━●━━━━━━━━━━►       │
├─────────────────────────────────────────┤
│                                          │
│                                          │
│         地图主区域                        │
│    (事件标记 + 路线动画)                  │
│                                          │
│                              ┌─────────┐ │
│                              │详情卡片  │ │
│                              │ 浮层     │ │
│                              └─────────┘ │
├─────────────────────────────────────────┤
│  [播放控制]  ⏮ ▶ ⏭   速度: 1x 2x 4x     │
└─────────────────────────────────────────┘
```

- 时间轴条位于顶部（或左侧），可拖拽/滚动推进时间
- 地图主区域占据中央大部分空间，使用 Leaflet 渲染
- 事件节点以标记形式显示在地图上，点击弹出详情卡片浮层
- 路线随时间轴推进逐步绘制，使用 D3.js 路径动画
- 底部为播放控制条（播放/暂停/跳转/速度调节）
- 详情卡片浮层位于地图右上或右侧，毛玻璃效果

## 交互模式

1. **时间轴拖拽**：拖动时间轴上的指针，推进或回溯叙事进度，地图同步更新
2. **地图缩放平移**：鼠标滚轮缩放、拖拽平移地图视图（Leaflet 原生）
3. **点击事件标记**：点击地图上的事件节点，弹出详情卡片显示标题、描述、图片
4. **路线动画播放/暂停**：点击播放按钮，路线按时间顺序逐步绘制；可暂停
5. **时间流速控制**：1x / 2x / 4x 速度切换，控制路线绘制和事件推进节奏
6. **事件跳转**：点击时间轴上的事件节点，直接跳转到对应时间和地图位置

## 视觉风格

- **背景**：暖色调古地图风格，地图瓦片使用羊皮纸质感底图
- **主色调**：路线使用赤陶色 `#c2410c`，事件节点高亮金色 `#d97706`
- **强调色**：当前激活事件使用亮金色 `#f59e0b` 发光效果
- **文字**：深棕色 `#3d2817`（浅色面板上）/ 白色 `#ffffff`（深色浮层上）
- **控制面板**：`rgba(42,32,24,0.85)` + `backdrop-filter: blur(12px)` + `border: 1px solid rgba(217,119,6,0.2)`
- **路线效果**：赤陶色实线 + 阴影投射，已走部分实色、未走部分虚线半透明
- **事件节点**：圆形标记，金色边框，中心填充深色，hover 时放大并发光
- **字体**：系统无衬线字体，标题 16px bold，正文 13px regular，时间标签使用等宽字体

## 数据输入格式

用户用自然语言描述要生成的时空叙事，例如：
- "生成一个李白生平游历路线地图"
- "做一个丝绸之路贸易路线叙事"
- "创建一个红军长征路线图"
- "生成一个大航海时代航线地图"

AI 应根据描述：
1. 确定叙事主题和历史背景
2. 查阅资料整理事件列表（时间、地点、经纬度、标题、描述）
3. 按时间顺序排列事件，生成路线点序列
4. 为每个事件添加准确的历史描述和（可选）配图
5. 设置合理的地图初始视角和缩放级别

事件列表 JSON 格式：

```json
{
  "title": "李白生平与游历路线",
  "events": [
    {
      "time": "701年",
      "location": "碎叶城",
      "lat": 42.8378,
      "lng": 75.9959,
      "title": "李白出生",
      "description": "李白出生于碎叶城（今吉尔吉斯斯坦托克马克市附近），其父李客为商人。",
      "image": "可选配图URL"
    },
    {
      "time": "725年",
      "location": "江陵",
      "lat": 30.3263,
      "lng": 112.2397,
      "title": "出蜀远游",
      "description": "李白二十五岁出蜀，顺长江而下，开始漫游生涯，途经江陵遇司马承祯。",
      "image": ""
    }
  ],
  "route": [
    [42.8378, 75.9959],
    [30.3263, 112.2397],
    [32.0603, 118.7969],
    [30.5728, 104.0668]
  ]
}
```

- `events`：事件列表，每个事件包含时间、地点名、经纬度、标题、描述、可选配图
- `route`：路线点序列，按时间顺序排列的 `[lat, lng]` 坐标数组
- 路线点与事件节点可不完全重合（事件为关键节点，路线为完整路径）

## 地图与路线绘制要求

- 使用 Leaflet 初始化地图，设置古地图风格瓦片层（如 Stamen Terrain 或自定义羊皮纸瓦片）
- 事件节点使用 Leaflet CircleMarker 或自定义 DivIcon 渲染
- 路线绘制使用 D3.js 叠加在 Leaflet 上（通过 SVG overlay 或 map pane）
- 路线动画使用 `stroke-dasharray` + `stroke-dashoffset` 实现逐步绘制效果
- 时间轴使用 vis-timeline 组件，与地图事件双向联动
- 已经过的路线段显示为赤陶色实线，未到达段显示为虚线半透明
- 当前事件节点高亮放大，并自动平移地图至该节点居中

路线动画核心代码：

```javascript
// 路线逐步绘制动画
const pathLength = pathElement.getTotalLength();
pathElement
  .attr('stroke-dasharray', pathLength)
  .attr('stroke-dashoffset', pathLength)
  .transition()
  .duration(duration)
  .ease(d3.easeLinear)
  .attr('stroke-dashoffset', 0);

// 时间轴与地图联动
timeline.on('rangechange', () => {
  const current = timeline.getCurrentTime();
  updateMapToTime(current);
});
```

## 质量要求

1. 地图渲染流畅，缩放平移无明显卡顿
2. 路线动画流畅，与时间轴推进同步
3. 初始加载 < 3 秒（含地图瓦片）
4. 支持响应式（移动端触控缩放平移）
5. 所有事件节点可点击，详情卡片内容准确、史实严谨
6. 时间轴拖拽与地图更新实时同步，延迟 < 100ms
7. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个李白生平游历路线地图"
- "做一个丝绸之路贸易路线叙事"
- "创建一个红军长征路线图"
- "生成一个大航海时代航线地图"
- "做一个二战太平洋战场时间线地图"
- "创建一个中国佛教传播路线叙事"

## 参考案例

- [李白生平与游历路线](https://jingbo.xyz/demos/libai-life-journey/index.html)
- [丝绸之路贸易路线](https://jingbo.xyz/demos/silk-road-trade/index.html)
- [二战太平洋战场时间线](https://jingbo.xyz/demos/pacific-war-timeline/index.html)
- [大航海时代与地理大发现](https://jingbo.xyz/demos/age-of-exploration/index.html)
- [中国佛教传播路线](https://jingbo.xyz/demos/buddhism-spread-china/index.html)
- [工业革命与城市化进程](https://jingbo.xyz/demos/industrial-revolution/index.html)
- [红军长征路线图](https://jingbo.xyz/demos/long-march-route/index.html)
- [朝代疆域演变](https://jingbo.xyz/demos/dynasty-territory-evolution/index.html)
- [中外对照时间轴](https://jingbo.xyz/demos/china-world-timeline/index.html)
