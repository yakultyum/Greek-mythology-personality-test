# 神话人格 · 设计规范文档 DESIGN SYSTEM

> 版本 v1.0 · 2026-06-10  
> 风格定义：**羊皮纸古典 × 手绘线框 × 神秘符文 × 奶油白底**  
> 参考来源：赫卡忒神话图解 / 奥林匹斯宫殿插画 / Witch Test 极简手册

---

## 一、设计理念

### 核心关键词
**古老的** · **手工的** · **仪式感** · **可阅读的** · **神秘而不沉重**

### 风格定位
不是数字屏幕，是一本被翻阅了千年的古老手册。  
每一个页面都像一张从神庙地下室挖出的羊皮纸——有岁月的质感，有手写的温度，有符文的神秘，但内容是清晰可读的，不压迫，不炫技。

### 与参考图的对应关系

| 参考图 | 提取的设计语言 |
|--------|--------------|
| 图1·赫卡忒图解 | 手绘线框分栏、关键词竖列、装饰性角花、黑白灰 + 金色点缀 |
| 图2·奥林匹斯宫殿 | 奶油米黄底色、古典卡片标注框、中英文混排、建筑感纵深 |
| 图3·Witch Test | 大量留白、手写感字体、月相符文装饰、极简排版、规则说明感 |

---

## 二、色彩系统

### 主色板

```
背景主色    --bg-primary:    #F5F0E8    /* 羊皮纸奶油白 */
背景次色    --bg-secondary:  #EDE6D6    /* 微黄，用于卡片底色 */
背景深色    --bg-deep:       #2C1F0E    /* 深棕，用于页脚/强调区域 */

文字主色    --text-primary:  #2C1F0E    /* 深棕黑，主体文字 */
文字次色    --text-secondary:#6B5744    /* 中棕，次要说明文字 */
文字浅色    --text-muted:    #A89880    /* 浅棕灰，辅助标注 */

金色主色    --gold:          #B8860B    /* 深金，标题/强调 */
金色亮色    --gold-light:    #D4A843    /* 亮金，悬停/激活 */
金色暗色    --gold-dark:     #7A5C1E    /* 暗金，线框/分割线 */

描边主色    --border:        #C4A882    /* 米色描边，卡片/线框 */
描边深色    --border-dark:   #8B6E4E    /* 深米色，强调描边 */
```

### 功能色

```
成功/完成   #5C7A4E    /* 橄榄绿，符合古典感 */
警告/提示   #B8860B    /* 复用金色 */
错误/取消   #8B3A3A    /* 暗砖红 */
```

### 色彩使用规则

- **背景**：永远用羊皮纸色系，禁止纯白 `#FFFFFF` 和纯黑 `#000000`
- **文字**：主体文字用深棕 `#2C1F0E`，不用纯黑
- **强调**：只有金色才能做强调色，不引入其他彩色
- **卡片**：白色卡片加 `#F5F0E8` 底色 + `#C4A882` 描边，不用圆角或阴影
- **暗区域**：深棕 `#2C1F0E` 底色配奶油色文字，用于页眉/特殊区块

### 背景纹理

用 CSS 模拟羊皮纸质感（不依赖图片）：

```css
body {
  background-color: #F5F0E8;
  background-image:
    url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='4' height='4'%3E%3Crect width='4' height='4' fill='%23F5F0E8'/%3E%3Ccircle cx='1' cy='1' r='.4' fill='%23E8DCC8' opacity='.5'/%3E%3Ccircle cx='3' cy='3' r='.3' fill='%23DDD0B8' opacity='.3'/%3E%3C/svg%3E");
}
```

---

## 三、字体系统

### 字体层级

