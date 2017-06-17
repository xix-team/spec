# 业务项目规范

## 1 项目代号

业务项目*可以*为项目起一个代号名称。代号名称*必须*为一个单词，不宜过长。项目代号可以区分不同项目，还可以用于域名、源码仓库、业务目录等地方的命名。

## 2 项目版本

请参考[语义化版本 2.0.0](http://semver.org/lang/zh-CN/)

## 3 项目域名

[项目代号].[类型:m|api|bs].[环境:dev|sit|uat].[域名] 

## 4 package.json

**配置参考：**

使用 `npm init` 可以初始化。

```json
{
  "name": "项目代号",
  "description": "项目描述",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "asoiso",
  "license": "ISC"
}
```

详细规则请参考 [package.json 中文说明文档](https://github.com/undead25/package.json) 和 [package.json 官方说明文档](https://docs.npmjs.com/files/package.json)。

## 5 文件规范

请参考[源码文件规范](file.md)。

## 6 目录规范

请参考[目录结构规范](directory.md)。

## 7 参考资料

- http://semver.org/lang/zh-CN/
- https://docs.npmjs.com/files/package.json
- https://github.com/undead25/package.json
