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

根据资源的运行环境、语言特性、业务逻辑等开发概念定义开发资源分类。按资源分类划分 `src` 目录。

### 5.3 dist 目录划分

`dist` 目录存放打包文件。

每个团队都会有自己的运维需求，资源部署经常牵连到公司技术架构，因此要根据运维和业务要求，结合构建工具，来划分 `dist` 目录。


### 5.4 组件目录划分

组件是最小的开发单位，`组件目录`内独立维护自己的 js、css、模板、图片 等文件。

*鼓励* 将业务相关的`源文件资源`都直接置于`组件目录`下。

```
biz
├── index.png
├── index.css
├── index.js
└── index.tpl
```

`组件目录`下`内容资源`数量较多时，*允许* 按`文件类型`划分子目录。即：`组件目录`下允许出现`img`、`swf`、`font`目录。

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

`组件目录`下`源文件资源`数量较多时，我们第一直觉应该是：是否业务划分不够细？是否应该划分子业务，建立子组件目录？需要划分子目录时，也 *必须* 继续遵守`业务逻辑`划分的原则，划分子业务。

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

遇到确实是一个业务整体，无法划分子业务时，允许将非`JS资源`按`文件类型`划分目录进行管理，即：`组件目录`下允许出现`css`、`tpl`目录。

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

## 6 src 和 dist 目录参考示例

**静态资源常用分类说明**

_以下只是参考，提供划分目录的思路，实际划分以业务为准。_

- **入口资源**：前端入口页面、后端模板页面，通常直接放在 src 的根目录下，文件数量较多时，可以划分目录。
- **静态资源**：可以命名为`asset`，也可以根据语言规范命名为`static`、`public`、`resource`等，存放静态资源文件。
  - **生态模块资源**：从 模块生态 下载的模块，属于外部依赖。
  - **应用模块化资源**：可以命名为`app`，存放当前应用的业务模块。这些模块通常跟业务耦合较高，是具有独立性的模块化资源。每个模块将自己所需要的js、css、模板、图片等资源放在一起维护。
      - **业务公共资源**：可以命名为`common`，用于存放业务项目的业务公共文件。
      - **业务场景资源**：根据业务场景命名，多页面下，一般与入口资源同名；单页面下，一般与项目代号同名，为未来项目留下扩展的后路。
  - **应用非模块化资源**：可以命名为`lib`，虽然在模块化开发体系内，应该一切皆模块，但总有不应该成为模块的资源，比如模块化框架、页面启动器等。
- **动态资源**：可以命名为`server`，也可以根据后端语言规范划分和命名。

### 6.1 示例1

说明：包项目

**资源分类：**

- 业务逻辑 

**src：** 按业务逻辑划分

**dist：** 输出umd规范的打包文件


### 6.2 示例2

说明：业务项目，Web Page 模式，纯前端项目，单入口，非模块化，例如：活动页面。

**资源分类：**

- **入口资源**
- **静态资源**
  
**src** 和 **dist** 目录结构一致

```
├── asset (静态资源目录)
│   ├── font
│   │   ├── iconfont.eot
│   │   ├── iconfont.svg
│   │   ├── iconfont.ttf
│   │   └── iconfont.woff
│   ├── img
│   │   ├── index.png
│   │   ├── default.png
│   │   └── favicon.ico
│   ├── swf
│   │   └── board.swf
│   ├── index.css
│   └── index.js
└── index.html (入口资源)
```

### 6.3 示例3

说明：Web Page 模式，纯前端项目，多入口，非模块化，例如：静态展示网站。

**资源分类：**

- **入口资源**
- **静态资源**
  - **业务公共资源**
  - **业务场景资源**

**src：**

```
├── asset (静态资源目录)
│   ├── common (业务公共资源目录)
│   │   └── ...                         
│   ├── authorize (业务场景资源目录)
│   │   ├── img                         
│   │   │   ├── header.png              
│   │   │   ├── iloka.png               
│   │   │   ├── toutiao.png             
│   │   │   ├── wechat.png              
│   │   │   └── weibo.png               
│   │   ├── index.js                    
│   │   ├── result.css                  
│   │   └── result.js                   
│   ├── oauth                           
│   ├── payment                         
│   └── app.js (应用框架)
├── authorize.html                      
├── authorize-result.html               
├── oauth.html                          
├── oauth-callback.html
└── payment-wechat.html (入口资源)
```

**dist：**

