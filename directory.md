# 目录结构规范 (草稿)




## 1 引言

该文档主要的设计目标是项目开发的目录结构保持一致，使容易理解并方便构建与管理。

## 目录命名

1. 简洁。有习惯性缩写的单词 *必须(MUST)* 采用容易理解的缩写。如：源代码目录使用`src`，不使用`source`。下面是更多例子：
    1. `img`: 图片。 *禁止(MUST NOT)* 使用`image`、`images`、`imgs`等。
    2. `js`: javascript脚本。 *禁止(MUST NOT)* 使用`script`、`scripts`等。
    3. `css`: 样式表。 *禁止(MUST NOT)* 使用`style`、`styles`等。
    4. `swf`: flash。 *禁止(MUST NOT)* 使用`flash`等。
    5. `src`: 源文件目录。 *禁止(MUST NOT)* 使用`source`等。
    6. `lib`: 依赖包目录。 *禁止(MUST NOT)* 使用`library`、`dependency`等。
2. *禁止(MUST NOT)* 使用复数形式，目录本身就用于存放多个文件，不需要使用多余的复数形式。如：`imgs`、`docs`、`images`、`tpls`、`examples`、`tests`是不被允许的。

## 目录划分原则

根目录/一级目录/业务目录(业务职能/业务场景/业务分层/业务分块)/资源目录(文件类型)

### 按职能划分

### 按业务逻辑划分

### 按文件类型划分

## 一级目录划分

直接置于`$root`下的目录称作`一级目录`。`一级目录` *必须(MUST)* 按照`职能`划分， *禁止(MUST NOT)* 将`资源类型`或`业务逻辑`划分的目录直接置于`$root`下。

    $root/
        ├── bin           (存放可执行的文件)
        ├── conf          (存放项目部署配置文件)
        ├── doc           (存放文档文件。文档可以是开发者维护的文档，也可以是通过工具生成的文档)
        ├── example       (存放示例文件)
        ├── lib           (存放包项目的库文件)
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
        ├── .flowconfig 
        ├── .stylelintrc 
        └── ... 

除了上面列举的一些常见目录之外，`$root`下面也可以放置一些跟项目相关的功能文件，例如`yarn.lock`，`build.xml`，`Makefile`，`fis-conf.js`等等。






























### src

`src`目录用于存放源码文件。
`src`目录内，绝大多数情况 *应当(SHOULD)* 根据`业务逻辑`划分目录结构。

app-应用库(树形结构)-业务逻辑(业务场景-业务分层-业务分块)
lib-依赖库(扁平结构)

### 业务目录划分原则

根据`业务逻辑`划分的目录我们称为`业务目录`。

1. `JS资源` *禁止(MUST NOT)* 按`资源类型`划分目录， *必须(MUST)* 按`业务逻辑`划分目录。`JS资源`应直接置于`业务目录`下。即：`业务目录`下禁止出现`js`目录。
2. 除`JS资源`外的`源文件资源`，当资源数量较多时，为方便管理， *允许(SHOULD)* 按`资源类型`划分目录。即：`业务目录`下允许出现`css`、`tpl`目录。
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
`common`目录为公共业务目录，用于存放业务项目的业务公共文件。所以，根据`业务逻辑`划分目录结构时，业务逻辑命名 *禁止(MUST NOT)* 为`common`。

    $root/
        src/
            common/
            biz1/
                subbiz1/
                subbiz2/
            biz2/

### 包项目
`src`目录允许视如`业务目录`，直接按照业务目录划分原则划分目录结构。

    $root/
        src/
            foo.js


### 资源目录

根据`文件类型`划分的目录我们称为`资源目录`。`资源目录` *禁止(MUST NOT)* 直接置于src下。

#### asset

通用资源目录

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


资源目录
├── content (内容资源)
│   ├── avatar.png
│   ├── board.swf
│   ├── default.png
│   ├── favicon.ico
│   ├── iconfont.eot
│   ├── iconfont.svg
│   ├── iconfont.ttf
│   └── iconfont.woff
├── index.js  (源代码资源)
├── index.css (源代码资源)
└── index.tpl (源代码资源)


业务目录
  源代码资源(html,js,css,tpl)
   - asset/内容资源(img,font,flash,pdf)
   
业务目录
   入口(index.html)
   - asset/源代码资源(js,css,tpl)
   - asset/内容资源(img,font,flash,pdf)

#### js

`js`资源文件的后缀名 *可以(SHOULD)* 为js、jsx、es、ts、tsx 等。

`js`目录内 *必须(MUST)* 存放`js`资源文件，但`js`资源文件不一定（MAY NOT）存放于`js`目录下：

