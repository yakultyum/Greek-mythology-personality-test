# greek-myth-design — Platform Mapping

## FONT LOADING (Required — Always First)

### Google Fonts

```html
<!-- 放在 <head> 最前面，所有样式之前 -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Cinzel+Decorative:wght@400;700&family=Noto+Serif+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
```

### CSS Custom Properties (`:root` 完整声明)

```css
/* greek-myth-design — CSS Custom Properties */
/* ============================================ */

:root {
  /* === PRIMITIVES: Neutral (Warm Parchment) === */
  --neutral-50:  #FAF6EE;
  --neutral-100: #F5F0E8;
  --neutral-150: #EDE6D6;
  --neutral-200: #E0D5BF;
  --neutral-300: #C4A882;
  --neutral-400: #A89880;
  --neutral-500: #8B6E4E;
  --neutral-600: #6B5744;
  --neutral-700: #4A3828;
  --neutral-800: #3A2818;
  --neutral-900: #2C1F0E;
  --neutral-950: #1A1008;

  /* === PRIMITIVES: Brand (Deep Gold) === */
  --brand-50:  #FDF8EC;
  --brand-100: #FAF0D0;
  --brand-200: #F0D88A;
  --brand-300: #D4A843;
  --brand-400: #C49020;
  --brand-500: #B8860B;
  --brand-600: #9A6F08;
  --brand-700: #7A5C1E;
  --brand-800: #5C4216;
  --brand-900: #3D2C0A;
  --brand-950: #1E1505;

  /* === PRIMITIVES: Status === */
  --red-50:    #F9EDED;
  --red-500:   #8B3A3A;
  --red-900:   #4A1A1A;
  --green-50:  #EFF4EB;
  --green-500: #5C7A4E;
  --green-900: #2A3C22;
  --amber-50:  #FDF8EC;
  --amber-500: #B8860B;
  --amber-900: #3D2C0A;

  /* === SEMANTIC: Light Mode (Primary) === */
  --background:      var(--neutral-100);   /* #F5F0E8 */
  --bg:              var(--background);    /* alias */
  --surface1:        var(--neutral-150);   /* #EDE6D6 */
  --surface2:        var(--neutral-200);   /* #E0D5BF */
  --surface3:        var(--neutral-300);   /* #C4A882 */
  --border:          var(--neutral-300);   /* #C4A882 */
  --border-visible:  var(--neutral-500);   /* #8B6E4E */
  --text1:           var(--neutral-900);   /* #2C1F0E */
  --text2:           var(--neutral-600);   /* #6B5744 */
  --text3:           var(--neutral-500);   /* #8B6E4E */
  --text4:           var(--neutral-400);   /* #A89880 */
  --accent:          var(--brand-500);     /* #B8860B */
  --accent-subtle:   var(--brand-50);      /* #FDF8EC */
  --success:         var(--green-500);     /* #5C7A4E */
  --warning:         var(--amber-500);     /* #B8860B */
  --error:           var(--red-500);       /* #8B3A3A */
  --success-bg:      var(--green-50);      /* #EFF4EB */
  --warning-bg:      var(--amber-50);      /* #FDF8EC */
  --error-bg:        var(--red-50);        /* #F9EDED */

  /* === TYPOGRAPHY === */
  --font-display:  'Cinzel Decorative', 'Cinzel', 'Georgia', serif;
  --font-heading:  'Cinzel', 'Georgia', 'Times New Roman', serif;
  --font-body:     'Noto Serif SC', 'Georgia', '宋体', 'SimSun', serif;
  --font-caption:  'Cinzel', 'Noto Serif SC', serif;
  --font-mono:     'Courier New', 'Courier', monospace;

  /* Type Scale */
  --text-display:    clamp(2.8rem, 10vw, 4.5rem);
  --text-heading:    20px;
  --text-subheading: 14px;
  --text-body:       14px;
  --text-body-sm:    12px;
  --text-caption:    10px;
  --text-label:      10px;

  /* Line Heights */
  --lh-display:    1.1;
  --lh-heading:    1.3;
  --lh-body:       2.0;    /* 中文正文必须 2.0 */
  --lh-body-sm:    1.75;
  --lh-caption:    1.4;

  /* Letter Spacing */
  --ls-display:    0.15em;
  --ls-heading:    0.2em;
  --ls-subheading: 0.2em;
  --ls-body:       0.05em;
  --ls-caption:    0.2em;
  --ls-label:      0.15em;

  /* === SPACING (4px base grid) === */
  --space-2xs: 4px;
  --space-xs:  8px;
  --space-sm:  12px;
  --space-md:  16px;
  --space-lg:  24px;
  --space-xl:  32px;
  --space-2xl: 48px;
  --space-3xl: 64px;
  --space-4xl: 80px;

  /* === RADII (0px 直角为主) === */
  --radius-element:   0px;
  --radius-control:   0px;
  --radius-component: 0px;
  --radius-container: 2px;
  --radius-pill:      2px;

  /* === ELEVATION (Flat — no shadows) === */
  --shadow-none: none;

  /* === MOTION === */
  --easing-ritual:  cubic-bezier(0.22, 1, 0.36, 1);
  --duration-micro:    200ms;
  --duration-standard: 350ms;
  --duration-emphasis: 500ms;

  /* === BACKGROUND TEXTURE (羊皮纸纹) === */
  --bg-texture: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='4' height='4'%3E%3Crect width='4' height='4' fill='%23F5F0E8'/%3E%3Ccircle cx='1' cy='1' r='.4' fill='%23E8DCC8' opacity='.5'/%3E%3Ccircle cx='3' cy='3' r='.3' fill='%23DDD0B8' opacity='.3'/%3E%3C/svg%3E");
}

/* === DARK MODE === */
[data-theme="dark"], .dark {
  --background:     #1A1008;
  --bg:             var(--background);
  --surface1:       #2C1F0E;
  --surface2:       #3A2818;
  --surface3:       #4A3828;
  --border:         #4A3828;
  --border-visible: #6B5744;
  --text1:          #FAF6EE;
  --text2:          #C4A882;
  --text3:          #A89880;
  --text4:          #8B6E4E;
  --accent:         #D4A843;
  --accent-subtle:  #1E1505;
  --success-bg:     rgba(92,122,78,0.15);
  --warning-bg:     rgba(184,134,11,0.12);
  --error-bg:       rgba(139,58,58,0.15);
}

/* === BASE STYLES === */
body {
  background-color: var(--background);
  background-image: var(--bg-texture);
  color: var(--text1);
  font-family: var(--font-body);
  font-size: var(--text-body);
  line-height: var(--lh-body);
  letter-spacing: var(--ls-body);
  -webkit-font-smoothing: antialiased;
}

/* === UTILITY CLASSES === */

/* 顶部金色装饰线 */
.gold-top-line { border-top: 2px solid var(--accent); }

/* 装饰分割线 */
.divider {
  display: flex; align-items: center; gap: 12px;
  margin: 20px 0;
  color: var(--border-visible);
  font-size: 0.7rem;
  letter-spacing: 0.3em;
}
.divider::before, .divider::after {
  content: ''; flex: 1; height: 1px;
  background: linear-gradient(90deg, transparent, var(--border-visible), transparent);
}

/* 双重角花线框 */
.ornament-box {
  position: relative;
  border: 1px solid var(--border);
  padding: 24px;
}
.ornament-box::before {
  content: '';
  position: absolute; top: -3px; left: -3px; right: -3px; bottom: -3px;
  border: 1px solid var(--border);
  opacity: 0.4;
  pointer-events: none;
}
```

