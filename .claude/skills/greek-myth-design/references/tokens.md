# greek-myth-design — Tokens

## 0. PRIMITIVES

### Color Ramps

**Neutral** (warm parchment — 暖色调羊皮纸灰，黄棕底调)

| Step | Hex | Use |
|------|-----|-----|
| 50 | `#FAF6EE` | 最浅奶油 |
| 100 | `#F5F0E8` | 主背景羊皮纸色 |
| 150 | `#EDE6D6` | 卡片底色 |
| 200 | `#E0D5BF` | 深一档卡片 |
| 300 | `#C4A882` | 主描边色 |
| 400 | `#A89880` | 辅助标注文字 |
| 500 | `#8B6E4E` | 强描边、深层次 |
| 600 | `#6B5744` | 次要说明文字 |
| 700 | `#4A3828` | 深棕，较少使用 |
| 800 | `#3A2818` | 深色区域 |
| 900 | `#2C1F0E` | 主体文字深棕黑 |
| 950 | `#1A1008` | 最深，暗色背景 |

**Brand — Deep Gold 深金**

| Step | Hex |
|------|-----|
| 50 | `#FDF8EC` |
| 100 | `#FAF0D0` |
| 200 | `#F0D88A` |
| 300 | `#D4A843` |
| 400 | `#C49020` |
| 500 | `#B8860B` — primary accent 深金 |
| 600 | `#9A6F08` |
| 700 | `#7A5C1E` |
| 800 | `#5C4216` |
| 900 | `#3D2C0A` |
| 950 | `#1E1505` |

**Status Colors**

| Color | 50 (bg tint) | 500 (foreground) | 900 (dark tint) |
|-------|-------------|-----------------|-----------------|
| Red   | `#F9EDED` | `#8B3A3A` | `#4A1A1A` |
| Green | `#EFF4EB` | `#5C7A4E` | `#2A3C22` |
| Amber | `#FDF8EC` | `#B8860B` | `#3D2C0A` |

### Spacing Primitives

`0, 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80`

### Radii Primitives

`0, 2, 4` — 直角为主，仅容器允许最大 2px 微圆角

---

## 1. TYPOGRAPHY

### Font Stack

| Role | Font | Fallback | Weight | Use |
|------|------|----------|--------|-----|
| **Display** | `"Cinzel Decorative"` | `"Cinzel", "Georgia", serif` | 700 | 神祇名大标题、产品展示标题 |
| **Heading / UI** | `"Cinzel"` | `"Georgia", "Times New Roman", serif` | 400–700 | 页面标题、按钮、标签、注释 |
| **Body / 正文** | `"Noto Serif SC"` | `"Georgia", "宋体", "SimSun", serif` | 400–500 | 中文正文段落、选项内容、描述 |
| **Mono** | `"Courier New"` | `"Courier", monospace` | 400 | ID编号（仅用于极少量技术性数据） |

### Mono Font Rules

**`mono_for_code`: false** · **`mono_for_metrics`: false**

本设计语言的强调色是宋体的古典温度，非等宽的工程感。数字（分数、百分比）使用 Cinzel 字体而非 Mono，保持视觉一致性。

- **`mono_for_code: false`:** 这是一个内容阅读型产品，无代码展示需求。
- **`mono_for_metrics: false`:** 人格分值、百分比等数据使用 Cinzel 字体，与标签系统保持一致，Mono 仅用于极少数技术 ID。

**字体加载（Google Fonts）：**
```html
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Cinzel+Decorative:wght@400;700&family=Noto+Serif+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
```

### Type Scale

| Token | Size | Line Height | Letter Spacing | Weight | Use |
|-------|------|-------------|----------------|--------|-----|
| `--display` | 48px | 1.1 | 0.15em | 700 | 神祇名展示（结果页大标题） |
| `--heading` | 20px | 1.3 | 0.2em | 600 | 页面标题、屏幕标题 |
| `--subheading` | 14px | 1.4 | 0.2em | 400 | 章节小标题、卡片标题 |
| `--body` | 14px | 2.0 | 0.05em | 400 | 正文段落（中文必须 2.0 行高） |
| `--body-sm` | 12px | 1.75 | 0.05em | 400 | 次要说明、注释 |
| `--caption` | 10px | 1.4 | 0.2em | 400 | 标签、时间戳、序号 |
| `--label` | 10px | 1.4 | 0.15em | 400 | 微标签、辅助标注 |

