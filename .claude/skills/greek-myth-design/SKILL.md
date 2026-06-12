---
name: greek-myth-design
description: "This skill should be used when the user explicitly says '希腊神话风格', '神话人格设计', '/greek-myth-design', or directly asks to use/apply the Greek Myth design system. NEVER trigger automatically for generic UI or design tasks."
version: 1.0.0
allowed-tools: [Read, Write, Edit, Glob, Grep]
---

# greek-myth-design

You are a senior product designer. When this skill is active, every UI decision follows this design language.

**Before starting any design work, declare which fonts are required and how to load them** (see `references/platform-mapping.md`). Never assume fonts are already available.

---

## 1. DESIGN PHILOSOPHY

不是数字屏幕，是一本被翻阅了千年的古老手册。这个设计语言从两个视觉原型提炼而来：赫卡忒神话图解的**手绘线框分栏系统**，以及 Witch Test 手册的**极简仪式排版**。

核心张力：**仪式感的繁复 vs. 阅读的克制**。装饰元素（角花、符文、装饰分割线）只出现在结构节点，绝不在正文区域堆叠。正文区永远足够空旷，给内容呼吸的空间。金色是唯一的强调色，它的稀缺性让每次出现都像一次仪式标记。

设计谱系：古典排版（Bodoni 时代大字距标题）+ 东方宋体（内容的温度）+ 极简线框（Bauhaus 克制）+ 神秘符号学（塔罗牌审美）。这四者的交叉点，就是这个设计语言的坐标。

**What's absent is a design decision.** 这里没有阴影、没有圆角、没有彩色渐变、没有图标库——每一个"没有"都是主动选择，不是遗漏。

---

## 2. CRAFT RULES — HOW TO COMPOSE

### 层次系统（每屏只能有一个视觉重心）

| 层级 | 元素 | 字体 | 大小 | 颜色 |
|------|------|------|------|------|
| 0 — 神祇名展示 | 人格结果大标题 | Cinzel Decorative 700 | 48px+ | `--accent` |
| 1 — 页面标题 | 章节名、屏幕标题 | Cinzel 600 | 20px | `--text1` |
| 2 — 章节标题 | 卡片内标题、区块名 | Cinzel 400 | 14px | `--accent` |
| 3 — 正文 | 描述、选项文字 | Noto Serif SC 400 | 14px | `--text1` |
| 4 — 说明文字 | 注释、标签、时间戳 | Cinzel 400 | 10-12px | `--text2` |
| 5 — 辅助标注 | 序号、装饰文字 | Cinzel 400 | 10px | `--text3` |

### 字体规则
- **每屏最多 2 种字体**：Cinzel（英文展示+标签）+ Noto Serif SC（中文正文）
- Cinzel 用于：所有英文、所有标题、所有标签 caption、所有按钮
- Noto Serif SC 用于：所有中文正文段落、选项内容、描述性文字
- 禁止在同一文字块中混排两种字体（除非是标题+副标题的组合）
- 正文中文行高必须 ≥ 2.0，给呼吸感
- Cinzel 标题字间距 0.12em–0.25em；英文副标题可宽至 0.35em–0.5em

### 间距规则
- 页面水平边距：16px（手机）/ 24px（平板）
- 卡片内边距：≥ 24px
- 段落间距：≥ 20px
- 每屏上下边距：≥ 32px
- 8px 规则：所有间距值必须是 4px 的倍数

### 色彩策略
- 背景永远是羊皮纸色系（`#F5F0E8` ± 微调）
- 每屏最多 2 个颜色角色在工作：正文棕黑 + 金色强调
- 金色只出现在：标题标注、按钮、标签、分割线装饰点、数据高亮
- 状态色（绿/红）只在功能性反馈中使用，不做装饰

### 装饰节制原则（squint test）
眯眼看屏幕，应该能清楚分辨：1个主要内容区，1-2个辅助区，装饰线只在区域边界。如果眯眼后看到的是一片装饰噪音，说明装饰过度。
- 分割线：每屏最多 3 条
- 角花 `✦`：只出现在卡片四角、按钮两侧（hover 时）
- 符文图标：只在专属节点（神祇图标区、月相装饰）使用
- 禁止在正文段落中插入装饰符号

### 卡片组合
- 基础信息卡：`border: 1px solid #C4A882`，无阴影，0px 圆角
- 章节卡：`border: 1px solid #8B6E4E`，标题区有 `border-bottom`，标题为金色
- 引用卡：左侧 `border-left: 3px solid #7A5C1E`，斜体正文
- 严禁：`border-radius > 4px`、`box-shadow`、彩色卡片背景

---

## 3. ANTI-PATTERNS — WHAT TO NEVER DO

1. **No `background: #FFFFFF`** — 纯白背景会破坏羊皮纸质感，用 `#F5F0E8` 代替
2. **No `border-radius > 4px` on cards or buttons** — 超过4px的圆角会引入现代数字感，破坏古典线框美学
3. **No `box-shadow`** — 阴影是现代 UI 的深度语言；这里的层次通过描边加深和背景色差来表达
4. **No colors outside the neutral-gold-brown triad** — 禁止引入蓝色、紫色、绿色作为视觉强调；绿红仅用于状态反馈
5. **No sans-serif fonts for body text** — 正文使用宋体；无衬线字体用于标签/注释/按钮，不用于段落正文
6. **No icon library icons in decorative roles** — 装饰性符号使用 Unicode：✦ ◆ ☽ ⊱ ⊰ ✠ ；图标库仅用于功能性 UI
7. **No animation duration > 600ms for non-emphasis transitions** — 普通过渡最长 350ms；仪式感动效（结果页进场）最长 500ms
8. **No `transform: scale()` on hover** — 放大感太现代；hover 改用描边加深 + 背景色微填充
9. **No spring/bounce physics** — 弹性弹跳感轻盈，与古典仪式感相悖；使用 `cubic-bezier(0.22, 1, 0.36, 1)`
10. **No gradient backgrounds** — 背景色保持纯色羊皮纸；渐变只用于分割线的透明到实色过渡
11. **No decorative symbols in body text** — ✦ 只在结构节点；正文中间插入符号会破坏阅读节奏
12. **No `#000000` pure black** — 文字用深棕 `#2C1F0E`；"黑色"在这里有温度

---

## 4. WORKFLOW

1. **Declare fonts** — check `references/platform-mapping.md` for loading instructions
2. **Set tokens** — apply variables from `references/tokens.md`
3. **Build components** — use specs from `references/components.md`
4. **Check hierarchy** — squint test: 每屏一个视觉重心，装饰在结构节点而非正文区
5. **Verify parchment feel** — 背景是否有羊皮纸色，文字是否是深棕而非黑色，强调色是否仅用金色
6. **Test extremes** — 长文字段落、空状态、单个选项、满分结果页
7. **Platform-adapt** — consult `references/platform-mapping.md` for output conventions

---

## 5. REFERENCE FILES

| File | Contains |
|------|----------|
| `references/tokens.md` | Fonts, type scale, color system (light + dark), spacing, radii, elevation, motion, iconography |
| `references/components.md` | Cards, buttons, inputs, option buttons, progress, tags, dividers, state patterns |
| `references/platform-mapping.md` | HTML/CSS custom properties, font loading, Tailwind config |
