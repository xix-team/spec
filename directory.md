# 目录结构规范 (草稿)

#### [返回目录](README.md)

[1 引言](#1-引言)

[2 资源分类](#2-资源分类)

[3 目录命名](#3-目录命名)

[4 目录划分原则](#4-目录划分原则)

[5 目录划分方法](#5-目录划分方法)

[6 src 和 dist 目录参考示例](#6-src-和-dist-目录参考示例)
  
[7 参考资料](#7-参考资料)

## 1 引言

该文档主要的设计目标是项目开发的目录结构保持一致，使容易理解并方便构建与管理。

## 2 资源分类

`资源`分成两大类：

1. `源文件资源`：指开发者编写的源代码，包括`js`、`html`、`css`等。
2. `内容资源`：指希望做为内容提供给访问者的资源，包括`图片`、`字体`、`flash`、`pdf`等。

## 3 目录命名

- 使用 `all-lowercase-with-dashes` 命名方式。文件名建议只使用小写字母，不使用大写字母；文件名包含多个单词时，单词之间建议使用半角的连词线（-）分隔。 
- 简洁。有习惯性缩写的单词必须采用容易理解的缩写。下面是例子：
  - `js`:  脚本。 不得使用`script`、`scripts`等。
  - `css`: 样式表。 不得使用`style`、`styles`等。
  - `tpl`: 模板。不得使用`template`、`templates`、`tpls`等.
  - `img`: 图片。 不得使用`image`、`images`、`imgs`等。
  - `swf`: flash。 不得使用`flash`等。
  - `src`: 源文件目录。 不得使用`source`等。
  - `lib`: 依赖包目录。 不得使用`library`、`dependency`等。
- 不得使用复数形式，目录就是用于存放多个文件，所以不需要使用多余的复数形式。如：`imgs`、`docs`、`tpls`、`examples`、`tests`是不被允许的。

> 扩展阅读 [all-lowercase-with-dashes](http://www.ruanyifeng.com/blog/2017/02/filename-should-be-lowercase.html)

## 4 目录划分原则

- 如无必要，勿增实体。

  根据项目的实际情况，当文件数量较多时，为方便管理， 应当根据对应的划分方法划分目录；对于组件来说，如果通过 README.md 就很清晰地说明如何使用，某些目录可以省略，就没必要增加 doc 和 example 目录。

- 一目了然，容易学习。

## 5 目录划分方法

### 5.1 一级目录

直接置于根目录下的目录称作`一级目录`。`一级目录` 必须按照`项目职能`划分，以下为常见目录。

```
root
  ├── bin           (存放可执行的文件)
  ├── conf          (存放项目部署配置文件)
  ├── doc           (存放文档文件。文档可以是开发者维护的文档，也可以是通过工具生成的文档)
  ├── example       (存放示例文件)
  ├── lib           (存放包项目的库文件,业务项目用不到)
  ├── node_modules  (存放项目引入的依赖包,该目录下的内容由 npm 或 yarn 管理，禁止手动更改目录下的任何内容)
  ├── src           (存放源码文件)
  ├── test          (存放测试用例)
  ├── dist          (存放打包文件)
  ├── tool          (存放开发者工具)
  ├── CHANGELOG.md  (更新日志文档)
  ├── README.md     (总体说明文档)
  ├── LICENSE       (版权许可证)
  ├── package.json  (项目元信息文件)
  ├── yarn.lock     (yarn源锁定文件)
  ├── .gitignore    (git忽略文件)
  ├── .npmignore    (npm忽略文件)
  ├── .editorconfig (编辑器配置)
  ├── .eslintignore 
  ├── .eslintrc 
  ├── .stylelintrc 
  ├── .htmllintrc 
  └── ... 
```

除了上面列举的一些常见目录之外，根目录下下面也可以放置一些跟项目相关的功能文件，例如`yarn.lock`，`package.json`，`Makefile`，`fis-conf.js`，`webpack.config.js`等等。

### 5.2 src 目录划分

`src` 目录存放源码文件。

### 5.2.1 按开发概念划分

根据资源的运行环境、语言特性、业务场景等设计语义化开发概念，定义开发资源的分类。按开发概念划分 `src` 目录。

### 5.2.2 模块目录按业务逻辑划分

根据`业务逻辑`划分的目录，我们称为`业务目录`。

*鼓励* 将业务相关的`源文件资源`都直接置于`业务目录`下。

```
biz
├── index.png
├── index.css
├── index.js
└── index.tpl

```

`业务目录`下`内容资源`数量较多时，*允许* 按`文件类型`划分子目录。即：`业务目录`下允许出现`img`、`swf`、`font`目录。

```
biz
├── font
│   ├── iconfont.eot
│   ├── iconfont.svg
│   ├── iconfont.ttf
│   └── iconfont.woff
├── img
│   ├── index.png
│   ├── default.png
│   └── favicon.ico
├── swf
│   └── board.swf
├── index.js
├── index.css
└── index.tpl
```

`业务目录`下`源文件资源`数量较多时，我们第一直觉应该是：是否业务划分不够细？是否应该划分子业务，建立子业务目录？需要划分子目录时，也 *必须* 继续遵守`业务逻辑`划分的原则，划分子业务。

```
biz
├── subbiz1
│   ├── index.css
│   ├── index.js
│   └── index.tpl
└── subbiz2
    ├── index.css
    ├── index.js
    └── index.tpl
```

遇到确实是一个业务整体，无法划分子业务时，允许将非`JS资源`按`文件类型`划分目录进行管理，即：`业务目录`下允许出现`css`、`tpl`目录。

```
biz
├── css
│   ├── add.css
│   ├── edit.css
│   ├── list.css
│   └── img
│       ├── default.png
│       ├── icon.png
│       └── index.png
├── tpl
│   ├── add.tpl
│   ├── edit.tpl
│   └── list.tpl
├── img
│   └── banner.png
├── edit.js
├── list.js
└── add.js
```


### 5.3 dist 目录划分

`dist` 目录存放打包文件。

每个团队都会有自己的运维需求，资源部署经常牵连到公司技术架构，因此要根据运维和业务要求，结合构建工具，来划分 `dist` 目录。


## 6 src 和 dist 目录参考示例

### 6.1 示例1

说明：Web Page 模式，纯静态，单入口，非模块化，例如：活动页面。

**开发概念：**

- **入口资源**
- **静态资源**

**src：**

```
```

**dist：**

```
```


### 6.2 示例2

说明：Web Page 模式，纯静态，多入口，非模块化，例如：静态官网。

**开发概念：**

- **入口资源**
- **静态资源**

**src：**

```
├── asset
│   ├── common
│   ├── content
│   ├── mobile
│   └── index
├── content.html
├── mobile.html
└── index.html
```

**dist：**

```
├── asset
│   ├── common
│   ├── content
│   ├── mobile
│   ├── index
│   └── pkg       
├── content.html
├── mobile.html
└── index.html
```

### 6.3 示例3

说明：Web App 模式，纯静态，单入口，有非模块化资源，有模块化资源，fis3构建，例如：C端商城。

**开发概念：**

**src：**

```
```

**dist：**

```
```

### 6.4 示例4

说明：Web App 模式，纯静态，多入口，有非模块化资源，有模块化资源，fis3构建，例如：B端中台。

**开发概念：**

**src：**

```
```

**dist：**

```
```

### 6.5 示例5

说明：Web App 模式，纯静态，单入口，只有模块化资源，webpack构建，例如：C端商城。

**开发概念：**

**src：**

```
```

**dist：**

```
```

### 6.6 示例6

说明：Web App 模式，纯静态，多入口，只有模块化资源，webpack构建，例如：B端中台。

**开发概念：**

**src：**

```
```

**dist：**

```
```

### 6.7 示例7

说明：Web App 模式，动静结合，多入口，webpack构建，例如：复合型系统。

**开发概念：**

- **入口资源**：前端入口页面、后端模板页面。
- **静态资源目录**：可以命名为`asset`，也可以根据语言规范命名为`static`、`public`、`resource`等，存放静态资源文件。
  - **应用模块目录**：可以命名为`app`，存放当前应用的业务模块。
    - **业务公共目录**：可以命名为`common`，用于存放业务项目的业务公共文件。
    - **业务场景目录**：根据业务场景命名，多页面下，一般与前端入口文件同名；单页面下，一般与项目代号同名，为未来项目留下扩展的后路。
  - **依赖模块目录**：存放模块化框架、页面启动器。
- **动态资源目录**：可以命名为`server`，也可以根据后端语言规范划分和命名，存放动态资源文件。

**src：**

```
```

**dist：**

```
```

## 7 参考资料

- https://github.com/ecomfe/spec/blob/master/directory.md
- https://github.com/fouber/blog/issues/2

#### [返回目录](README.md)
#### [回到顶部](#)
