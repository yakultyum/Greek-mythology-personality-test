# greek-myth-design — Components

## 1. BUTTONS

### Variants

| Variant | Background | Text | Border | Radius | Style |
|---------|-----------|------|--------|--------|-------|
| Primary | `transparent` | `--accent` (`#B8860B`) | `1px solid #7A5C1E` | 0px | 线框感，hover 时微填充金色 |
| Secondary | `transparent` | `--text3` | `none + border-bottom 1px solid --border` | 0px | 下划线样式 |
| Ghost | `transparent` | `--text2` | none | 0px | 无边框文字按钮 |
| Destructive | `transparent` | `--error` | `1px solid #8B3A3A` | 0px | 砖红线框 |

### Specs

| Property | Value |
|----------|-------|
| Height (large) | 48px |
| Height (small) | 36px |
| Padding (large) | 14px 40px |
| Padding (small) | 8px 24px |
| Font | `"Cinzel"` 400, `--subheading` (14px) |
| Letter-spacing | 0.2em |
| Min touch target | 44px |

### States

| State | Change |
|-------|--------|
| **Hover** | `background: rgba(184,134,11,0.08)` + `border-color` 加深至 `#B8860B` + `color` 变 `--accent-light` |
| **Active / Pressed** | `background: rgba(184,134,11,0.12)` |
| **Disabled** | `opacity: 0.4`，无交互 |
| **Focus** | `outline: 1px solid #B8860B`，`outline-offset: 2px` |

### 角花装饰（Primary 专属）
```css
.btn-primary::before { content: '✦'; position: absolute; left: 12px; opacity: 0; transition: opacity 0.2s; }
.btn-primary::after  { content: '✦'; position: absolute; right: 12px; opacity: 0; transition: opacity 0.2s; }
.btn-primary:hover::before, .btn-primary:hover::after { opacity: 1; color: var(--accent); }
```

---

## 2. CARDS / SURFACES

### Info Card（基础信息卡）
- Background: `--surface1` (`#EDE6D6`)
- Border: `1px solid #C4A882`
- Radius: 0px（直角）
- Padding: 20px 24px
- Shadow: none

### Section Card（章节卡，参考图1「她是谁」样式）
- Background: `--surface1`
- Border: `1px solid #8B6E4E`（深一档）
- Radius: 0px
- Padding: 20px 24px
- 标题区：底部 `border-bottom: 1px solid #C4A882`，标题用 Cinzel 12px 金色

### Quote Card（引用卡）
- Border: none，左侧 `border-left: 3px solid #7A5C1E`
- Padding: 12px 0 12px 20px
- Font: Noto Serif SC 斜体
- Color: `--text2`

### God Result Card（神祇结果卡 — 核心组件）
- Background: `--background` (`#F5F0E8`)
- Border: `1px solid #8B6E4E`
- Radius: 0px
- Padding: 32px 24px
- 顶部角标 `.card-badge`：`background: #7A5C1E`，白文，绝对定位在 `top: -1px, left: 24px`

### Content Layout
- Title: `--subheading`, `--accent`（金色）
- Description: `--body`, `--text1`
- Metadata: `--caption`, `--text3`
- Internal spacing: `--space-sm` (12px)
- Press state: `border-color` 加深至 `--border-visible`

---

## 3. INPUTS

### Text Field（下划线风格）

| Property | Value |
|----------|-------|
| Height | 44px |
| Background | `transparent` |
| Border (default) | `none; border-bottom: 1px solid #8B6E4E` |
| Border (focus) | `border-bottom-color: #B8860B` |
| Border (error) | `border-bottom-color: #8B3A3A` |
| Radius | 0px |
| Padding | 10px 0 |
| Font | `"Noto Serif SC"`, `--body` (14px) |
| Placeholder color | `--text4` (`#A89880`) |

### Label
- Position: 上方，间距 8px
- Font: `"Cinzel"`, `--caption` (10px), `--text3`
- Letter-spacing: 0.2em

### States

| State | Treatment |
|-------|-----------|
| **Default** | `border-bottom: 1px solid #8B6E4E` |
| **Focus** | `border-bottom-color: #B8860B` + `color: --text1` |
| **Error** | `border-bottom-color: #8B3A3A`。错误文字在下方，`--caption`，`--error` 色 |
| **Disabled** | Opacity 0.4，无交互 |

---

## 4. OPTION BUTTONS（测试题选项）

参考图1的信息格子风格，每个选项是独立的线框块。

