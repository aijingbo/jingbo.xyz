# 景礴 Skill：物理实验模拟器

## Skill 信息

- **名称**：物理实验模拟器
- **类型**：交互工具型（Interactive Tool）
- **学科**：物理
- **技术栈**：Canvas + requestAnimationFrame
- **CDN**：无外部依赖（纯原生 Canvas 2D API）

## 框架描述

生成物理实验参数化模拟页面。控制面板调节物理参数（角度、速度、电阻等），可视化区域实时展示物理过程和数据。适用于抛体运动、电路、杠杆滑轮、透镜成像、简谐运动等任何需要参数化模拟的物理实验。

## 布局规范

```
┌─────────────────────────────────────────┐
│  [标题栏]                                │
├──────────────┬──────────────────────────┤
│              │                          │
│  参数控制面板  │      物理过程可视化画布    │
│  (滑块/输入框) │   (Canvas 实时动画)      │
│              │                          │
│  [实验控制]   │      [运动轨迹/电路]      │
│  [数据显示]   │      [矢量/数据标注]      │
└──────────────┴──────────────────────────┘
```

- 左侧参数面板（固定宽度 280-320px），暖色浅底
- 右侧可视化画布自适应剩余空间，实时动画
- 参数面板包含：滑块、数字输入框、播放/暂停/重置按钮
- 可视化区域：物理场景、运动轨迹、矢量分解、实时数据

## 交互模式

1. **参数调节**：拖动滑块设置角度、速度、电阻等物理量
2. **播放控制**：开始/暂停/重置实验模拟
3. **实时数据**：速度、加速度、电流、力等数据实时显示
4. **矢量显示**：力的分解、速度方向等矢量箭头可视化
5. **轨迹追踪**：运动轨迹可选保留或清除

## 视觉风格

- **背景**：暖色浅底 `linear-gradient(135deg,#f0e8e0,#e6d8cc)`
- **主色调**：绿色系 `#059669`（交互工具标识）
- **参数面板**：`rgba(255,255,255,0.85)` + 柔和边框
- **可视化画布**：白色背景，浅灰参考网格
- **强调色**：矢量红 `#ef4444`、轨迹蓝 `#3b82f6`、数据绿 `#059669`
- **字体**：系统无衬线字体，标题 16px bold，参数标签 13px

## 数据输入格式

用户用自然语言描述要生成的物理实验模拟，例如：
- "生成一个抛体运动模拟器"
- "做一个电路实验模拟"
- "创建一个透镜成像模拟器"

AI 应根据描述：
1. 确定要模拟的物理实验类型
2. 设计合适的参数控制项（物理量、范围、单位）
3. 实现物理规律的数值计算
4. 添加实时动画、矢量可视化、数据显示

## 参数控制要求

- 所有滑块使用原生 `<input type="range">`，标注物理量和单位
- 使用 `requestAnimationFrame` 驱动动画循环
- 关键物理量实时显示当前数值
- 支持播放、暂停、重置、单步控制

## 物理计算要求

```javascript
// 动画循环驱动物理模拟
function animate(timestamp) {
  const dt = (timestamp - lastTime) / 1000;
  lastTime = timestamp;
  updatePhysics(dt);  // 更新物理状态
  draw();             // 重绘场景
  requestAnimationFrame(animate);
}
// 抛体运动示例
function updatePhysics(dt) {
  vx = v0 * Math.cos(angle);
  vy = v0 * Math.sin(angle) - g * t;
  x += vx * dt;
  y += vy * dt;
}
```

## 质量要求

1. 动画流畅（目标 60fps）
2. 物理计算准确，符合真实物理规律
3. 初始加载 < 1 秒
4. 支持响应式（移动端纵向布局）
5. 所有参数有清晰的物理量和单位标注
6. 纯单 HTML 文件，仅依赖 CDN

## 示例指令

用户安装此技能后，可以这样说：

- "生成一个抛体运动模拟器，角度和初速度可调，显示轨迹和力的分解"
- "做一个电路实验模拟，电阻电压调节，实时计算电流"
- "创建一个透镜成像模拟器，物距焦距调节，光路图实时"
- "生成一个杠杆与滑轮力学实验，力臂与平衡条件交互"
- "做一个简谐运动模拟，振幅频率阻尼参数化"

## 参考案例

- [抛体运动与力的分解](https://jingbo.xyz/demos/projectile-motion/index.html)
- [电路模拟与欧姆定律](https://jingbo.xyz/demos/circuit-simulation/index.html)
- [杠杆与滑轮力学实验](https://jingbo.xyz/demos/lever-pulley/index.html)
- [光学透镜成像模拟器](https://jingbo.xyz/demos/lens-imaging-simulator/index.html)
- [简谐运动与波动](https://jingbo.xyz/demos/simple-harmonic-motion/index.html)
- [阻尼振动模拟](https://jingbo.xyz/demos/damped-harmonic-motion/index.html)
- [电场线与等势面](https://jingbo.xyz/demos/electric-field-lines/index.html)
- [透镜与面镜光学](https://jingbo.xyz/demos/lens-mirror-optics/index.html)
- [电路搭建器](https://jingbo.xyz/demos/circuit-builder-current/index.html)