| 层级 | 字体 | 用途 | 示例 |
|------|------|------|------|
| Display | Cinzel Decorative (英) + 自定义手写中文 | 产品标题、神祇名大标题 | 神话人格 / ZEUS |
| Heading | Cinzel (英) + 宋体/思源宋体 (中) | 页面标题、章节标题 | 你的神话人格 |
| Body | Georgia (英) + 思源宋体/楷体 (中) | 正文段落、描述 | 性格解读段落 |
| Caption | Cinzel (英) + 系统黑体 (中) | 标签、注释、数据标注 | 权威 85% |
| Mono | 等宽字体 | ID编号 | #A7F3K2 |

### Google Fonts 引入

```html
<link href="https://fonts.googleapis.com/css2?
  family=Cinzel:wght@400;600;700;900&
  family=Cinzel+Decorative:wght@400;700&
  family=Noto+Serif+SC:wght@300;400;500;700&
  display=swap" rel="stylesheet">
```

### 字体规则

```css
/* CSS 变量 */
--font-display:  'Cinzel Decorative', 'Cinzel', serif;
--font-heading:  'Cinzel', 'Noto Serif SC', serif;
--font-body:     'Noto Serif SC', 'Georgia', '宋体', serif;
--font-caption:  'Cinzel', 'Noto Serif SC', sans-serif;
```

### 字号比例（基于 16px 根）

```
--text-xs:   0.65rem   /* 10.4px — 极小标注、ID */
--text-sm:   0.75rem   /* 12px   — 说明文字、标签 */
--text-base: 0.9rem    /* 14.4px — 正文 */
--text-md:   1rem      /* 16px   — 正文大号 */
--text-lg:   1.25rem   /* 20px   — 小标题 */
--text-xl:   1.6rem    /* 25.6px — 中标题 */
--text-2xl:  2.2rem    /* 35.2px — 大标题 */
--text-3xl:  3rem      /* 48px   — 神祇名展示标题 */
--text-4xl:  clamp(2.8rem, 10vw, 4.5rem)  /* 响应式超大标题 */
```

### 字间距规则

```
标题（Cinzel）:     letter-spacing: 0.12em ~ 0.25em
英文副标题:         letter-spacing: 0.35em ~ 0.5em
正文（中文）:       letter-spacing: 0.05em
标签/注释:          letter-spacing: 0.1em ~ 0.2em
```

### 行高规则

```
标题:    line-height: 1.2
正文:    line-height: 2.0    /* 中文正文必须 2.0，给呼吸感 */
说明:    line-height: 1.75
标签:    line-height: 1.4
```

---

## 四、间距系统

基于 4px 基准网格：

```
--space-1:  4px
--space-2:  8px
--space-3:  12px
--space-4:  16px
--space-5:  20px
--space-6:  24px
--space-8:  32px
--space-10: 40px
--space-12: 48px
--space-16: 64px
--space-20: 80px
```

### 留白哲学
参考图3（Witch Test）：**留白是设计的一部分，不是空浪费**。  
- 页面上下边距 ≥ 32px  
- 卡片内边距 ≥ 24px  
- 段落间距 ≥ 20px  
- 不要把元素堆满，要让内容「呼吸」

---

## 五、装饰元素系统

这是本设计最有辨识度的部分，从三张参考图提炼。

### 5.1 分割线

**标准装饰分割线**（参考图1的横向装饰线）：

```
────────── ✦ ──────────

⊱ ────────── ⊰

· · · ◆ · · ·

─────── ☽ ───────
```

CSS 实现：
```css
.divider {
  display: flex;
  align-items: center;
  gap: 12px;
  margin: 20px 0;
  color: var(--gold-dark);
  font-size: 0.7rem;
  letter-spacing: 0.3em;
}
.divider::before,
.divider::after {
  content: '';
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--border-dark), transparent);
}
```

### 5.2 角花装饰（Corner Ornament）

参考图1和图2的边角装饰，用 SVG 或 CSS 实现：

