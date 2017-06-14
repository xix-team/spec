# CSS \ Less \ Sass 风格指南 (草稿)

[1 引言](#1-引言)

[2 风格规范](#2-风格规范)

　　[2.1 命名](#2.1-命名)

　　[2.2 注释](#2.2-注释)

　　[2.3 格式](#2.3-格式)

[3 语言规范](#3-语言规范)

[4 代码检查](#4-代码检查)

[5 参考资料](#5-参考资料)

## 1 引言

## 2 风格规范

以行业内主流风格指南为基础，拓展符合我们团队的最佳实践。使 JavaScript 代码风格保持一致，容易被理解和被维护。

  - CSS [中文版](https://github.com/Zhangjd/css-style-guide) | [English](https://github.com/airbnb/css)

### 2.1 命名


#### [BEM](http://getbem.com/)

#### 常用命名

待完善
  
### 2.2 注释

#### 2.2.1 文件注释

```
/**
 * 文件描述
 */
```

#### 2.2.1 细节注释

- 建议使用行注释 (在 Sass、Less 中是 //) 代替块注释。有多行注释内容时，使用多个单行注释。
- 建议注释独占一行。避免行末注释。
- 给没有自注释的代码写上详细说明，比如：
  - 为什么用到了 z-index
  - 兼容性处理或者针对特定浏览器的 hack

### 2.3 格式

- CSS 格式配置应用 WebStorm Code Style -> CSS  标准配置，拓展部分在下面补充。

- Sass 格式配置应用 WebStorm Code Style -> Sass 标准配置，拓展部分在下面补充。

- SCSS 格式配置应用 WebStorm Code Style -> SCSS 标准配置，拓展部分在下面补充。

- Less 格式配置应用 WebStorm Code Style -> Less 标准配置，拓展部分在下面补充。

## 3 语言规范

遵循主流风格指南，拓展部分在下面补充。

## 4 代码检查

[StyleLint](https://stylelint.io/) 详细规则请参考 https://stylelint.io/user-guide/rules/

配置示例:

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
- https://github.com/Zhangjd/css-style-guide#注释
- https://github.com/ElemeFE/style-guide/blob/master/css-modulize.md
