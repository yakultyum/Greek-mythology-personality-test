# 神话人格 · 设计规范文档 DESIGN SYSTEM

> 版本 v2.0 · 2026-06-12  
> 风格定义：**深色炭黑 × 羊皮纸 × AI 油画神祇 × 金色古典线框**  
> 参考来源：ui-design/01~05.jpg + ui-destiny-bond.jpg

---

## 一、设计理念

### 核心关键词
**神秘的** · **史诗感** · **仪式感** · **油画质感** · **金色点亮黑暗**

### 风格定位
两种质感并存、互相呼应：
- **深色炭黑**（`#1A1510`）：题目页、图鉴详情、命运羁绊 — 如神庙地下室的石壁
- **羊皮纸奶油**（`#F0E8D5`）：介绍页、设置页、结果页内容区 — 如从神庙挖出的古卷

核心法则：**金色是唯一的彩色**，在任何背景上都只用金/棕色系，用 AI 油画图片承载色彩张力。

### 各页面风格对应

| 页面 | 主背景 | 氛围 |
|------|--------|------|
| 介绍页 | 羊皮纸 + 神祇大图水印 | 古卷封面，庄重 |
| 设置页 | 羊皮纸 + 廊柱装饰 | 神庙前厅，仪式感 |
| 题目页 | 深炭黑 + AI 场景图 | 神谕时刻，神秘 |
| 结果页 | 神祇油画 → 渐变羊皮纸 | 史诗揭晓 |
| 好友页 | 羊皮纸 + 双神祇对比 | 命运交汇 |

---

## 二、色彩系统

### 主色板（CSS 变量）

```css
:root {
  /* 羊皮纸系 */
  --parchment:   #F0E8D5;
  --parchment2:  #E8DCC0;
  --parchment3:  #DDD0A8;

  /* 深色系 */
  --charcoal:    #1A1510;
  --charcoal2:   #241C10;
  --deep-brown:  #2C1F0E;
  --mid-brown:   #6B5744;
  --muted:       #A89070;

  /* 金色系（唯一彩色） */
  --gold:        #B8860B;
  --gold-lt:     #D4A843;
  --gold-dk:     #7A5C1E;

  /* 描边系 */
  --border:      #C4A070;
  --border-dk:   #8B6040;

  /* 字体 */
  --font-d: 'Cinzel Decorative','Cinzel',Georgia,serif;
  --font-h: 'Cinzel',Georgia,serif;
  --font-b: 'Noto Serif SC','Georgia','宋体',serif;
}
```

### 色彩使用规则

- **深色背景页**：`--charcoal` 底，文字用 `--parchment` 和 `--gold`
- **羊皮纸页**：`--parchment` 底，文字用 `--deep-brown` 和 `--gold`
- **强调色**：只用金色，禁止引入蓝/红/绿等彩色
- **禁止**：纯白 `#fff`、纯黑 `#000`、`border-radius > 2px`、`box-shadow`

---

## 三、字体系统

### 字体层级

| 层级 | 字体 | 用途 |
|------|------|------|
| Display | Cinzel Decorative | 产品主标题「神话人格」、神祇大名 |
| Heading | Cinzel | 英文副标题、按钮、标签、章节标题 |
| Body | Noto Serif SC | 中文正文、性格解读、选项文字 |

### 字号规则

```
神祇名大标题:   clamp(2.8rem, 10vw, 4rem)  letter-spacing: 0.2em
页面主标题:     1.8rem ~ 2.2rem             letter-spacing: 0.1em
章节标题:       0.75rem                     letter-spacing: 0.25em  全大写
正文:           0.87rem ~ 0.92rem           line-height: 2.0
标签/标注:      0.72rem ~ 0.8rem            letter-spacing: 0.15em
极小标注:       0.62rem ~ 0.68rem           letter-spacing: 0.2em
```

### 字间距规则

```
Cinzel 标题:      letter-spacing: 0.12em ~ 0.25em
英文全大写副标题:  letter-spacing: 0.35em ~ 0.5em
中文正文:         letter-spacing: 0.03em ~ 0.05em
标签:             letter-spacing: 0.1em ~ 0.2em
```

---

## 四、间距系统

基于 4px 网格，移动端用 vw 单位保持比例：

```
页面水平边距:   5.3vw（约 20px）
章节间距:       6.4vw（约 24px）
卡片内边距:     4vw ~ 5.3vw
元素间距:       3.2vw（约 12px）
```

---

## 五、装饰元素系统

### 5.1 分割线（三种规格）

```
标准金色分割线:    ──────── ✦ ────────
细金线（纯线）:    1px solid rgba(184,134,11,.3)
章节标题分割:      ◇ ─── 命运之问 ─── ◇
```

CSS：
```css
.divider {
  display: flex; align-items: center; gap: 12px;
  color: var(--gold-dk); font-size: .65rem; letter-spacing: .3em;
  margin: 5.3vw 0;
}
.divider::before, .divider::after {
  content: ''; flex: 1; height: 1px;
  background: linear-gradient(90deg, transparent, var(--border-dk), transparent);
}
```

### 5.2 卡片角标装饰