```css
/* 四角装饰 */
.corner-frame {
  position: relative;
}
.corner-frame::before,
.corner-frame::after {
  content: '✦';
  position: absolute;
  font-size: 0.6rem;
  color: var(--gold);
  opacity: 0.6;
}
.corner-frame::before { top: 8px; left: 8px; }
.corner-frame::after  { bottom: 8px; right: 8px; }
```

更完整的四角方块（CSS border 实现）：
```css
.ornament-box {
  position: relative;
  border: 1px solid var(--border);
  padding: 24px;
}
.ornament-box::before {
  content: '';
  position: absolute;
  top: -3px; left: -3px; right: -3px; bottom: -3px;
  border: 1px solid var(--border);
  opacity: 0.4;
  pointer-events: none;
}
```

### 5.3 符文/图标体系

使用 Unicode 符号模拟手绘风格，不依赖图标库：

| 类型 | 符号 | 用途 |
|------|------|------|
| 星形 | ✦ ✧ ✶ ✷ ✸ | 分割、装饰点缀 |
| 月相 | ☽ ☾ ● ◑ ◐ ◒ | 月亮主题装饰 |
| 方向 | ◆ ◇ ▲ △ ▼ ▽ | 列表前缀 |
| 植物 | ✿ ❀ ❁ ✾ | 柔和装饰 |
| 古典 | ⊕ ⊗ ⊙ ✠ ❖ | 章节标记 |
| 钥匙/权杖 | 🗝 🔱 ⚡ ⚔ | 神祇属性图标 |

### 5.4 线框卡片样式

参考图1的信息分区框：

```css
/* 基础信息卡 */
.info-card {
  background: #F5F0E8;
  border: 1px solid #C4A882;
  padding: 20px 24px;
  position: relative;
}

/* 带标题的章节卡（参考图1左上角"她是谁"样式）*/
.section-card {
  background: #EDE6D6;
  border: 1px solid #8B6E4E;
  padding: 20px 24px;
}
.section-card .card-title {
  font-family: var(--font-heading);
  font-size: var(--text-sm);
  color: var(--gold);
  letter-spacing: 0.2em;
  border-bottom: 1px solid var(--border);
  padding-bottom: 8px;
  margin-bottom: 16px;
}

/* 引用/名言卡 */
.quote-card {
  border-left: 3px solid var(--gold-dark);
  padding: 12px 0 12px 20px;
  font-family: var(--font-body);
  font-style: italic;
  color: var(--text-secondary);
  line-height: 1.9;
}
```

### 5.5 标签 Tag

```css
.tag {
  display: inline-block;
  border: 1px solid var(--gold-dark);
  color: var(--gold);
  padding: 4px 12px;
  font-size: var(--text-xs);
  letter-spacing: 0.15em;
  font-family: var(--font-caption);
  background: transparent;
}
/* 实心标签 */
.tag-filled {
  background: var(--gold-dark);
  color: #F5F0E8;
}
```

---

## 六、组件规范

### 6.1 按钮

```css
/* 主按钮 — 参考图3的简洁风格 */
.btn-primary {
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  background: transparent;
  border: 1px solid var(--gold-dark);
  color: var(--gold);
  padding: 14px 40px;
  font-family: var(--font-heading);
  font-size: var(--text-base);
  letter-spacing: 0.2em;
  cursor: pointer;
  transition: all 0.25s;
  position: relative;
}
.btn-primary::before,
.btn-primary::after {
  content: '✦';
  position: absolute;
  font-size: 0.5rem;
  color: var(--gold);
  opacity: 0;
  transition: opacity 0.25s;
}
.btn-primary::before { left: 12px; }
.btn-primary::after  { right: 12px; }
.btn-primary:hover {
  background: rgba(184,134,11,0.08);
  color: var(--gold-light);
}
.btn-primary:hover::before,
.btn-primary:hover::after { opacity: 1; }

/* 次要按钮 */
.btn-secondary {
  background: transparent;
  border: none;
  border-bottom: 1px solid var(--border);
  color: var(--text-muted);
  padding: 8px 0;
  font-family: var(--font-caption);
  font-size: var(--text-sm);
  letter-spacing: 0.15em;
  cursor: pointer;
  transition: color 0.2s, border-color 0.2s;
}
.btn-secondary:hover {
  color: var(--text-primary);
  border-color: var(--gold-dark);
}
```

