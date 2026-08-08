# 工作流 B：技能库页面与 Skill 文件

> 涉及文件：`skills.html`、`skills/景礴-Edu-*.html`（20个）、`skills/景礴-Edu-*.md`（20个）
> 预计耗时：45-60 分钟

---

## B1. 技能库抬头与介绍重写

### 当前状态（skills.html 第 475-479 行）

```html
<span class="jb-kicker">技能库</span>
<h1>知识可视化 Skill 模板</h1>
<p>每个 Skill 是一套「知识画法」模板——获取后安装到 Trae 等 AI 编程助手中，说一句话就能生成对应的交互式可视化课件。20 个技能，覆盖八大学科。</p>
```

### 修改要求

用户要求：
1. 介绍文案需重写，更充分地讲解 Skill 是什么
2. "20 个技能，8 大学科"另起一行
3. 说明会不断补充更多技能
4. 提到未来开放社区上传技能
5. 传达这是一个 AI 驱动的教育社区的理念
6. "让知识可视化、触手可及"

### 修改后文案

```html
<span class="jb-kicker">技能库</span>
<h1>知识可视化 Skill 模板</h1>
<p>每个 Skill 是一套「知识画法」模板——获取后安装到 Trae 等 AI 编程助手中，说一句话就能生成对应的交互式可视化课件。</p>
<p class="page-head-meta">20 个技能，覆盖八大学科。我们会持续补充更多技能，未来也将开放社区上传——让每个老师都能把教学经验沉淀为 Skill，让知识可视化触手可及。</p>
```

需要为 `.page-head-meta` 添加样式：
```css
.page-head-meta {
  margin-top: 12px;
  font-size: 14px;
  line-height: 1.8;
  color: var(--text-faint);
  max-width: 620px;
}
```

---

## B2. Skill 文件名英文化

### 当前命名

```
skills/景礴-Edu-3d-micro-structure-v0.1.md
skills/景礴-Edu-3d-micro-structure-v0.1.html
...（共 20 组，40 个文件）
```

### 新命名规则

```
skills/jingbo-edu-3d-micro-structure-v0.1.md
skills/jingbo-edu-3d-micro-structure-v0.1.html
```

- 前缀 `景礴-Edu-` → `jingbo-edu-`
- 全小写英文
- 无中文字符

### 完整映射表

| 当前文件名 | 新文件名 |
|-----------|---------|
| 景礴-Edu-3d-bio-structure-v0.1 | jingbo-edu-3d-bio-structure-v0.1 |
| 景礴-Edu-3d-celestial-motion-v0.1 | jingbo-edu-3d-celestial-motion-v0.1 |
| 景礴-Edu-3d-earth-science-v0.1 | jingbo-edu-3d-earth-science-v0.1 |
| 景礴-Edu-3d-math-geometry-v0.1 | jingbo-edu-3d-math-geometry-v0.1 |
| 景礴-Edu-3d-micro-structure-v0.1 | jingbo-edu-3d-micro-structure-v0.1 |
| 景礴-Edu-advanced-calculus-v0.1 | jingbo-edu-advanced-calculus-v0.1 |
| 景礴-Edu-art-music-creative-v0.1 | jingbo-edu-art-music-creative-v0.1 |
| 景礴-Edu-biochem-model-sim-v0.1 | jingbo-edu-biochem-model-sim-v0.1 |
| 景礴-Edu-chemistry-lecture-v0.1 | jingbo-edu-chemistry-lecture-v0.1 |
| 景礴-Edu-cs-algorithm-viz-v0.1 | jingbo-edu-cs-algorithm-viz-v0.1 |
| 景礴-Edu-history-map-narrative-v0.1 | jingbo-edu-history-map-narrative-v0.1 |
| 景礴-Edu-humanities-lecture-v0.1 | jingbo-edu-humanities-lecture-v0.1 |
| 景礴-Edu-life-science-lecture-v0.1 | jingbo-edu-life-science-lecture-v0.1 |
| 景礴-Edu-linear-algebra-viz-v0.1 | jingbo-edu-linear-algebra-viz-v0.1 |
| 景礴-Edu-math-graph-tool-v0.1 | jingbo-edu-math-graph-tool-v0.1 |
| 景礴-Edu-math-magazine-lecture-v0.1 | jingbo-edu-math-magazine-lecture-v0.1 |
| 景礴-Edu-physics-astronomy-lecture-v0.1 | jingbo-edu-physics-astronomy-lecture-v0.1 |
| 景礴-Edu-physics-experiment-sim-v0.1 | jingbo-edu-physics-experiment-sim-v0.1 |
| 景礴-Edu-probability-stats-viz-v0.1 | jingbo-edu-probability-stats-viz-v0.1 |
| 景礴-Edu-trig-circle-viz-v0.1 | jingbo-edu-trig-circle-viz-v0.1 |