```
├── asset (静态资源目录)
│   ├── authorize (打包后内容资源目录)
│   │   └── img
│   │       ├── header.309ecb.png
│   │       ├── iloka.8e661b.png
│   │       ├── toutiao.4c0431.png
│   │       ├── wechat.657d11.png
│   │       └── weibo.d0f7f2.png
│   ├── ...
│   └── pkg (打包文件目录)
│       ├── authorize.aa43b1.js
│       ├── authorize-result.390559.js
│       ├── oauth.766f36.js
│       ├── oauth-callback.719db6.js
│       └── payment-wechat.77cf68.js
├── authorize.html
├── authorize-result.html
├── oauth.html                          
├── oauth-callback.html
└── payment-wechat.html (入口资源)

```

### 6.4 示例4

说明：Web App 模式，纯前端项目，单入口，有生态模块资源，有非模块化资源，有模块化资源，fis3构建，例如：C端商城。

**资源分类：**

- **入口资源**
- **生态模块资源**
- **应用模块化资源**
- **应用非模块化资源**
  - **业务公共资源**
  - **业务场景资源**

**src：**

```
├── app (应用非模块化资源目录)
│   ├── common (业务公共资源目录)
│   │   ├── iconfont
│   │   │   ├── iconfont.eot
│   │   │   ├── iconfont.svg
│   │   │   ├── iconfont.ttf
│   │   │   └── iconfont.woff
│   │   └── ...
│   └── m (业务场景资源目录)
│       ├── page
│       │   ├── home
│       │   │   ├── img
│       │   │   │   ├── money.png
│       │   │   │   └── product.png
│       │   │   ├── index.js
│       │   │   ├── index.less
│       │   │   └── index.tpl
│       │   └── ...
│       ├── ...
│       └── index.js
├── lib (应用非模块化资源目录)
│   ├── ...
│   ├── fastclick
│   │   └── fastclick.js
│   ├── flexible
│   │   ├── flexible.js
│   │   └── flexible_css.js
│   ├── mod
│   │   └── mod.js
│   └── seed
│       ├── loading.gif
│       ├── seed.css
│       └── seed.js
├── node_modules (生态模块资源目录)
├── favicon.ico
├── favicon.png
└── index.html (入口资源)
```

**dist：**

```
├── asset (静态资源目录)
│   ├── app (打包后内容资源目录)
│   │   ├── common
│   │   │   ├── iconfont
│   │   │   │   ├── iconfont.276005.woff
│   │   │   │   ├── iconfont.35515f.eot
│   │   │   │   ├── iconfont.6358a8.ttf
│   │   │   │   └── iconfont.e5a7cf.svg
│   │   │   └── ...
│   │   └── m
│   │       ├── page
│   │       │   ├── home
│   │       │   │   └── img
│   │       │   │       ├── money.607fb8.png
│   │       │   │       └── product.ecdd39.png
│   │       │   └── ...
│   │       └── ...
│   ├── lib (打包后非模块资源目录)
│   │   ├── seed
│   │   │   ├── loading.38ed26.gif
│   │   │   ├── seed.b5dcbc.css
│   │   │   └── seed.eb7611.js
│   │   └── ...
│   └── pkg (打包文件目录)
│       ├── lib.37e5d2.css
│       ├── lib.48336d.js
│       ├── app.65f637.css
│       └── app.a700ad.js
├── favicon.ico
├── favicon.png
└── index.html (入口资源)
```

### 6.5 示例5

说明：Web App 模式，纯前端项目，多入口，有生态模块资源，有非模块化资源，有模块化资源，fis3构建，例如：B端中台。

**资源分类：**

- **入口资源**
- **生态模块资源**
- **应用模块化资源**
- **应用非模块化资源**
  - **业务公共资源**
  - **业务场景资源**

**src：**

```
├── app (应用模块化资源目录)
│   ├── common (业务公共资源目录)
│   ├── content (业务场景资源目录)
│   │   ├── ...
│   │   └── index.js
│   ├── h5
│   ├── index
│   ├── marketing
│   ├── mobile
│   └── platform
├── lib (应用非模块化资源目录)
│   ├── mod
│   ├── seed
│   ├── ueditor
│   └── ...
├── node_modules (生态模块资源目录)
├── content.html
├── favicon.ico
├── favicon.png
├── h5.html
├── index.html
├── marketing.html
├── mobile.html
├── platform.html (入口资源)
└── robots.txt
```

**dist：**