### 6.2 进度条

```css
/* 参考图3的极简线性风格 */
.progress-wrap {
  width: 100%;
}
.progress-label {
  display: flex;
  justify-content: space-between;
  font-size: var(--text-xs);
  letter-spacing: 0.15em;
  color: var(--text-muted);
  margin-bottom: 6px;
  font-family: var(--font-caption);
}
.progress-track {
  height: 1px;   /* 极细线，不是粗条 */
  background: var(--border);
  position: relative;
}
.progress-fill {
  height: 100%;
  background: var(--gold);
  transition: width 0.6s ease;
}
/* 节点圆点 */
.progress-dot {
  position: absolute;
  right: 0; top: 50%;
  transform: translate(50%, -50%);
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--gold);
  border: 1px solid var(--bg-primary);
}
```

### 6.3 选项按钮（测试题）

```css
/* 参考图1的信息格子风格 */
.option-btn {
  width: 100%;
  text-align: left;
  background: transparent;
  border: 1px solid var(--border);
  padding: 14px 20px 14px 36px;
  font-family: var(--font-body);
  font-size: var(--text-base);
  line-height: 1.7;
  color: var(--text-primary);
  cursor: pointer;
  position: relative;
  transition: all 0.2s;
}
/* 左侧序号圆点 */
.option-btn::before {
  content: attr(data-index);
  position: absolute;
  left: 14px; top: 50%;
  transform: translateY(-50%);
  font-size: var(--text-xs);
  font-family: var(--font-caption);
  color: var(--text-muted);
  letter-spacing: 0;
}
.option-btn:hover {
  border-color: var(--gold-dark);
  background: rgba(184,134,11,0.05);
  color: var(--gold);
}
.option-btn:hover::before { color: var(--gold); }
.option-btn.selected {
  border-color: var(--gold);
  background: rgba(184,134,11,0.08);
  color: var(--gold);
}
```

### 6.4 数据条形图（6维人格）

```css
/* 参考图1的数据呈现方式，极简线性 */
.stat-row {
  display: grid;
  grid-template-columns: 60px 1fr 36px;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
.stat-label {
  font-size: var(--text-xs);
  letter-spacing: 0.1em;
  color: var(--text-secondary);
  font-family: var(--font-caption);
  text-align: right;
}
.stat-track {
  height: 1px;  /* 极细 */
  background: var(--border);
  position: relative;
}
.stat-bar {
  position: absolute;
  top: 0; left: 0;
  height: 100%;
  background: var(--gold-dark);
  transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}
/* 终点圆点 */
.stat-bar::after {
  content: '';
  position: absolute;
  right: -3px; top: 50%;
  transform: translateY(-50%);
  width: 5px; height: 5px;
  border-radius: 50%;
  background: var(--gold);
}
.stat-value {
  font-size: var(--text-xs);
  color: var(--gold);
  font-family: var(--font-caption);
  letter-spacing: 0;
}
```

### 6.5 输入框

```css
/* 参考图3的极简风格 */
.input-field {
  width: 100%;
  background: transparent;
  border: none;
  border-bottom: 1px solid var(--border-dark);
  padding: 10px 0;
  font-family: var(--font-body);
  font-size: var(--text-md);
  color: var(--text-primary);
  outline: none;
  transition: border-color 0.2s;
}
.input-field::placeholder { color: var(--text-muted); }
.input-field:focus { border-color: var(--gold); }

/* 输入框标签 */
.input-label {
  display: block;
  font-size: var(--text-xs);
  letter-spacing: 0.2em;
  color: var(--text-muted);
  font-family: var(--font-caption);
  margin-bottom: 8px;
}
```