题目卡片和结果卡片四角有金色小方角：
```css
.corner-frame::before { content: ''; position: absolute; top: 8px; left: 8px;
  width: 12px; height: 12px;
  border-top: 1px solid var(--gold-dk); border-left: 1px solid var(--gold-dk); }
.corner-frame::after  { content: ''; position: absolute; bottom: 8px; right: 8px;
  width: 12px; height: 12px;
  border-bottom: 1px solid var(--gold-dk); border-right: 1px solid var(--gold-dk); }
```

### 5.3 符文速查

```
页面顶部菱形:   ◆
分割装饰:       ✦  ◇  ◈
引号:           「 」
章节装饰:       ☽  ✦  ✧
角花:           四角 L 形线框
底部标注:       · · ·  20 DEITIES · 190 RELATIONSHIPS  · · ·
```

### 5.4 图腾图标（设置页 12 个）

从 UI 设计图提炼，使用 AI 生成的真实图标图片（存于 `assets/totems/`）：
- 猫头鹰、狼、狮子、橄榄枝、海豚、三叉戟
- 凤凰、蛇、鹿、橄榄、雄鹰、独角兽

### 5.5 维度图标（结果页 6 个）

使用 AI 生成的小图标（存于 `assets/icons/`）：
权威⚡ 智慧🦉 激情🔥 守护🛡 公正⚖ 独立🌙

---

## 六、组件规范

### 6.1 主按钮（深色背景版）

```css
.btn-main {
  width: 100%;
  background: transparent;
  border: 1px solid var(--gold-dk);
  color: var(--gold);
  padding: 4vw 5.3vw;
  font-family: var(--font-h);
  font-size: .82rem;
  letter-spacing: .12em;
  cursor: pointer;
  transition: background .2s;
  position: relative;
}
/* 四角装饰 */
.btn-main::before, .btn-main::after { /* corner-frame 同上 */ }
.btn-main:active { background: rgba(184,134,11,.15); }
```

### 6.2 选项按钮（题目页）

深色底，左侧字母标注 A/B/C/D，选中时金色边框：
```css
.opt-btn {
  width: 100%; text-align: left;
  background: rgba(26,21,16,.88);
  border: 1px solid rgba(139,96,64,.45);
  color: var(--parchment);
  padding: 3.5vw 4vw 3.5vw 11vw;
  font-family: var(--font-b); font-size: .87rem; line-height: 1.65;
  position: relative; cursor: pointer;
  transition: background .18s, border-color .18s;
}
/* 字母标注 */
.opt-btn::before {
  content: attr(data-k);
  position: absolute; left: 4vw; top: 50%; transform: translateY(-50%);
  font-family: var(--font-h); font-size: .75rem; color: var(--gold-dk);
}
.opt-btn.sel { border-color: var(--gold); background: rgba(122,92,30,.35); }
/* 选中右侧指南针图标 */
.opt-btn.sel::after {
  content: '◈'; position: absolute; right: 4vw; top: 50%;
  transform: translateY(-50%);
  font-size: .85rem; color: var(--gold);
}
```

### 6.3 命运羁绊卡片（新增）

参考 ui-destiny-bond.jpg：
```css
.bond-card {
  display: flex; align-items: center; gap: 3.2vw;
  padding: 3.2vw 4vw;
  border: 1px solid rgba(184,134,11,.3);
  background: rgba(26,21,16,.5);
}
/* 相契版：金色边框微发光 */
.bond-card.kindred { border-color: rgba(212,168,67,.5); }
/* 张力版：暗边框 */
.bond-card.tension { border-color: rgba(139,96,64,.3); }

.bond-avatar {
  width: 12vw; height: 12vw; max-width: 48px; max-height: 48px;
  border-radius: 50%;
  border: 1px solid var(--gold-dk);
  object-fit: cover; flex-shrink: 0;
}
.bond-name { font-family: var(--font-h); font-size: .78rem; color: var(--gold); }
.bond-desc { font-family: var(--font-b); font-size: .72rem; color: var(--muted); line-height: 1.5; }
```

### 6.4 好友对比卡片（新增）

参考 05-friend.jpg，两列对比布局：
```css
.friend-grid {
  display: grid; grid-template-columns: 1fr auto 1fr; gap: 3.2vw;
  align-items: start;
}
.friend-card {
  border: 1px solid var(--border-dk);
  background: var(--parchment2);
  overflow: hidden;
}
.friend-card img {
  width: 100%; aspect-ratio: 3/4; object-fit: cover; object-position: top;
}
.friend-vs {
  font-family: var(--font-h); font-size: 1.1rem; color: var(--gold);
  align-self: center; text-align: center;
}
```

### 6.5 进度条（题目页顶部）

```css
.quiz-progress { height: 1px; background: rgba(184,134,11,.2); }
.quiz-progress-fill { height: 100%; background: var(--gold); transition: width .6s; }
```

### 6.6 统计条形图