### Typographic Rules

- 标题（Cinzel）字间距 0.12em–0.25em；英文副标题可宽至 0.35em–0.5em
- 正文中文行高必须 ≥ 2.0（给呼吸感，参考 Witch Test 图的极致留白）
- 每屏最多 2 种字体角色并存（Cinzel + Noto Serif SC）
- 禁止在同一段落内混排两种字体
- 数字数据（85%、第3题）使用 Cinzel，不用 Mono

---

## 2. COLOR SYSTEM (Semantic Tokens)

### Primary Mode (Light — 羊皮纸浅色模式)

| Token | Primitive | Hex | Role |
|-------|-----------|-----|------|
| `--background` | `{neutral.100}` | `#F5F0E8` | 页面背景羊皮纸色 |
| `--bg` | — | `var(--background)` | Shorthand alias |
| `--surface1` | `{neutral.150}` | `#EDE6D6` | 卡片、浮层容器 |
| `--surface2` | `{neutral.200}` | `#E0D5BF` | 二级卡片、分组背景 |
| `--surface3` | `{neutral.300}` | `#C4A882` | 三级面，强调描边同色 |
| `--border` | `{neutral.300}` | `#C4A882` | 微妙描边、卡片边缘 |
| `--border-visible` | `{neutral.500}` | `#8B6E4E` | 强描边、章节卡、输入焦点 |
| `--text1` | `{neutral.900}` | `#2C1F0E` | 主体文字深棕黑 |
| `--text2` | `{neutral.600}` | `#6B5744` | 次要说明文字中棕 |
| `--text3` | `{neutral.500}` | `#8B6E4E` | 辅助标注浅棕灰 |
| `--text4` | `{neutral.400}` | `#A89880` | 禁用文字、占位符 |
| `--accent` | `{brand.500}` | `#B8860B` | 金色强调（标题、按钮、高亮） |
| `--accent-subtle` | `{brand.50}` | `#FDF8EC` | 金色微底（选中态背景） |
| `--success` | `{green.500}` | `#5C7A4E` | 完成、通过（橄榄绿） |
| `--warning` | `{amber.500}` | `#B8860B` | 警告（复用金色） |
| `--error` | `{red.500}` | `#8B3A3A` | 错误、取消（暗砖红） |

### Secondary Mode (Dark — 神庙深夜模式)

| Token | Primitive | Hex | Role |
|-------|-----------|-----|------|
| `--background` | `{neutral.950}` | `#1A1008` | 最深背景 |
| `--surface1` | `{neutral.900}` | `#2C1F0E` | 主卡片（主体文字色变背景） |
| `--surface2` | `{neutral.800}` | `#3A2818` | 二级卡片 |
| `--surface3` | `{neutral.700}` | `#4A3828` | 三级面 |
| `--border` | `{neutral.700}` | `#4A3828` | 微妙描边 |
| `--border-visible` | `{neutral.600}` | `#6B5744` | 可见描边 |
| `--text1` | `{neutral.50}` | `#FAF6EE` | 主体文字奶油白 |
| `--text2` | `{neutral.300}` | `#C4A882` | 次要文字暖米 |
| `--text3` | `{neutral.400}` | `#A89880` | 辅助标注 |
| `--text4` | `{neutral.500}` | `#8B6E4E` | 禁用文字 |
| `--accent` | `{brand.300}` | `#D4A843` | 亮金（暗色模式下更明亮） |
| `--accent-subtle` | `{brand.950}` | `#1E1505` | 金色微底暗版 |
| `--success` | `{green.500}` | `#5C7A4E` | 橄榄绿 |
| `--warning` | `{amber.500}` | `#B8860B` | 金色警告 |
| `--error` | `{red.500}` | `#8B3A3A` | 砖红错误 |

### Accent & Status Tints

