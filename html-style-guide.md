# HTML 风格指南 (草稿)

#### [返回目录](README.md)

[1 引言](#1-引言)

[2 风格规范](#2-风格规范)

　　[2.1 命名](#2.1-命名)

　　[2.2 注释](#2.2-注释)

　　[2.3 格式](#2.3-格式)

[3 语言规范](#3-语言规范)

[4 标准代码](#4-标准代码)

[5 代码检查](#5-代码检查)

[6 参考资料](#6-参考资料)

## 1 引言

### 1.1 原则

- 坚持遵循同一套代码规范，代码同出一门，保持整洁、易读、一致，更容易被理解和被维护。
- 对待规范，要严格遵守；对待风格，要懂得尊重。
- 如果你想要为这个规范做贡献或觉得有不合理的地方，请访问New Issue。

### 1.2 说明

以行业内主流风格指南为基础，编写符合自己团队的风格指南。

## 2 风格规范

### 2.1 命名

- `class` 和 `id`  单词全字母小写，单词间以 `-` 分隔。

- 元素 `id` 必须保证页面唯一。

### 2.2 注释

```html
<!-- 注释内容 -->
```

### 2.3 格式

HTML 格式配置应用 WebStorm Code Style -> HTML 标准配置，拓展部分在下面补充。

## 3 语言规范

遵循主流风格指南，拓展部分在下面补充。

## 4 代码检查

[HtmlLint](http://htmllint.github.io/) 详细规则请参考 https://github.com/htmllint/htmllint/wiki/Options

`.htmllintrc` 配置示例:

```htmllint
{
  "force": true,
  "tag-name-lowercase": false,
  "disable-inline-style": true,
  "indent-width": 2
}
```

## 5 参考资料

- https://github.com/ecomfe/spec/blob/master/html-style-guide.md

#### [返回目录](README.md)
#### [回到顶部](#)