| Property | Value |
|----------|-------|
| Width | 100% |
| Background | `transparent` |
| Border | `1px solid #C4A882` |
| Padding | 14px 20px 14px 36px |
| Font | `"Noto Serif SC"`, `--body` (14px) |
| Line-height | 1.7 |
| Radius | 0px |
| Margin-bottom | 8px |

### 左侧序号
```css
.option-btn::before {
  content: attr(data-index);   /* A B C D 或 1 2 3 4 */
  position: absolute;
  left: 14px; top: 50%;
  transform: translateY(-50%);
  font-family: 'Cinzel';
  font-size: 10px;
  color: var(--text3);
  letter-spacing: 0;
}
```

### States

| State | Treatment |
|-------|-----------|
| **Default** | `border-color: #C4A882` |
| **Hover** | `border-color: #7A5C1E` + `background: rgba(184,134,11,0.05)` + 序号变金色 |
| **Selected** | `border-color: #B8860B` + `background: rgba(184,134,11,0.08)` + 文字/序号变 `--accent` |
| **Disabled** | Opacity 0.4，无交互 |

---

## 5. PROGRESS BAR（极细线性）

参考 Witch Test 极简风格：1px 高，不是粗条。

| Property | Value |
|----------|-------|
| Track height | 1px |
| Track color | `#C4A882` |
| Fill color | `#B8860B` |
| Radius | 0px |
| Label position | 上方两侧（左：步骤名，右：n/N） |
| Label font | `"Cinzel"`, 10px, `--text3` |
| Transition | `width 0.6s ease` |

### 终点圆点
```css
.progress-dot {
  position: absolute; right: 0; top: 50%;
  transform: translate(50%, -50%);
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--accent);
  border: 1px solid var(--background);
}
```

---

## 6. STAT ROW（6维人格数据条）

参考图1的数据呈现方式，极简线性。

```
标签文字 ──────────────●  85%
```

| Property | Value |
|----------|-------|
| Grid layout | `60px 1fr 36px` |
| Gap | 12px |
| Track height | 1px |
| Track color | `#C4A882` |
| Bar color | `#7A5C1E` |
| Dot color | `#B8860B`，5px 圆形 |
| Label font | `"Cinzel"`, 10px, `--text2`, 右对齐 |
| Value font | `"Cinzel"`, 10px, `--accent` |
| Animation | `width: 0 → N%`, duration 1.2s, `cubic-bezier(0.4,0,0.2,1)`, delay `i*100ms` |

---

## 7. LISTS / DATA ROWS

### Standard Row

| Property | Value |
|----------|-------|
| Min height | 48px |
| Padding | 12px 16px |
| Divider | `border-bottom: 1px solid #C4A882` |
| Label font | `"Noto Serif SC"`, `--body`, `--text1` |
| Value font | `"Cinzel"`, `--caption`, `--text2` |

### Interaction States

| State | Treatment |
|-------|-----------|
| **Default** | `background: transparent` |
| **Pressed** | `background: rgba(184,134,11,0.05)` |
| **Selected** | `border-left: 2px solid #B8860B` + `background: rgba(184,134,11,0.06)` |

---

## 8. NAVIGATION / TAB BAR

### Tab Bar（底部导航）

| Property | Value |
|----------|-------|
| Height | 56px + safe area |
| Background | `--background` |
| Border | `border-top: 1px solid #C4A882` |
| Font | `"Cinzel"`, `--caption` (10px) |

### Tab States

| State | Treatment |
|-------|-----------|
| **Active** | `color: --accent`，标签文字金色 |
| **Inactive** | `color: --text3` |
| **Hover** | `color: --text2` |

### Navigation Bar（顶部导航）
- Title: `--subheading`, `--text1`, Cinzel, letter-spacing 0.2em
- Border: `border-bottom: 1px solid #C4A882`
- Background: `--background`

---

## 9. TAGS / CHIPS

| Property | Value |
|----------|-------|
| Height | 24px |
| Padding | 4px 12px |
| Radius | 0px（直角方形标签） |
| Font | `"Cinzel"`, `--caption` (10px), 400 |
| Letter-spacing | 0.15em |
| Background | `transparent` |
| Text color | `--accent` (`#B8860B`) |
| Border | `1px solid #7A5C1E` |

### Filled Variant
- Background: `#7A5C1E`
- Text: `#F5F0E8`
- Border: none

### Selected State
- Background: `--accent-subtle` (`#FDF8EC`)
- Text: `--accent`
- Border: `1px solid #B8860B`

---

## 10. DIVIDERS（装饰分割线）

本设计语言最有辨识度的元素之一。

### Ornamental Divider（标准装饰分割线）
```html
<div class="divider">✦</div>
<!-- 或 -->
<div class="divider">⊱ ── ⊰</div>
<!-- 或 -->
<div class="divider">☽</div>
```

