# 开发规范手册

## 1 原则

- 代码同出一门，保持整洁、易读、一致，码出质量、码出高效。
- 对待规范，要严格遵守；对待风格，要懂得尊重。
- 如果觉得有不合理或者遗漏的地方，请访问 New Issue。

## 2 目录

- [JavaScript \ EMCAScript \ TypeScript 编码规范](javascript-style-guide.md) [草稿]
- [CSS \ Less \ Sass 编码规范](css-style-guide.md) [草稿]
- [HTML 编码规范](html-style-guide.md) [草稿]
- [源码文件规范](file.md) [草稿]
- [目录结构规范](directory.md) [草稿]

## 3 规范书写要求

## 3.1 规则条目

- 【强制】规则描述

  **说明：** 规则补充说明
  
  **示例：**
  
  ```
  // 反例：
  
  // 正例：
  ```

- 【推荐】规则描述
- 【参考】规则描述

### 3.2 表示要求的动词

表达的时候，必须严格区分哪些是"建议"（suggestion），哪些是"要求"（requirement）。所以，[RFC2119]((http://www.ietf.org/rfc/rfc2119.txt))专门对一些词语的涵义做出了规定，定义了五个关键词，表示"要求"的严格程度。

- 必须 MUST、REQUIRED、SHALL

  表示绝对要求这样做。

- 不得 MUST NOT、SHALL
  
  表示绝对不要求这样做。
  
- 应该 SHOULD、RECOMMENDED
  
  表示一般情况下应该这样做，但是在某些特定情况下可以忽视这个要求。
  
- 不应该 SHOULD NOT、SHALL NOT
  
  表示一般情况下不应该这样做，但是在某些特定情况下可以忽视这个要求。
  
- 可以 MAY、OPTIONAL
  
  表示这个要求完全是可选的，你可以这样做，也可以不这样做。


> 拓展阅读 [RFC2119：表示要求的动词](http://www.ruanyifeng.com/blog/2007/03/rfc2119.html)

## 4 保障方法

- code format
	- 统一编辑器配置
- code lint
	- lint校验
- code inspect
	- webstorm inspect
	- sonar自动分析代码质量
- code review
	- 人工