1. 对于`asset`目录，`js`资源文件 *可以(SHOULD)* 存放于`js`目录下。
3. 对于其他`一级目录`内，`js`资源文件 *可以(SHOULD)* 不存放于`js`目录下。

#### css

`css`资源文件的后缀名 *可以(SHOULD)* 为css、less、sass、scss 等。

`css`目录内 *必须(MUST)* 存放css资源文件，但`css`资源文件不一定（MAY NOT）存放于`css`目录下：

1. 对于`src`目录，`css`资源文件 *可以(SHOULD)* 存放于`业务目录`下，也 *可以(SHOULD)* 存放于`css`目录下。
2. 对于`asset`目录，`css`资源文件 *可以(SHOULD)* 存放于`css`目录下，视构建行为决定。
3. 对于其他`一级目录`内，`css`资源文件 *可以(SHOULD)* 不存放于`css`目录下。

#### tpl

模板资源文件的后缀名 *可以(SHOULD)* 为 html、tpl 等。

`tpl`目录内 *必须(MUST)* 存放模板资源文件，但模板资源文件不一定（MAY NOT）存放于`tpl`目录下：

#### img

图片资源文件的后缀名 *可以(SHOULD)* 为 gif、jpg、jpeg、png、svg、bmp、ico 等。

`img`目录内 *必须(MUST)* 存放图片资源文件。包括`页面直接引用`的图片与`css引用`图片。

对于`css`引用的图片， *必须(MUST)* 放在`./img`目录下，`.`代表当前`css`资源所在的目录。

对于`页面直接引用`的图片：

1. 被多页面引用的图片 *应该(SHOULD)* 放在`common/img`目录下。
2. 单一页面引用的图片 *应该(SHOULD)* 放在`./img`目录下，`.`代表当前页面所在的目录。


#### font

字体资源文件的后缀名 *可以(SHOULD)* 为 eot、woff、ttf、svg 等。

`font`目录内 *必须(MUST)* 存放字体资源文件。


#### swf

flash资源文件的后缀名 *可以(SHOULD)* 为 swf 。

`swf`目录内 *必须(MUST)* 存放flash资源文件。






### dist 目录结构划分

##### asset

`asset`目录用于存放用于`线上访问`的静态资源。

通常构建工具会对`src`目录和`dep`目录下的资源进行分析、合并与压缩等，生成到`asset`目录下。所以该目录尽量避免手工管理。下面是一个构建工具生成后的`asset`目录示例：

    $root/
        asset/
            js/
                loader.js
                build.js
            css/
                common.css
                img/
            tpl/
                build.tpl.html
            img/
            ...

`entry`目录用于存放项目的`页面入口文件`，通常是上线后可被直接访问的静态页面。

`RIA项目`通常会包含较少的`页面入口文件`，常见的是`main.html`，这些文件 *可以(SHOULD)* 直接放在`$root`目录下。

    $root/
        src/
            common/
                conf.js
            card/
            gold/
            message/
        index.html
        main.html
        ......


`多页面项目`通常`页面入口文件`较多， *可以(SHOULD)* 统一放在`entry`目录中，按`业务逻辑`命名。

    $root/
        src/
            common/
                conf.js
            card/
            gold/
            message/
        entry/
            card.html
            gold.html
            message.html
            ......


项目在发布的时候，构建工具可以`页面入口文件`为入口进行分析和编译。


`RIA项目`经过构建工具编译后，目录结构可能如下：

    output/
        asset/
            js/
            css/
            tpl/
            img/
        index.html
        main.html

`多页面项目`经过构建工具编译后，目录结构可能如下：

    output/
        card/
            asset/
                js/
                css/
                img/
            index.html
        gold/
            asset/
                js/
                css/
                img/
            index.html

#### 项目目录划分示例

    src/
        app/
            common/
                img/
                    sprites.png
                    logo.png
                conf.js
                layout.css
            biz1/
                img/
                    add_button.png
                add.js
                add.tpl.html
                add.less
            biz2/
                subbiz1/
                    list.js
                    list.tpl.html
                    list.css
                subbiz2/
        lib/
        index.html
        main.html
        ......

## 项目基础结构

## 包项目
src 按业务逻辑划分

## 业务项目
src 按职能划分 - 按业务逻辑划分 - 按资源类型划分




### 规范说明约定

以下规范文档中：

1. `项目`包含但不限于`业务项目`和`包项目`。
2. `$root`表示`项目`的根目录。


## 资源分类

入口资源 entry
静态资源 asset
动态资源 server



`资源`分成两大类：

1. `源代码资源`：指开发者编写的源代码，包括`html`、`js`、`css`、`tpl`等。
2. `内容资源`：指希望做为内容提供给访问者的资源，包括`img`、`font`、`flash`、`pdf`等。