### 需要同步更新的引用

1. **`skills.html`** 中 20 个 Skill 数据的 `showcaseUrl` 字段：
   - `skills/景礴-Edu-3d-bio-structure-v0.1.html` → `skills/jingbo-edu-3d-bio-structure-v0.1.html`
   
2. **每个 Skill 展示页 HTML** 中的 CDN URL 和下载链接：
   - `https://cdn.jsdelivr.net/gh/aijingbo/jingbo.xyz@main/skills/景礴-Edu-*.md` → `.../jingbo-edu-*.md`
   - `景礴-Edu-*.md` download 链接 → `jingbo-edu-*.md`

### 执行方式

用脚本批量重命名 + 批量更新引用：

```bash
# 1. 重命名文件
cd /Users/a1/Desktop/jingbo.xyz/skills
for f in 景礴-Edu-*; do
  mv "$f" "$(echo $f | sed 's/景礴-Edu-/jingbo-edu-/')"
done

# 2. 更新 skills.html 中的引用
# 3. 更新每个 HTML 文件中的 CDN URL 和下载链接
```

---

## B3. Skill 下载机制梳理

### 当前问题

Skill MD 文件中包含了参考课件的 HTML 代码或链接。用户下载 MD 文件后，无法访问这些参考课件（因为课件文件不在本地）。

### 推荐方案：纯 MD 文档

1. **MD 文档自包含**：只包含 Skill 规范描述（框架描述、布局规范、交互模式、视觉风格、数据输入格式等）
2. **参考课件通过线上 URL 访问**：在 MD 中用链接指向 `https://jingbo.xyz/demos/xxx/index.html` 或 Cloudflare Pages 预览地址
3. **不内嵌完整 HTML 代码**：避免文件过大且本地无法运行

### MD 文件结构调整

```markdown
# 景礴 Skill：[技能名称]

## Skill 信息
- 名称、类型、学科、技术栈、CDN 依赖

## 框架描述
（保留 — 这是 Skill 的核心规范）

## 布局规范
（保留）

## 交互模式
（保留）

## 视觉风格
（保留）

## 数据输入格式
（保留）

## 参考案例
- [案例1名称](https://jingbo.xyz/demos/xxx/index.html)
- [案例2名称](https://jingbo.xyz/demos/yyy/index.html)
（改为线上链接，不内嵌代码）

## 示例指令
- "生成一个水分子 3D 结构"
- "做一个氯化钠晶体晶胞 3D 模型"
```

### 执行方式

1. 读取每个 MD 文件
2. 找到内嵌的参考课件代码块（大段 HTML）
3. 替换为线上链接
4. 保留规范描述部分

---

## B4. 复制链接确认与更新

### 当前 CDN URL 格式

```
https://cdn.jsdelivr.net/gh/aijingbo/jingbo.xyz@main/skills/景礴-Edu-3d-micro-structure-v0.1.md
```

### 更新后

```
https://cdn.jsdelivr.net/gh/aijingbo/jingbo.xyz@main/skills/jingbo-edu-3d-micro-structure-v0.1.md
```

### 验证步骤

1. 文件重命名后，推送代码到 GitHub
2. 等待 jsdelivr CDN 缓存更新（通常几分钟）
3. 访问 CDN URL 确认能正确返回 MD 文件内容
4. 在技能展示页点击"复制链接"，粘贴到浏览器验证

### 注意事项

- jsdelivr URL 中的 `@main` 分支名需与 GitHub 默认分支一致
- 推送代码后 CDN 会有缓存延迟，可用 `https://purge.jsdelivr.net/gh/aijingbo/jingbo.xyz@main/skills/jingbo-edu-*.md` 清除缓存
- URL 中无中文字符后，不需要 URL 编码，更可靠

---

## 执行顺序

1. B1：重写技能库抬头与介绍（约 10 分钟）
2. B2：重命名 Skill 文件（约 15 分钟，含脚本编写）
3. B3：清理 MD 文件中的参考课件代码（约 20 分钟）
4. B4：更新所有 CDN URL 和下载链接（约 10 分钟）
5. 本地预览验证：`http://localhost:9000/skills.html`

## 验证清单

- [ ] 技能库页面介绍文案已更新，"20个技能8大学科"另起一行
- [ ] 社区规划和持续补充的说明已添加
- [ ] 20 个 Skill 文件（.md + .html）全部重命名为纯英文
- [ ] skills.html 中的 showcaseUrl 全部更新
- [ ] 每个 Skill 展示页的 CDN URL 已更新
- [ ] MD 文件中无内嵌的参考课件 HTML 代码
- [ ] 参考案例改为线上链接
- [ ] 本地点击"复制链接"可正确复制更新后的 URL