| Token | Light | Dark | Usage |
|-------|-------|------|-------|
| `--accent-subtle` | `#FDF8EC` | `#1E1505` | 选中态背景、强调底色 |
| `--success-bg` | `#EFF4EB` | `rgba(92,122,78,0.15)` | 成功状态底色 |
| `--warning-bg` | `#FDF8EC` | `rgba(184,134,11,0.12)` | 警告状态底色 |
| `--error-bg` | `#F9EDED` | `rgba(139,58,58,0.15)` | 错误状态底色 |

### Color Usage Rules

- **背景**：永远羊皮纸色系，禁止纯白 `#FFFFFF` 和纯黑 `#000000`
- **文字**：主体文字用深棕 `#2C1F0E`，不用纯黑；深色模式用奶油白 `#FAF6EE`
- **强调**：只有金色系做强调，不引入其他彩色（蓝/紫/粉）
- **卡片**：`#F5F0E8` 底色 + `#C4A882` 描边，不用圆角或阴影
- **状态色**：绿/红仅用于功能性反馈，不做装饰

---

## 3. SPACING

### Scale (4px base grid)

| Token | Value | Use |
|-------|-------|-----|
| `--space-2xs` | 4px | 序号圆点与文字间距、微小光学调整 |
| `--space-xs` | 8px | 图标到标签、标签内边距 |
| `--space-sm` | 12px | 组件内元素间距、列表项间距 |
| `--space-md` | 16px | 标准内边距、卡片内元素间距 |
| `--space-lg` | 24px | 卡片内边距、章节内间距 |
| `--space-xl` | 32px | 章节间距、按钮外边距 |
| `--space-2xl` | 48px | 主要区块分隔 |
| `--space-3xl` | 64px | 屏幕级分隔 |
| `--space-4xl` | 80px | Hero 呼吸空间 |

---

## 4. BORDERS & RADII

### Radii Scale

| Token | Value | Use |
|-------|-------|-----|
| `--radius-element` | 0px | 复选框、图标容器 |
| `--radius-control` | 0px | 按钮、输入框（直角线框） |
| `--radius-component` | 0px | 卡片、面板（直角线框） |
| `--radius-container` | 2px | 模态框（极微圆角，几乎察觉不到） |
| `--radius-pill` | 2px | 标签/Badge（古典感方形标签） |

### Border Treatment

| Element | Border |
|---------|--------|
| Cards / Surfaces | `1px solid #C4A882` |
| Section Cards | `1px solid #8B6E4E` (更深) |
| Buttons | `1px solid #7A5C1E` |
| Inputs | `none + border-bottom: 1px solid #8B6E4E` |
| Tags / Chips | `1px solid #7A5C1E` |
| Dividers | 渐变线：`transparent → #8B6E4E → transparent` |

**Corner Philosophy:** 0px 直角。这是古典线框美学的核心——直角的精确感比任何圆角都更有仪式感和古籍质感。`border-radius` 在卡片和按钮上严格禁止超过 4px。

---

## 5. ELEVATION & SHADOWS

| Level | Light Mode | Dark Mode | Use |
|-------|-----------|----------|-----|
| **0** | None | None | 所有元素（flat 策略） |
| **1** | `border: 1px solid #C4A882` | `border: 1px solid #4A3828` | 基础卡片（通过描边表达层次） |
| **2** | `border: 1px solid #8B6E4E` | `border: 1px solid #6B5744` | 章节卡、活跃容器 |
| **3** | `border: 1px solid #8B6E4E + background: #EDE6D6` | `border: 1px solid #6B5744 + bg: #2C1F0E` | 模态框（背景+描边组合） |

**Elevation Strategy: Flat.** 无任何 `box-shadow`。深度通过描边颜色深浅和背景色差异来表达，不使用投影。

---

## 6. MOTION & INTERACTION

### Personality

**Ritual（仪式感）**— 动效服务于内容和仪式感，不抢主角。重要时刻允许更隆重的动效（进入结果页的淡入），普通交互保持克制。翻书感 easing，不弹跳。

### Timing

