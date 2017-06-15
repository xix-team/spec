# 目录结构规范 (草稿)

## 1 引言

该文档主要的设计目标是项目开发的目录结构保持一致，使容易理解并方便构建与管理。

## 2 目录命名

- 使用 `all-lowercase-with-dashes` 命名方式。文件名建议只使用小写字母，不使用大写字母；文件名包含多个单词时，单词之间建议使用半角的连词线（-）分隔。 
- 简洁。有习惯性缩写的单词 必须采用容易理解的缩写。下面是例子：
  - `js`: javascript脚本。 不得使用`script`、`scripts`等。
  - `css`: 样式表。 不得使用`style`、`styles`等。
  - `tpl`: 
  - `img`: 图片。 不得使用`image`、`images`、`imgs`等。
  - `swf`: flash。 不得使用`flash`等。
  - `src`: 源文件目录。 不得使用`source`等。
  - `lib`: 依赖包目录。 不得使用`library`、`dependency`等。
- 不得使用复数形式，目录就是用于存放多个文件，所以不需要使用多余的复数形式。如：`imgs`、`docs`、`images`、`tpls`、`examples`、`tests`是不被允许的。

> 扩展阅读 [all-lowercase-with-dashes](http://www.ruanyifeng.com/blog/2017/02/filename-should-be-lowercase.html)

## 3 目录划分原则

- 如无必要，勿增实体。

  根据项目的实际情况，当文件数量较多时，为方便管理， 应当根据对应的划分方法划分目录；例如对于组件来说，如果通过 README.md 就很清晰地说明如何使用，某些目录可以省略，就没必要增加 doc 和 example 目录。

- 目了然，容易学习。

## 资源分类

入口资源 entry
静态资源 asset
动态资源 server

`资源`分成两大类：

1. `源代码资源`：指开发者编写的源代码，包括`html`、`js`、`css`、`tpl`等。
2. `内容资源`：指希望做为内容提供给访问者的资源，包括`img`、`font`、`flash`、`pdf`等。


## 4 目录划分方法

### 4.1 一级目录划分

直接置于根目录下的目录称作`一级目录`。`一级目录` 必须按照`项目职能`划分。

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
  ├── dist          (存放部署文件，文件是通过开发者工具构建生成的)
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

除了上面列举的一些常见目录之外，根目录下下面也可以放置一些跟项目相关的功能文件，例如`yarn.lock`，`build.xml`，`Makefile`，`fis-conf.js`等等。


### 4.2 src 和 dist 目录划分

`src` 目录用于存放源码文件，绝大多数情况应当根据`业务逻辑`划分目录结构。

```

```

src/业务逻辑/业务职能/业务场景/业务分层/业务分块/文件类型

app-应用库(树形结构)-业务逻辑(业务场景-业务分层-业务分块)

lib-依赖库(扁平结构)

## 包项目
src 按业务逻辑划分

## 业务项目

src 按职能划分 - 按业务逻辑划分 - 按资源类型划分


### 按文件类型划分


### 业务目录划分原则

1. `JS资源` 不得按`资源类型`划分目录， *必须(MUST)* 按`业务逻辑`划分目录。`JS资源`应直接置于`业务目录`下。即：`业务目录`下禁止出现`js`目录。
2. 除`JS资源`外的`源文件资源`，当文件数量较多时，为方便管理， *允许(SHOULD)* 按`资源类型`划分目录。即：`业务目录`下允许出现`css`、`tpl`目录。
3. `内容资源` *允许(SHOULD)* 按`资源类型`划分目录。即：`业务目录`下允许出现`img`、`swf`、`font`目录。
4. `业务目录`中，如果文件太多不好管理，需要划分子目录时，也 *必须(MUST)* 继续遵守根据`业务逻辑`划分的原则，划分子业务。如：下面例子中的`subbiz1`。
   

通常，对于一个`业务目录`， *鼓励(SHOULD)* 将业务相关的`源文件资源`都直接置于`业务目录`下。

    biz1/
        img/
            add_button.png
        add.js
        add.tpl.html
        add.css

`业务目录`下`源文件资源`数量较多时，我们第一直觉应该是：是否业务划分不够细？是否应该划分子业务，建立子业务目录？

    biz2/
        subbiz1/
            list.js
            list.tpl.html
            list.css
        subbiz2/

遇到确实是一个业务整体，无法划分子业务时， *允许(MAY)* 将非`JS资源`按`文件类型`划分目录进行管理。

    biz1/
        css/
            add.css
            edit.css
            remove.css
            img/
                add_button.png
        tpl/
            add.html
            edit.html
            remove.html
        add.js
        edit.js
        remove.js

##### common

`src`目录下 *必须(MUST)* 只包含`业务目录`与`common`目录。`业务公共资源` *必须(MUST)* 命名为`common`。`common`目录做为`业务公共资源`的目录，也视如`业务目录`。
`common`目录为公共业务目录，用于存放业务项目的业务公共文件。所以，根据`业务逻辑`划分目录结构时，业务逻辑命名 不得为`common`。

    $root/
        src/
            common/
            biz1/
                subbiz1/
                subbiz2/
            biz2/


### 资源目录

根据`文件类型`划分的目录我们称为`资源目录`。`资源目录` 不得直接置于src下。

#### asset

```
通用组件目录
├── asset (资源目录)
│   ├── css
│   │   ├── item.css
│   │   └── list.css
│   ├── font
│   │   ├── iconfont.eot
│   │   ├── iconfont.svg
│   │   ├── iconfont.ttf
│   │   └── iconfont.woff
│   ├── img
│   │   ├── avatar.png
│   │   ├── default.png
│   │   └── favicon.ico
│   ├── swf
│   │   └── board.swf
│   ├── index.js  (源代码资源)
│   ├── index.css (源代码资源)
│   └── index.tpl (源代码资源)
└── index.html (入口)
```

#### js 存放脚本资源文件

#### css 存放样式资源文件

#### tpl 存放模板资源文件

#### img 存放图片资源文件

#### font 存放字体资源文件

#### swf 存放flash资源文件


`asset`目录用于存放用于`线上访问`的静态资源。

`RIA项目`通常会包含较少的`页面入口文件`，常见的是`main.html`，这些文件 *可以(SHOULD)* 直接放在`$root`目录下。

`多页面项目`通常`页面入口文件`较多， *可以(SHOULD)* 统一放在`entry`目录中，按`业务逻辑`命名。


```
根目录/
  - 一级目录/
    业务目录(业务职能/业务场景/业务分层/业务分块)/
      业务职能/
        业务场景/
          业务分层/
            业务分块/
              文件类型/
```

