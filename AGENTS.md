# AGENTS.md — jingbo.xyz（上线仓库）

## 这里是什么
这是景礴学院的**线上网站仓库**。所有代码直接部署到 www.jingbo.xyz。

## 部署链路
```
git push → GitHub (aijingbo/jingbo.xyz) → Cloudflare Pages (jingbo-site) → jingbo.xyz
```

## 目录结构
```
jingbo.xyz/
├── index.html          首页
├── demos.html          课件库（75个课件）
├── skills.html         技能库（20个技能）
├── demo-gallery.html   课件画廊页
├── demos/              课件目录（每个含 index.html）
├── skills/             技能文件（.md + .html 成对）
├── assets/
│   ├── css/            样式表
│   └── img/            预览图
├── wrangler.toml       Cloudflare 部署配置
└── README.md
```

## 铁律
1. **只放网站代码** — 文档、调研、提示词放 `~/Desktop/jingbo-obsidian/`
2. **改动即上线** — push 到 main 分支会自动部署到线上
3. **不创建非网站目录** — 不要在这里建 docs/、notes/ 等文件夹
4. **新课件流程** — 先在 workspace 开发测试 → 复制到这里 → git push
5. **Git 代理** — http.proxy = http://127.0.0.1:3213（Astrill）

## 技术栈
- 纯静态 HTML/CSS/JS，无后端
- Three.js（3D课件）、GSAP（动画）、Canvas/SVG（2D课件）
- Cloudflare Pages 部署，wrangler.toml 配置
- 预览图通过 Playwright + SwiftShader 截图生成

## 设计规范
- 科学杂志风，赤陶暖调
- 主色：赤陶色 #c2410c，背景：暖米白 #faf8f5
- 字体：衬线体（标题）+ 无衬线（正文）+ 等宽（数据）
- 详见 `assets/css/design-system.css`

## 上线状态（2026-08-10）
- 域名 jingbo.xyz 已绑定 Cloudflare，DNS 已生效
- 75个课件 + 20个技能已上线
- 首页5个可交互Demo（化学/生物/地理/数学/物理）
- 课件库预览图全部为高质量截图