### 6.6 神祇头像选择器

```css
/* 12个 emoji 头像，点选高亮 */
.avatar-grid {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 8px;
}
.avatar-item {
  aspect-ratio: 1;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.6rem;
  border: 1px solid var(--border);
  cursor: pointer;
  transition: all 0.2s;
  background: transparent;
}
.avatar-item:hover {
  border-color: var(--gold-dark);
  background: rgba(184,134,11,0.05);
}
.avatar-item.active {
  border-color: var(--gold);
  background: rgba(184,134,11,0.1);
}
```

### 6.7 神祇结果卡（核心展示组件）

```css
/* 参考图2的标注卡风格 */
.god-result-card {
  background: #F5F0E8;
  border: 1px solid #8B6E4E;
  padding: 32px 24px;
  position: relative;
}
/* 卡片标题角标 */
.god-result-card .card-badge {
  position: absolute;
  top: -1px; left: 24px;
  background: var(--gold-dark);
  color: #F5F0E8;
  font-size: var(--text-xs);
  letter-spacing: 0.2em;
  padding: 4px 12px;
  font-family: var(--font-caption);
}
/* 神祇图标区 */
.god-icon-display {
  font-size: 4rem;
  text-align: center;
  margin-bottom: 8px;
  filter: sepia(0.2);  /* 给 emoji 加复古感 */
}
/* 神祇名 */
.god-name-display {
  font-family: var(--font-display);
  font-size: var(--text-3xl);
  color: var(--gold);
  text-align: center;
  letter-spacing: 0.15em;
  margin-bottom: 4px;
}
.god-name-en {
  font-family: var(--font-heading);
  font-size: var(--text-xs);
  letter-spacing: 0.5em;
  color: var(--text-muted);
  text-align: center;
  margin-bottom: 8px;
  text-transform: uppercase;
}
.god-role {
  font-size: var(--text-sm);
  color: var(--text-secondary);
  text-align: center;
  letter-spacing: 0.08em;
  font-family: var(--font-body);
}
```

---

## 七、页面布局规范

### 7.1 最大宽度

```
手机端最大内容宽:  540px
平板端最大内容宽:  680px
页面水平边距:     16px (手机) / 24px (平板)
```

### 7.2 页面结构

每个屏幕（Screen）的基本结构：

```
┌─────────────────────────┐
│  顶部装饰线（可选）       │ 2px 金色线
├─────────────────────────┤
│  页眉（可选）             │ 极简，含页面标题
├─────────────────────────┤
│                         │
│  主内容区                │ flex 居中，可滚动
│                         │
├─────────────────────────┤
│  底部操作区              │ 固定在底部
└─────────────────────────┘
```

### 7.3 卡片网格（图鉴页）

```css
.codex-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
}
/* 每张图鉴卡 */
.codex-card {
  border: 1px solid var(--border);
  padding: 16px 12px;
  text-align: center;
  background: #F5F0E8;
  cursor: pointer;
  transition: border-color 0.2s;
}
.codex-card:hover { border-color: var(--gold-dark); }
.codex-card.active { border-color: var(--gold); background: rgba(184,134,11,0.06); }
```

---

## 八、动效规范

### 8.1 动效原则

- **克制**：动效服务于内容，不抢主角
- **仪式感**：重要时刻（进入结果页）可以有更隆重的动效
- **流畅**：easing 使用 `cubic-bezier(0.22, 1, 0.36, 1)`（缓出，有古典书页翻开感）

### 8.2 页面切换

```css
/* 淡入淡出，不做位移 */
.screen { opacity: 0; transition: opacity 0.45s ease; }
.screen.on { opacity: 1; }
```

### 8.3 卡片进场