---

## TAILWIND CONFIG

```js
// tailwind.config.js
module.exports = {
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        // Neutral (warm parchment)
        neutral: {
          50:  '#FAF6EE',
          100: '#F5F0E8',
          150: '#EDE6D6',
          200: '#E0D5BF',
          300: '#C4A882',
          400: '#A89880',
          500: '#8B6E4E',
          600: '#6B5744',
          700: '#4A3828',
          800: '#3A2818',
          900: '#2C1F0E',
          950: '#1A1008',
        },
        // Brand gold
        gold: {
          50:  '#FDF8EC',
          100: '#FAF0D0',
          200: '#F0D88A',
          300: '#D4A843',
          400: '#C49020',
          500: '#B8860B',
          600: '#9A6F08',
          700: '#7A5C1E',
          800: '#5C4216',
          900: '#3D2C0A',
        },
        success: '#5C7A4E',
        warning: '#B8860B',
        error:   '#8B3A3A',
      },
      fontFamily: {
        display: ['"Cinzel Decorative"', '"Cinzel"', 'Georgia', 'serif'],
        heading: ['"Cinzel"', 'Georgia', '"Times New Roman"', 'serif'],
        body:    ['"Noto Serif SC"', 'Georgia', '"宋体"', 'serif'],
        mono:    ['"Courier New"', 'Courier', 'monospace'],
      },
      fontSize: {
        'display':    ['clamp(2.8rem,10vw,4.5rem)', { lineHeight: '1.1', letterSpacing: '0.15em' }],
        'heading':    ['20px', { lineHeight: '1.3', letterSpacing: '0.2em' }],
        'subheading': ['14px', { lineHeight: '1.4', letterSpacing: '0.2em' }],
        'body':       ['14px', { lineHeight: '2.0', letterSpacing: '0.05em' }],
        'body-sm':    ['12px', { lineHeight: '1.75', letterSpacing: '0.05em' }],
        'caption':    ['10px', { lineHeight: '1.4',  letterSpacing: '0.2em' }],
      },
      spacing: {
        '2xs': '4px',
        'xs':  '8px',
        'sm':  '12px',
        'md':  '16px',
        'lg':  '24px',
        'xl':  '32px',
        '2xl': '48px',
        '3xl': '64px',
        '4xl': '80px',
      },
      borderRadius: {
        none:      '0px',
        sm:        '2px',
        DEFAULT:   '0px',  // 默认直角
      },
      boxShadow: {
        none: 'none',       // flat 策略，无阴影
      },
      transitionTimingFunction: {
        ritual: 'cubic-bezier(0.22, 1, 0.36, 1)',
      },
      transitionDuration: {
        micro:    '200ms',
        standard: '350ms',
        emphasis: '500ms',
      },
    },
  },
};
```

