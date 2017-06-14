# CSS \ Less \ Sass 风格指南 (草稿)

#### [返回目录](README.md)

[1 引言](#1-引言)

[2 风格规范](#2-风格规范)

　　[2.1 命名](#2.1-命名)

　　[2.2 注释](#2.2-注释)

　　[2.3 格式](#2.3-格式)

[3 语言规范](#3-语言规范)

[4 代码检查](#4-代码检查)

[5 参考资料](#5-参考资料)

## 1 引言

### 1.1 原则

- 坚持遵循同一套代码规范，代码同出一门，保持整洁、易读、一致，更容易被理解和被维护。
- 对待规范，要严格遵守；对待风格，要懂得尊重。
- 如果你想要为这个规范做贡献或觉得有不合理的地方，请访问New Issue。

### 1.2 说明

本文档以 `Airbnb CSS Style Guide` 为基础，编写符合自己团队的风格指南；
统一了**命名**和**注释**两大痛点，就统一了80%的风格，所以我们重点拓展这两部分内容，主体部分请参考基础。

### 1.3 基础

- CSS [中文版](https://github.com/Zhangjd/css-style-guide) | [English](https://github.com/airbnb/css)
  
## 2 风格规范

### 2.1 命名

#### 2.1.1 类选择器

出于以下原因，我们鼓励使用 OOCSS 和 BEM 的某种组合：

  * 可以帮助我们理清 CSS 和 HTML 之间清晰且严谨的关系。
  * 可以帮助我们创建出可重用、易装配的组件。
  * 可以减少嵌套，降低特定性。
  * 可以帮助我们创建出可扩展的样式表。

**OOCSS(http://oocss.org/)**，也就是 “Object Oriented CSS（面向对象的CSS）”，是一种写 CSS 的方法，其思想就是鼓励你把样式表看作“对象”的集合：创建可重用性、可重复性的代码段让你可以在整个网站中多次使用。

参考资料：

  * Nicole Sullivan 的 [OOCSS wiki](https://github.com/stubbornella/oocss/wiki)
  * Smashing Magazine 的 [Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)

**[BEM](http://getbem.com/)**，也就是 “Block-Element-Modifier”，是一种用于 HTML 和 CSS 类名的_命名约定_。BEM 最初是由 Yandex 提出的，要知道他们拥有巨大的代码库和可伸缩性，BEM 就是为此而生的，并且可以作为一套遵循 OOCSS 的参考指导规范。

  * CSS Trick 的 [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts 的 [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

以下两种方式都可以，项目内保持统一。

**命名方式1：**

```html
<article class="listing-card listing-card-active">

  <h1 class="listing-card-title">标题</h1>

  <div class="listing-card-content">
    <p>内容</p>
  </div>

</article>
```

```css
.listing-card{ }
.listing-card-active{ }
.listing-card-title{ }
.listing-card-content{ }
.listing-card-footer{ }
```

  * `.listing-card` 是一个块（block），表示高层次的组件。
  * `.listing-card-title` 是一个元素（element），它属于 `.listing-card` 的一部分，因此块是由元素组成的。
  * `.listing-card-featured` 是一个修饰符（modifier），表示这个块与 `.listing-card` 有着不同的状态或者变化。

**命名方式2：**

```html
<article class="listing-card listing-card--active">

  <h1 class="listing-card__title">标题</h1>

  <div class="listing-card__content">
    <p>内容</p>
  </div>

</article>
```

```css
.listing-card { }
.listing-card--active { }
.listing-card__title { }
.listing-card__content { }
```

  * `.listing-card` 是一个块（block），表示高层次的组件。
  * `.listing-card__title` 是一个元素（element），它属于 `.listing-card` 的一部分，因此块是由元素组成的。
  * `.listing-card--featured` 是一个修饰符（modifier），表示这个块与 `.listing-card` 有着不同的状态或者变化。

#### 2.1.2 ID 选择器

在 CSS 中，虽然可以通过 ID 选择元素，但大家通常都会把这种方式列为反面教材。ID 选择器给你的规则声明带来了不必要的高[优先级](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)，而且 ID 选择器是不可重用的。

想要了解关于这个主题的更多内容，参见 [CSS Wizardry 的文章](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/)，文章中有关于如何处理优先级的内容。

#### 2.1.3 JavaScript 钩子

避免在 CSS 和 JavaScript 中绑定相同的类。否则开发者在重构时通常会出现以下情况：轻则浪费时间在对照查找每个要改变的类，重则因为害怕破坏功能而不敢作出更改。

我们推荐在创建用于特定 JavaScript 的类名时，添加 `.js-` 前缀：

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

#### 2.1.4 命名空间

#### 2.1.5 常用命名

待完善
  
### 2.2 注释

#### 2.2.1 文件注释

```
/**
 * 文件描述
 */
```

#### 2.2.1 细节注释

建议注释独占一行，有多行注释内容时，使用多个单行注释。避免行末注释。

```css
/* CSS注释内容 */
```

```less
// Less注释内容
```

```sass
// Sass注释内容
```

### 2.3 格式

- CSS 格式配置应用 WebStorm Code Style -> CSS  标准配置，拓展部分在下面补充。

- Sass 格式配置应用 WebStorm Code Style -> Sass 标准配置，拓展部分在下面补充。

- SCSS 格式配置应用 WebStorm Code Style -> SCSS 标准配置，拓展部分在下面补充。

- Less 格式配置应用 WebStorm Code Style -> Less 标准配置，拓展部分在下面补充。

## 3 语言规范

遵循主流风格指南，拓展部分在下面补充。

## 4 代码检查

[StyleLint](https://stylelint.io/) 详细规则请参考 https://stylelint.io/user-guide/rules/

`.stylelintrc` 配置示例:

```stylelint
{
  "extends": "stylelint-config-standard",
  "rules": {
    "at-rule-empty-line-before": null,
    "at-rule-name-space-after": null,
    "comment-empty-line-before": null,
    "declaration-bang-space-before": null,
    "declaration-empty-line-before": null,
    "function-comma-newline-after": null,
    "function-name-case": null,
    "function-parentheses-newline-inside": null,
    "function-max-empty-lines": null,
    "function-whitespace-after": null,
    "indentation": null,
    "number-leading-zero": null,
    "number-no-trailing-zeros": null,
    "rule-empty-line-before": null,
    "selector-list-comma-newline-after": null,
    "selector-pseudo-element-colon-notation": null,
    "unit-no-unknown": null,
    "value-list-max-empty-lines": null,
    "color-hex-length": null,
    "length-zero-no-unit": null,
    "shorthand-property-no-redundant-values": null,
    "declaration-block-no-redundant-longhand-properties": null,
    "no-eol-whitespace": null,
    "no-missing-end-of-source-newline": null,
    "declaration-block-semicolon-newline-after": null,
    "block-closing-brace-empty-line-before": null,
    "function-comma-space-after": null,
    "block-closing-brace-newline-before": null,
    "comment-whitespace-inside": null
  }
}
```

## 5 参考资料

- https://github.com/airbnb/css
- https://github.com/ecomfe/spec/blob/master/css-style-guide.md
- https://github.com/ecomfe/spec/blob/master/less-code-style.md
- https://github.com/ElemeFE/style-guide/blob/master/css-modulize.md
- https://github.com/airbnb/javascript/tree/master/css-in-javascript
- https://github.com/Zhangjd/css-style-guide

#### [返回目录](README.md)
#### [回到顶部](#)
