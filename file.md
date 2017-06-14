# 源文件风格指南 (草稿)

## 1 引言

该文档主要的设计目标是让项目的源码文件的风格保持一致，使源码文件方便格式化与管理。

## 2 文件命名 

- [all-lowercase-with-dashes](http://www.ruanyifeng.com/blog/2017/02/filename-should-be-lowercase.html)。
- 文件名建议只使用小写字母，不使用大写字母；文件名包含多个单词时，单词之间建议使用半角的连词线（-）分隔。 
- 为了醒目，某些说明文件的文件名，可以使用大写字母，比如README、LICENSE。


## 3 文件注释

### 3.1 开源项目

文件头只要添加文件描述，不需要添加作者信息和版权信息，author 和 contributors 信息，在 GitHub 上可以清晰看出来。

```
/**
 * 文件描述
 */
```

### 3.2 业务项目
		
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

## 4 编辑器配置

官网链接：http://editorconfig.org

配置选项：https://github.com/editorconfig/editorconfig/wiki/EditorConfig-Properties


### 文件编码

`charset = utf-8`

**说明：** 使用无 BOM 的 UTF-8 编码，UTF-8 编码具有更广泛的适应性，BOM 在使用程序或工具处理文件时可能造成不必要的干扰。


### 缩进类型

`indent_style = space`

**说明：** 使用空格缩进，将制表符转为 2 个空格；因为使用制表符容易出现空格和制表符混用，而且不同的编辑器制表符的长度可能不一致，在不同的地方查看容易出现排版错乱。


### 缩进数量

`indent_size = 4`

**说明：** 一般设置 2 个或 4 个空格，项目内保持统一，不混用。为了不让缩进占用了太多的列宽，建议使用 2 个空格作为缩进。


### 换行符

`end_of_line = lf`

**说明：** 换行符格式，详细介绍请查看[Wiki：换行](https://zh.wikipedia.org/zh/%E6%8F%9B%E8%A1%8C)。


### 行末空格

`trim_trailing_whitespace = true`

**说明：** 自动清除所有行末空格


### 结尾空行

`insert_final_newline = true`

**说明：** 文件尾保留一个空行。UNIX 对文本文件的定义是由多行组成，每行需以换行符结尾，文件是流式的，文件尾保留一个空行可以被任意的拼接并且拼接后仍然保证完整性。

### 单行列宽

`max_line_length = 80`

**说明：** 尽量让你的代码保持在 80 列之内。终端界面默认显示都是 80 列宽。80 列限制事实上有助于避免代码可读性失控, 比如超多重嵌套块, 超多重函数调用等等。
在语句的行长度超过 120 时，根据逻辑条件合理缩进。

## 5 .editorconfig 配置示例

```
# http://editorconfig.org

root = true

[*]
charset = utf-8
end_of_line = lf
indent_style = space
indent_size = 4
trim_trailing_whitespace = true
max_line_length = 80
insert_final_newline = true

[{package.json,.**}]
indent_style = space
indent_size = 2

```

## 6 文件模版

### HTML File

```html

```

### CSS File

```css

```

### Less File

```less

```

### SCSS File

```scss

```

### JavaScript File

```javascript

```

### TypeScript File

```typescript

```
        