---

## HTML TEMPLATE（完整页面骨架）

```html
<!DOCTYPE html>
<html lang="zh-CN" data-theme="light">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
  <title>神话人格测试</title>

  <!-- Google Fonts — 必须最先加载 -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Cinzel+Decorative:wght@400;700&family=Noto+Serif+SC:wght@300;400;500;700&display=swap" rel="stylesheet">

  <style>
    /* 粘贴上方的 CSS Custom Properties */
    /* 注意：必须在 :root 中声明所有变量 */
  </style>
</head>
<body>
  <!-- 顶部金色装饰线（可选） -->
  <div style="height:2px;background:var(--accent);"></div>

  <!-- 主内容区 -->
  <main style="max-width:540px;margin:0 auto;padding:32px 16px;">
    <!-- 内容 -->
  </main>

  <!-- 底部操作区（按需） -->
  <footer style="position:fixed;bottom:0;left:0;right:0;padding:16px;background:var(--background);border-top:1px solid var(--border);">
    <!-- 操作按钮 -->
  </footer>
</body>
</html>
```

---

## RESPONSIVE BREAKPOINTS

```css
/* 手机优先 */
:root { font-size: 15px; }
.content-wrap { padding: 0 16px; max-width: 540px; margin: 0 auto; }

/* 极小手机 (< 390px) */
@media (max-width: 390px) {
  :root { font-size: 14px; }
  .god-name-display { font-size: 2.4rem; }
}

/* 平板 (>= 600px) */
@media (min-width: 600px) {
  :root { font-size: 16px; }
  .content-wrap { max-width: 560px; padding: 0 24px; }
}
```