```
├── asset (静态资源目录)
│   ├── app (打包后内容资源目录)
│   │   └── ...
│   ├── lib (打包后非模块化资源目录)
│   │   └── ...
│   └── pkg (打包文件目录)
│       ├── common.9a9def.js
│       ├── common.d41d59.css
│       ├── content.037bbb.js
│       ├── content.be468e.css
│       ├── h5.95da69.js
│       ├── h5.e3f125.css
│       ├── index.acc1dd.css
│       ├── index.b5e557.js
│       ├── lib.3a7345.js
│       ├── lib.c90e12.css
│       ├── marketing.4aecf8.css
│       ├── marketing.ced405.js
│       ├── mobile.357ddb.css
│       ├── mobile.c78d40.js
│       ├── platform.bb6942.css
│       └── platform.c393f9.js
├── content.html
├── h5.html
├── index.html
├── marketing.html
├── mobile.html
├── platform.html (入口资源)
├── favicon.ico
├── favicon.png
└── robots.txt
```

### 6.6 示例6

说明：Web App 模式，纯前端项目，单入口，有生态模块资源，一切皆模块，没有非模块化资源，webpack构建，例如：C端商城。

**资源分类：**

- **入口资源**
- **生态模块资源**
- **应用业务公共资源**
- **应用业务场景资源**
  
**src：**

```
├── common (应用业务公共资源目录)
├── m (应用业务场景资源目录)
│   ├── ...
│   └── index.js
├── favicon.ico
├── favicon.png
└── index.tpl (入口资源)
```

**dist：**

```
├── asset (静态资源目录)
│   ├── img (打包后图片资源目录)
│   │   └── ...
│   ├── font (打包后字体资源目录)
│   │   └── ...
│   ├── app.bb6942.css (aio打包文件)
│   └── app.c393f9.js  (aio打包文件)
├── favicon.ico
├── favicon.png
└── index.html (入口资源)
```

### 6.7 示例7

说明：Web App 模式，纯前端项目，多入口，有生态模块资源，一切皆模块，没有非模块化资源，webpack构建，例如：B端中台。

**资源分类：**

- **入口资源**
- **生态模块资源**
- **业务公共资源**
- **业务场景资源**

**src：**

```
├── common (业务公共资源目录)
│   └── ...
├── content (业务场景资源目录)
│   ├── ...
│   └── index.js
├── h5
├── index
├── marketing
├── mobile
├── platform
│   └── ...
├── favicon.ico
├── favicon.png
└── index.tpl (入口资源模版)
```

**dist：**

```
├── asset (静态资源目录)
│   ├── img (打包后图片资源目录)
│   │   └── ...
│   ├── font (打包后字体资源目录)
│   │   └── ...
│   ├── common.9a9def.js
│   ├── common.d41d59.css
│   ├── content.037bbb.js
│   ├── content.be468e.css
│   ├── h5.95da69.js
│   ├── h5.e3f125.css
│   ├── index.acc1dd.css
│   ├── index.b5e557.js
│   ├── lib.3a7345.js
│   ├── lib.c90e12.css
│   ├── marketing.4aecf8.css
│   ├── marketing.ced405.js
│   ├── mobile.357ddb.css
│   ├── mobile.c78d40.js
│   ├── platform.bb6942.css
│   └── platform.c393f9.js
├── content.html
├── h5.html
├── index.html (入口资源)
├── marketing.html
├── mobile.html
├── platform.html
├── favicon.ico
├── favicon.png
└── robots.txt
```

### 6.8 示例8

说明：Web App 模式，前后混合，多入口，例如：复合型系统。

**资源分类：**

- **入口资源**
- **静态资源**
  - **业务公共资源**
  - **业务场景资源**
- **动态资源**

**src** 和 **dist** 目录结构一致

```
├── public (静态资源目录)
│   ├── common (业务公共资源目录)
│   ├── user (业务场景资源目录)
│   ├── index (业务场景资源目录)
│   └── ...
├── routes
│   ├── index.js
│   └── users.js
├── views (入口资源目录)
│   ├── error.jade
│   ├── index.jade
│   └── layout.jade
└── app.js
```

```
├── index.jsp (入口资源目录)
├── META-INF  (动态资源目录)
├── WEB-INF   (动态资源目录)
└── resources (静态资源)
    ├── common (业务公共资源目录)
    ├── index  (业务场景资源目录)
    └── ...
```

## 7 参考资料

- https://github.com/ecomfe/spec/blob/master/directory.md
- https://github.com/fouber/blog/issues/2

#### [返回目录](README.md)
#### [回到顶部](#)
