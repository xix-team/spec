# 技术文档写作规范

## 1 基本书写规范

- 尽量用中文，力求简洁清晰。（注：源码中的注释，可用英文。）
- 含有中文的段落，标点符号必须用中文全角。
- 中英文混杂时，中文与英文之间，要保持一个空格。
- 更多内容请参考阮一峰的[《中文技术文档的写作规范》](https://github.com/ruanyf/document-style-guide)。

## 2 README.md 书写规范

每个项目的根目录下，必须有该文件，用来描述项目的基本情况。

## 3 CHANGELOG.md 书写规范

有正式版本更新的项目，必须要有该文件，用来描述版本变更情况，模板如下：

```
  ## 版本号 / 更新日期
  * `[+]` 新增 XXX 功能
  * `[-]` 移除 XXX 功能
  * `[^]` 更新 XXX 功能
  * `[#]` 修复 XXX 问题
  
  ## 0.1.0 / 2017-06-01
  * 初始化项目

  ## 0.2.0 / 2017-06-10
  * [+] 新增 AAA 功能
  * [^] 优化 BBB 代码
  * [#] #18 修复 CCC 问题
  * [#] #36 修复 DDD 问题
  
  ## 1.0.0 / 2017-06-18
  * 正式发布
  
```

## 4 规范文档书写规范

## 4.1 规则条目

- 【强制】规则描述

  **说明：** 规则补充说明
  
  **示例：**
  
  ```
  // 反例：
  
  // 正例：
  ```

- 【推荐】规则描述
- 【参考】规则描述

### 4.2 表示要求的动词

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


## 参考资料

- https://github.com/ruanyf/document-style-guide
- https://github.com/aralejs/aralejs.github.io/wiki/文档书写规范
- http://www.ietf.org/rfc/rfc2119.txt
- http://www.ruanyifeng.com/blog/2007/03/rfc2119.html
