# 包项目规范

## 1 包名称

使用 `all-lowercase-with-dashes` 命名方式。

以下是命名参考，每个选项都为可选：

**生态组件**：[技术系]-[组件名称]

```
react
react-router
react-redux
vue
vue-router
vue-resource
vue-cli
```

**平台组件**：[平台]-[技术系|场景]-[组件名称]

```
lk-react-app
lk-vue-app
lk-wechat-app
lk-util
lk-logger
lk-m-wechat
lk-m-payment
lk-m-share
lk-vuex
```


## 2 包版本

请参考[语义化版本 2.0.0](http://semver.org/lang/zh-CN/)

## 3 package.json

详细规则请参考 [package.json 中文说明文档](https://github.com/undead25/package.json) 和 [package.json 官方说明文档](https://docs.npmjs.com/files/package.json)

## 4 文件规范
 
请参考[源码文件规范](file.md)。

## 5 目录规范

一级目录划分请参考[目录结构规范](directory.md#51-一级目录)。

**src：** 按业务逻辑划分

**dist：** 输出umd规范的打包文件

## 6 参考资料

- http://semver.org/lang/zh-CN/
- https://docs.npmjs.com/files/package.json
- https://github.com/undead25/package.json
