# 景礴 Skill：艺术音乐创意工具

## Skill 信息

- **名称**：艺术音乐创意工具
- **类型**：交互工具型（Interactive Tool）
- **学科**：艺术 · 音乐
- **技术栈**：chroma.js + Tone.js + Web Audio API
- **CDN**：
  - `https://cdn.jsdelivr.net/npm/chroma-js@2.4.2/chroma.min.js`
  - `https://cdn.jsdelivr.net/npm/tone@14.7.77/build/Tone.js`

## 框架描述

生成艺术与音乐的交互式创意工具页面。支持视听联动，参数调节实时影响视觉和听觉效果。适用于色彩理论与配色方案、钢琴音阶与声波形可视化等任何需要视听双重感知的跨学科创意可视化。

## 布局规范

```
┌─────────────────────────────────────────┐
│  [标题栏]                                │
├──────────────┬──────────────────────────┤
│              │                          │
│  创意参数面板  │      视听可视化画布        │
│  (色彩/音阶)  │   (Canvas + Web Audio)   │
│              │                          │
│  [视听控制]   │      [色彩/波形/频谱]     │
│  [参数显示]   │      [实时反馈]           │
└──────────────┴──────────────────────────┘
```

- 左侧创意参数面板（固定宽度 280-320px），暖色浅底
- 右侧可视化画布自适应剩余空间，视听联动
- 参数面板包含：色彩选择、音阶选择、播放控制
- 可视化区域：色轮/波形/频谱、实时视听反馈

## 交互模式

1. **色彩调节**：选择基色、调整色相饱和明度，实时生成配色方案
2. **音阶交互**：点击钢琴键播放音符，实时显示波形与频谱
3. **视听联动**：音符触发色彩变化，色彩映射为音高
4. **参数控制**：滑块调节色彩参数、音频参数
5. **实时反馈**：波形、频谱、色彩空间数据同步显示

## 视觉风格

- **背景**：暖色浅底 `linear-gradient(135deg,#f0e8e0,#e6d8cc)`
- **主色调**：绿色系 `#059669`（交互工具标识）
- **参数面板**：`rgba(255,255,255,0.85)` + 柔和边框
- **可视化画布**：白色背景，丰富的色彩与波形展示
- **强调色**：根据色彩理论动态生成，波形青 `#06b6d4`
- **字体**：系统无衬线字体，标题 16px bold，频率/色值 13px monospace

## 数据输入格式

用户用自然语言描述要生成的创意工具，例如：
- "生成一个色彩理论交互工具"
- "做一个钢琴音阶与声波可视化"

AI 应根据描述：
1. 确定要实现的创意工具类型（色彩/音乐/视听联动）
2. 设计合适的参数控制项（色相、音阶、波形类型等）
3. 实现视听联动与实时反馈
4. 添加波形、频谱、色彩空间可视化

## 视听联动要求

- 色彩工具使用 chroma.js 进行色彩空间转换与配色方案生成
- 音乐工具使用 Tone.js + Web Audio API 实现音频合成与播放
- 视听联动：音符触发色彩动画，色彩变化映射音高
- 波形与频谱使用 AnalyserNode 实时获取并绘制

## 渲染要求

```javascript
// 视听联动：音符触发色彩与波形
function playNote(frequency) {
  synth.triggerAttackRelease(frequency, '8n');
  // 实时绘制波形
  analyser.getByteTimeDomainData(waveform);
  drawWaveform(waveform);
  // 音高映射色彩
  const color = chroma.hsl(mapFreqToHue(frequency), 0.8, 0.5);
  drawColorEffect(color);
}
// 色彩理论：生成配色方案
function generatePalette(baseColor) {
  return {
    complementary: chroma(baseColor).set('hsl.h', '+180'),
    analogous: [chroma(baseColor).set('hsl.h', '+30'), chroma(baseColor).set('hsl.h', '-30')],
    triadic: [chroma(baseColor).set('hsl.h', '+120'), chroma(baseColor).set('hsl.h', '+240')]
  };
}
```

## 质量要求

1. 音频播放无延迟，波形绘制流畅（目标 60fps）
2. 色彩计算准确，符合色彩理论
3. 初始加载 < 2 秒（含音频上下文初始化）
4. 支持响应式（移动端纵向布局）
5. 视听联动自然协调
6. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个色彩理论交互工具，色轮/配色方案/色彩空间转换"
- "做一个钢琴音阶与声波可视化，交互钢琴+实时波形频谱"
- "创建一个视听联动的色彩音乐工具，色彩变化触发音符"
- "生成一个色环配色方案生成器，支持互补色/类似色/三角色"
- "做一个音频频谱可视化器，多种波形实时展示"

## 参考案例

- [色彩理论交互式可视化](https://jingbo.xyz/demos/color-theory/index.html)
- [钢琴音阶与声波可视化](https://jingbo.xyz/demos/piano-scale-sound-wave/index.html)