| Type | Duration | Easing | Use |
|------|----------|--------|-----|
| **Micro** | 200ms | `ease-out` | 按钮按压、颜色变化、hover 状态 |
| **Standard** | 350ms | `cubic-bezier(0.22, 1, 0.36, 1)` | 卡片展开、内容过渡、进度条 |
| **Emphasis** | 500ms | `cubic-bezier(0.22, 1, 0.36, 1)` | 结果页进场、神祇揭示动效 |

### Interaction States

- **Hover 按钮:** `border-color` 加深 + `background: rgba(184,134,11,0.08)` 微填充；无 scale 放大
- **Active 按钮:** `background: rgba(184,134,11,0.12)` 稍深填充
- **Selected 选项:** `border-color: #B8860B` + `background: rgba(184,134,11,0.08)` + 文字变金色
- **Focus 输入:** `border-bottom-color: #B8860B`
- **页面切换:** `opacity: 0 → 1`，duration 450ms，无位移，无 slide

---

## 7. ICONOGRAPHY

> **⚠ 设计说明。** 本设计语言**主要使用 Unicode 符号**（✦ ◆ ☽ ⊱ ⊰ ✠ 等）作为装饰和标识系统。这不是因为图标库不够好，而是因为 Unicode 符号与古典羊皮纸美学更契合，无需外部资源。标准图标库作为功能性备选。

### 核心符号体系（Unicode 优先）

| 类型 | 符号 | 用途 |
|------|------|------|
| 星形装饰 | `✦ ✧ ✶ ✷ ✸` | 分割点、角花装饰、按钮装饰 |
| 月相 | `☽ ☾ ● ◑ ◐ ◒` | 月亮主题装饰、页眉装饰 |
| 方向菱形 | `◆ ◇ ▲ △ ▼ ▽` | 列表前缀、强调标记 |
| 装饰括弧 | `⊱ ⊰` | 分割线两端装饰 |
| 古典标记 | `⊕ ⊗ ⊙ ✠ ❖` | 章节标记、神祇属性 |
| 月相序列 | `🌑 🌒 🌓 🌔 🌕 🌖 🌗 🌘` | 月相选择器、加载指示 |

### Fallback Kit（功能性图标需要时）

- **Kit:** Phosphor (thin weight)
- **Weight / variant:** thin (1px stroke)
- **Match score:** medium
- **Why this kit:** 细描边与古典美学最接近；人文感不过分工业化。但实际上本设计尽量使用 Unicode 符号而非图标库。
- **CDN:** `https://unpkg.com/@phosphor-icons/web@2/src/thin/style.css`
- **Usage:** `<i class="ph-thin ph-ICON-NAME"></i>`

### 神祇专属图标（Emoji + Unicode 混合）

```
⚡ 宙斯    👑 赫拉    🦉 雅典娜   ☀️ 阿波罗
🌙 阿尔忒弥斯  🔱 波塞冬   🌾 得墨忒耳  🪶 赫尔墨斯
🌹 阿芙罗狄忒  ⚔️ 阿瑞斯   🔥 赫淮斯托斯  🍇 狄俄尼索斯
💀 哈迪斯   🌺 珀耳塞福涅  💘 厄洛斯   🏆 尼刻
```

### Sizes

| Context | Size |
|---------|------|
| Unicode 装饰符号（分割线点） | 0.7rem — 0.8rem |
| Unicode 列表前缀 | 1em（与正文同大） |
| 神祇 Emoji 头像 | 3rem — 4rem（filter: sepia(0.2) 加复古感） |
| Phosphor 功能性图标（按钮内） | 16px |

### Color rule

Unicode 符号颜色：装饰点用 `--accent`（金色），分割线用 `--border-visible`（深米色），列表前缀用 `--text3`（浅棕）。Emoji 图标加 `filter: sepia(0.2)` 使其融入羊皮纸色调。

### Don't

- 不要把图标库图标用于纯装饰目的（Unicode 符号更合适）
- 不要在正文行内插入 Emoji（会破坏文字排版节奏）
- 不要使用彩色 Emoji 而不加 sepia 滤镜（会破坏色调统一）
- Never claim these are the brand's real icons — they are a best-match fallback.