```css
.stat-row {
  display: grid; grid-template-columns: 5.3vw 1fr 10vw;
  align-items: center; gap: 2.7vw; margin-bottom: 3.2vw;
}
.stat-icon { font-size: 1rem; text-align: center; }
.stat-track { height: 1px; background: rgba(184,134,11,.2); position: relative; }
.stat-bar {
  position: absolute; top: 0; left: 0; height: 100%;
  background: var(--gold); transition: width 1.2s cubic-bezier(.4,0,.2,1);
}
.stat-bar::after {
  content: ''; position: absolute; right: -3px; top: 50%; transform: translateY(-50%);
  width: 5px; height: 5px; border-radius: 50%; background: var(--gold-lt);
}
.stat-val { font-family: var(--font-h); font-size: .72rem; color: var(--gold); text-align: right; }
```

---

## 七、图片资源规范

### 7.1 神祇图片（images/）

- 尺寸：800×800px（正方形，压缩后约 100-160KB）
- 格式：JPEG，quality 75
- 用途：结果页大图（3:4 裁切，`object-position: top center`）、好友对比页
- 命名：`zeus.jpg` / `hera.jpg` / ...

### 7.2 题目场景图（assets/scene-*.jpg）

- 尺寸：1200×900px，压缩后约 250-450KB
- 格式：JPEG，quality 75
- `object-position: center top`（避免人物头部被裁切）

### 7.3 图腾图标（assets/totems/）

- 尺寸：200×200px，约 20-40KB
- 格式：JPEG，深色背景，金色/棕色图案
- 12个：owl / wolf / lion / olive / dolphin / trident / phoenix / snake / deer / eagle / unicorn / branch

### 7.4 背景素材（assets/）

| 文件 | 用途 | 尺寸建议 |
|------|------|---------|
| parchment-texture.jpg | 羊皮纸底色纹理叠加 | 1200px，multiply混合 |
| ink-border.jpg | 全局炭笔毛边框 | 全屏，fixed定位 |
| ornament-band.jpg | 结果页底部卷草纹 | 宽1200px |
| pillar-left/right.jpg | 设置页两侧廊柱 | 高800px，半透明遮罩 |
| quiz-bg.jpg | 题目页深色背景 | 1200px |

---

## 八、性能规范（新增）

### 8.1 预加载策略

```
首屏必要（立即加载）:
  - parchment-texture.jpg（介绍页背景）
  - ink-border.jpg（全局叠加层）
  - quiz-bg.jpg（题目页背景）

按需加载（进入对应页面时才加载）:
  - 神祇图片 images/*.jpg — 结果页渲染时加载
  - 场景图 assets/scene-*.jpg — 题目切换时加载当前题

预取（用户答题过程中后台加载）:
  - 所有场景图用 IntersectionObserver 或题目切换时 prefetch
```

### 8.2 图片加载技巧

```js
// 预加载下一张场景图（在当前题展示时后台加载下一题图片）
function prefetchNext(idx) {
  if (Q_SCENES[idx]) {
    var img = new Image();
    img.src = Q_SCENES[idx];
  }
}

// 神祇图片 — 先显示 emoji 占位，图片加载完再替换
function loadImg(imgEl, emojiEl, card, gid) {
  card.classList.add('no-img'); // 先显示 emoji
  var t = new Image();
  t.onload = function() {
    imgEl.src = t.src;
    card.classList.remove('no-img');
  };
  t.src = GOD_IMGS[gid];
}
```

### 8.3 字体加载

使用 `font-display: swap` 避免 FOIT（不可见文字闪烁）：
```html
<link rel="preload" href="cinzel-400.woff2" as="font" crossorigin>
```

---

## 九、动效规范

### 9.1 动效原则

- **克制**：动效服务内容，不抢主角
- **仪式感**：结果页揭晓、命运羁绊展开可以有隆重动效
- **easing**: `cubic-bezier(0.22, 1, 0.36, 1)`（缓出，古典书页翻开感）

### 9.2 标准时长

```
页面切换:       opacity 0.45s
卡片进场:       0.5s translateY(20px → 0)
数据条填充:     1.2s，各条 delay 100ms
按钮反馈:       0.2s background
图片加载淡入:   0.3s opacity
```

### 9.3 禁止事项

- ❌ `transform: scale()` 悬停放大（太现代）
- ❌ `box-shadow` 发光（改用描边加深）
- ❌ 弹性弹跳（`spring` 物理效果太轻盈）
- ❌ 彩色渐变 background（保持色彩系统稳定）
- ❌ 动画时长 > 600ms（非仪式性场景）

---

## 十、禁止项清单

| 禁止 | 原因 |
|------|------|
| 纯白背景 `#fff` | 失去羊皮纸/古典质感 |
| 纯黑文字 `#000` | 改用深棕 `#2C1F0E` 或羊皮纸 `#F0E8D5` |
| `border-radius > 2px` | 现代感，破坏直角线框风格 |
| `box-shadow` 阴影 | 改用描边加深表达层次 |
| 非金/棕色系彩色 | 破坏色彩一致性 |
| 无衬线字体做正文 | 降低古典感 |
| 图标库（Font Awesome 等）| 用 Unicode 符号或 AI 生成图片替代 |
| 动画时长 > 600ms（非仪式性）| 影响操作流畅感 |