```css
.divider {
  display: flex; align-items: center; gap: 12px;
  margin: 20px 0;
  color: var(--border-visible);
  font-size: 0.7rem;
  letter-spacing: 0.3em;
}
.divider::before, .divider::after {
  content: '';
  flex: 1; height: 1px;
  background: linear-gradient(90deg, transparent, var(--border-visible), transparent);
}
```

### Variants
- `────────── ✦ ──────────` — 通用分割
- `⊱ ────────── ⊰` — 章节内分割（更优雅）
- `· · · ◆ · · ·` — 轻量段落间分割
- `─────── ☽ ───────` — 月亮主题页专用

---

## 11. CORNER ORNAMENT（角花装饰）

```css
/* 双重边框角花效果 */
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

/* ✦ 角花点 */
.corner-ornament::before { content: '✦'; position: absolute; top: 6px; left: 8px; font-size: 0.6rem; color: var(--accent); opacity: 0.6; }
.corner-ornament::after  { content: '✦'; position: absolute; bottom: 6px; right: 8px; font-size: 0.6rem; color: var(--accent); opacity: 0.6; }
```

---

## 12. OVERLAYS

### Modal / Dialog

| Property | Value |
|----------|-------|
| Background | `--surface1` |
| Radius | 2px（极微，几乎直角） |
| Border | `1px solid #8B6E4E` |
| Shadow | none（flat 策略） |
| Backdrop | `rgba(44,31,14,0.5)` |
| Max width | 480px |
| Padding | 32px 24px |
| Close button | `✦` 或 `×`，右上角，`--text3` 色 |

### Bottom Sheet（底部弹层）

| Property | Value |
|----------|-------|
| Background | `--surface1` |
| Top radius | 2px |
| Handle | 4px × 32px 线条，`--border-visible` 色，居中 |
| Backdrop | `rgba(44,31,14,0.5)` |
| Border-top | `1px solid #8B6E4E` |

---

## 13. STATE PATTERNS

### Empty State
- Layout: 居中，`padding-top: 64px`
- 图标/符号: 大型 Unicode 符号（如 `☽` 或神祇 Emoji），`font-size: 3rem`，`filter: sepia(0.2)`
- Headline: `--subheading`, `--text2`, Cinzel
- Description: `--body`, `--text3`, max 2 行
- CTA: primary button，距描述 24px

### Loading（月相旋转）
```css
.loading-moon { font-size: 3rem; animation: moonPulse 3s ease-in-out infinite; filter: sepia(0.3); }
@keyframes moonPulse {
  0%, 100% { transform: rotate(-15deg) scale(1); }
  50%       { transform: rotate(15deg) scale(1.1); }
}
```
- Inline: 旋转 `◐` 或 `🌕` 符号
- Full screen: 居中月相动画 + Cinzel 标题

### Error
- Inline (field): `--error` 文字，`--caption`，field 下方 4px 处
- Screen-level: 砖红 `#8B3A3A` 线框卡片，左侧 `border-left: 3px solid #8B3A3A`
- Tone: 古典克制（"发生了错误"，不用感叹号和 emoji）

### Disabled
- Opacity 0.4，无交互，保持布局
- Border 变为 `--border`（较浅）
- 无 hover/focus 状态

---

## 14. AVATAR（神祇头像选择器）

参考设计规范 6.6 节。12个 Emoji 头像，点选高亮。

```css
.avatar-grid { display: grid; grid-template-columns: repeat(6, 1fr); gap: 8px; }
.avatar-item {
  aspect-ratio: 1;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.6rem;
  border: 1px solid var(--border);
  cursor: pointer;
  transition: all 0.2s;
  background: transparent;
  filter: sepia(0.15);
}
.avatar-item:hover { border-color: var(--border-visible); background: rgba(184,134,11,0.05); }
.avatar-item.active { border-color: var(--accent); background: rgba(184,134,11,0.1); filter: none; }
```

### 可选头像
```
🌟 ⚡ 🌙 🔱 🌹 🦉 🍃 🔥 🌊 💫 🗝️ 🌺
```

---

## 15. CODEX GRID（图鉴卡片网格）

```css
.codex-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; }
.codex-card {
  border: 1px solid var(--border);
  padding: 16px 12px;
  text-align: center;
  background: var(--surface1);
  cursor: pointer;
  transition: border-color 0.2s;
}
.codex-card:hover { border-color: var(--border-visible); }
.codex-card.active { border-color: var(--accent); background: var(--accent-subtle); }
```