```css
@keyframes cardIn {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
.card-enter { animation: cardIn 0.5s cubic-bezier(0.22, 1, 0.36, 1); }
```

### 8.4 数据条动画

```css
/* 延迟加载，依次出现 */
.stat-bar { width: 0; transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1); }
/* JS 赋值后触发：el.style.width = value + '%' */
/* 每条延迟 100ms：transitionDelay: i * 100 + 'ms' */
```

### 8.5 加载动效（Loading 页）

```css
/* 月相旋转，参考图3的月相装饰 */
@keyframes moonSpin {
  0%   { content: '🌑'; transform: rotate(0deg); }
  25%  { content: '🌒'; }
  50%  { content: '🌕'; transform: rotate(180deg); }
  75%  { content: '🌘'; }
  100% { content: '🌑'; transform: rotate(360deg); }
}
/* 简单实现：旋转月亮 emoji */
.loading-moon {
  font-size: 3rem;
  display: block;
  animation: rotate 3s ease-in-out infinite;
  filter: sepia(0.3);
}
@keyframes rotate {
  0%,100% { transform: rotate(-15deg) scale(1); }
  50%     { transform: rotate(15deg) scale(1.1); }
}
```

### 8.6 禁止事项

- ❌ 不用 `transform: scale()` 做悬停放大（太现代感）
- ❌ 不用 `box-shadow` 发光效果（改用描边加深）
- ❌ 不用弹性弹跳动效（`spring` 物理效果太轻盈）
- ❌ 不用颜色渐变过渡（保持颜色系统稳定）

---

## 九、图标与装饰资源

### 9.1 12个头像 emoji（供用户选择）

```
🌟 ⚡ 🌙 🔱 🌹 🦉 🍃 🔥 🌊 💫 🗝️ 🌺
```

### 9.2 20位神祇图标

```
⚡ 宙斯      👑 赫拉      🦉 雅典娜    ☀️ 阿波罗
🌙 阿尔忒弥斯  🔱 波塞冬    🌾 得墨忒耳  🪶 赫尔墨斯
🌹 阿芙罗狄忒  ⚔️ 阿瑞斯    🔥 赫淮斯托斯  🍇 狄俄尼索斯
💀 哈迪斯    🌺 珀耳塞福涅  💘 厄洛斯    🏆 尼刻
🎲 堤喀      🔦 普罗米修斯  🛡️ 阿喀琉斯  🌊 奥德修斯
```

### 9.3 装饰符文速查

```
页面标题装饰:   ── ✦ ──
章节分割:       ⊱ ──── ⊰
列表前缀:       ◆  或  ✧
引用标记:       「 」
角花:           ✦ (四角)
月相序列:       🌑 🌒 🌓 🌔 🌕 🌖 🌗 🌘
```

---

## 十、响应式规范

```css
/* 手机优先 */
:root { font-size: 15px; }

/* 375px — 标准手机 */
@media (max-width: 390px) {
  :root { font-size: 14px; }
  .god-name-display { font-size: 2.4rem; }
}

/* 平板 */
@media (min-width: 600px) {
  :root { font-size: 16px; }
  .content-wrap { max-width: 560px; margin: 0 auto; }
}
```

---

## 十一、禁止项清单

| 禁止 | 原因 |
|------|------|
| 纯白背景 `#fff` | 失去羊皮纸质感 |
| 圆角 `border-radius` > 4px | 现代感太强，不符合古典线框风格 |
| `box-shadow` 阴影 | 改用描边加深表达层次 |
| 彩色（非金/棕色系） | 破坏色彩一致性 |
| 无衬线字体做正文 | 降低古典感 |
| 图标库（Font Awesome 等） | 用 Unicode 符号替代 |
| 动画时长 > 600ms（非仪式性） | 影响操作流畅感 |
| 纯黑文字 `#000` | 改用深棕 `#2C1F0E` |
| `border-radius` 在卡片上 | 直角线框才有古典仪式感 |
