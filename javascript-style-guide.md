# JavaScript \ EMCAScript \ TypeScript 风格指南 (草稿)

[1 引言](#1-引言)

[2 风格规范](#2-风格规范)

　　[2.1 命名](#2.1-命名)

　　[2.2 注释](#2.2-注释)

　　[2.3 格式](#2.3-格式)

[3 语言规范](#3-语言规范)

[4 代码检查](#4-代码检查)

[5 参考资料](#5-参考资料)

## 1 引言

以行业内主流风格指南为基础，拓展符合我们团队的最佳实践。使 JavaScript 代码风格保持一致，容易被理解和被维护。

  - JavaScript [中文版](https://github.com/sivan/javascript-style-guide/tree/master/es5) | [English](https://github.com/airbnb/javascript)
  - ES5 [中文版](https://github.com/yuche/javascript) | [English](https://github.com/airbnb/javascript/tree/es5-deprecated/es5)
  - React [中文版](https://github.com/JasonBoy/javascript/tree/master/react) | [English](https://github.com/airbnb/javascript/tree/es5-deprecated/react)
  - [CSS-in-JavaScript](https://github.com/airbnb/javascript/tree/master/css-in-javascript)

## 2 风格规范

### 2.1 命名

  - 使用 `驼峰式(lowerCamelCase)` 命名变量和函数。
  
  ```javascript
  let thisIsMyObject = {};
  
  function thisIsMyFunction() {}
  ```

  - 使用 `帕斯卡式(UpperCamelCase)` 命名构造函数、类、枚举。
  
  ```javascript
  class User {
    name = 'xxx';
  }
  
  function User(options) {
    this.name = options.name;
  }
  
  const TargetState = {
    PENDING:1,
    SUCCESS:2,
    FAILURE:3
  };
  ```
    
  - 使用 `全部字母大写，单词间下划线分隔(CONSTANT_CASE)` 的命名方式命名常量和枚举的属性
  
  ```javascript
  const HTML_ENTITY = 1;
  
  const TargetState = {
    PENDING:1,
    SUCCESS:2,
    FAILURE:3
  };
  ```

  - 由多个单词组成的缩写词，在命名中，根据当前命名法和出现的位置，所有字母的大小写与首字母的大小写保持一致。
  
  ```javascript
  function XMLParser() {}
  
  function insertHTML(element, html) {}
  
  var httpRequest = new HTTPRequest();
  ```

  - 不要使用下划线前/后缀。

  > 解释：JavaScript 并没有私有属性或私有方法的概念。虽然使用下划线是表示「私有」的一种共识，但实际上这些属性是完全公开的，它本身就是你公共接口的一部分。这种习惯或许会导致开发者错误的认为改动它不会造成破坏或者不需要去测试。长话短说：如果你想要某处为「私有」，它必须不能是显式提出的。

  ```javascript
  // bad
  this.__firstName__ = 'Panda';
  this.firstName_ = 'Panda';
  this._firstName = 'Panda';
  
  // good
  this.firstName = 'Panda';
  ```

#### 常用命名
 
待完善

### 2.2 注释

#### 2.2.1 单行注释

必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。

#### 2.2.2 多行注释

避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。

> 解释：注释块（/* ... */）中不能有(/*或*/，JavaScript正则表达式中可能产生这种代码)，这样会产生语法错误，有多行注释内容时，使用多个单行注释。

#### 2.2.3 文件注释

文件顶部必须包含文件注释，标识文件描述

##### 开源项目

文件头只要添加文件描述，不需要添加作者信息和版权信息，author 和 contributors 信息，在 GitHub 上可以清晰看出来。

```
/**
 * 文件描述
 */
```

##### 业务项目

- 添加文件描述	
- 使用 @copyright 标识，添加版权信息。
- 使用 @author 标识，添加上责任人信息，以便遇到问题时，快速找到相关责任人。
	- 通常情况文件在被创建时标识的是创建者。
	- 随着项目的进展，模块移交给其他人，新的责任人在新增代码时，添加 @author 标识应该把自己的名字添加在创建人的前面。
	- @author 标识具有多人时，按照责任进行排序。也就是如果有问题，就是找第一个人应该比找第二个人有效。
	- @author 中的名字不允许被删除。任何劳动成果都应该被尊重。
- 使用 @since 标识，描述此功能何时被添加进来的，可以为版本号，也可以为创建时间。

```
/**
 * 文件描述
 * @copyright Copyright ${COMPNAY} All Rights Reserved.
 * @author ${USER} <${EMAIL}>
 * @author ${USER} <${EMAIL}>
 * @since ${DATE}
 */
```

#### 2.2.4 文档化注释

JSDoc可以根据文档化注释，生成 JavaScript 应用程序或库、模块的API文档，现在很多编辑器或 IDE 中还可以通过 JSDoc 直接或使用插件生成智能提示。

详细规则请参考 [Use JSDoc](http://usejsdoc.org/) 和 [JSDoc Guide](http://www.css88.com/doc/jsdoc/index.html)；

#### 2.2.5 细节注释

对于内部实现、不容易理解的逻辑说明、摘要信息等，我们可能需要编写细节注释。
细节注释遵循单行注释的格式。说明必须换行时，每行是一个单行注释的起始。

```javascript
function foo(p1, p2, opt_p3) {
    // 这里对具体内部逻辑进行说明
    // 说明太长需要换行
    for (...) {
        ....
    }
}
```

给注释增加 `FIXME` 或 `TODO` 的前缀可以帮助其他开发者快速了解这是一个需要复查的问题，或是给需要实现的功能提供一个解决方式。这将有别于常见的注释，因为它们是可操作的。
使用 `FIXME -- need to figure this out` 或者 `TODO -- need to implement`。

- 使用 `// FIXME:` 标注问题。

```javascript
function Calculator() {

  // FIXME: shouldn't use a global here
  total = 0;

  return this;
}
```

- 使用 `// TODO:` 标注问题的解决方式。

```javascript
function Calculator() {

  // TODO: total should be configurable by an options param
  this.total = 0;

  return this;
}
```

### 2.3 格式

- JavaScript 格式配置应用 WebStorm Code Style -> JavaScript -> Predefined Style -> JavaScript Standard Style 标准配置，拓展部分在下面补充。
  - indent 使用4个空格缩进
  - quotes 使用单引号
  - semi   使用分号
  - no-extra-semi 禁止多余的分号

- TypeScript 格式配置应用 WebStorm Code Style -> WebStorm Code Style -> Less 标准配置，拓展部分在下面补充。

## 3 语言规范

遵循主流风格指南，拓展部分在下面补充。

## 4 代码检查

### 4.1 [ESLint](http://eslint.org/)

详细规则请参考 http://eslint.org/docs/rules/

`eslintrc` 配置示例:

```eslint
{
  "extends": [
    "eslint-config-airbnb"
  ],
  "env": {
    "browser": true,
    "node": true,
    "jasmine": true,
    "jest": true,
    "es6": true
  },
  "parser": "babel-eslint",
  "parserOptions": {
    "ecmaVersion": 6,
    "ecmaFeatures": {
      "jsx": true,
      "experimentalObjectRestSpread": true
    }
  },
  "plugins": [
    "markdown",
    "react",
    "babel"
  ],
  "rules": {
    "func-names": 0,
    "arrow-body-style": 0,
    "react/sort-comp": 0,
    "react/prop-types": 0,
    "react/jsx-first-prop-new-line": 0,
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [
          ".js",
          ".jsx",
          ".md"
        ]
      }
    ],
    "import/extensions": 0,
    "import/no-unresolved": 0,
    "import/no-extraneous-dependencies": 0,
    "no-param-reassign": 0,
    "no-return-assign": 0,
    "max-len": 0,
    "consistent-return": 0,
    "no-redeclare": 0,
    "react/require-extension": 0,
    "jsx-a11y/no-static-element-interactions": 0,
    "jsx-a11y/anchor-has-content": 0,
    "react/no-danger": 0,
    "comma-dangle": [
      "error",
      "always-multiline"
    ]
  }
}
```

### 4.2 [TSLint](https://palantir.github.io/tslint/)

详细规则请参考 https://palantir.github.io/tslint/rules/

`tsconfig.json` 配置示例:

```tslint
{
  "compilerOptions": {
    "strictNullChecks": true,
    "moduleResolution": "node",
    "allowSyntheticDefaultImports": true,
    "experimentalDecorators": true,
    "jsx": "preserve",
    "noUnusedParameters": true,
    "noUnusedLocals": true,
    "target": "es6",
    "lib": [
      "dom",
      "es7"
    ]
  },
  "exclude": [
    "node_modules",
    "lib",
    "es"
  ]
}
```

## 5 参考资料

- https://github.com/airbnb/javascript
- https://google.github.io/styleguide/jsguide.html
- https://github.com/ecomfe/spec/blob/master/javascript-style-guide.md
- http://alloyteam.github.io/CodeGuide/
- https://github.com/aralejs/aralejs.github.io/issues/36
- http://usejsdoc.org/
- http://www.css88.com/doc/jsdoc/index.html
- https://github.com/aralejs/aralejs.github.io/issues/36
- https://github.com/aralejs/aralejs.github.io/wiki/JavaScript-注释规范
