# 常用词命名统一表

## 原则：

1. *可读性强，见名知义。*
1. 尽量不与社区已有的习惯冲突。
1. 尽量写全。不用缩写，除非是下面列表中约定的。

大家一起来，逐步完善。

https://github.com/aralejs/aralejs.github.io/wiki/常用词命名统一表

## 项目名

## 目录名

## 文件名

### 页面
| 页面名 | 说明 |
| index | 默认页 |
| list  | 列表页 |
| show  | 查看详情页 | 
| form  | 表单页 |

## CSS命名

## 函数名
| list         | 列表 | 
| show         | 查看 | 
| add          | 新增 | 
| edit         | 编辑 | 
| save         | 保存 | 
| del          | 删除 | 
| remove       | 移除 | 
| clear        | 清空 | 
| refresh      | 刷新 | 
| search       | 搜索 | 
| sort         | 排序 | 
| filter       | 筛选 | 
| check        | 检测 | 
| exists       | 存在 | 
| checkAll     | 全选 | 
| checkInverse | 反选 | 
| batch        | 批量 | 

## 属性名

| 常用词 | 说明 |
| options | 表示配置，与 jQuery 社区保持一致，不要用 config, opts 等 |
| active | 表示当前，不要用 current 等 |
| index | 表示索引，不要用 idx 等 |
| trigger | 触点元素 |
| triggerType | 触发类型、方式 |
| context | 表示传入的 this 对象 |
| object | 推荐写全，不推荐简写为 o, obj 等 |
| element | 推荐写全，不推荐简写为 el, elem 等 |
| length | 不要写成 len, l |
| prev | previous 的缩写 |
| constructor | 不能写成 ctor |
| easing | 表示动画平滑函数 |
| min | minimize 的缩写 |
| max | maximize 的缩写 |
| DOM | 不要写成 dom, Dom |
| .tpl | 使用 tpl 后缀表示模版 |
| btn | button 的缩写 |


### 异步操作状态
| pending | 挂起 |
| success | 成功 |
| failure | 失败 |

### Promise
未完成（unfulfilled）
已完成（resolved）
拒绝的（rejected）

```
var Promise = function (resolve, reject) {
    /* initialize promise */
    if(true){
       resolve(resolved)
    }else{
       reject(rejected)
    }
}

Promise.prototype.then = funciton(onResolved, onRejected){
    //
}

```


### actions
新增XX      ADD_USER  | CREATE_USER
获取XX      GET_USER  | FETCH_USER
获取XX列表   GET_USERS | FETCH_USERS
修改XX      UPDATE_USER
保存XX      SAVE_USER
删除XX      DEL_USER

addUser(){

}

getUsers(){

}

getUser(){

}

updateUser(){

}

saveUser(){

}

delPost(){

}

### URL

| GET     | FETCH   | 从服务器取出资源（一项或多项）|
| POST    | CREATE  | 在服务器新建一个资源|
| PUT     | UPDATE  | 在服务器更新资源（客户端提供改变后的完整资源）|
| PATCH   | UPDATE  | 在服务器更新资源（客户端提供改变的属性）|
| DELETE  | DELETE  | 从服务器删除资源|
| HEAD    |         | 获取资源的元数据|
| OPTIONS |         | 获取信息，关于资源的哪些属性是客户端可以改变的|
| 
| GET    | /zoos | 获取所有动物园 |
| POST   | /zoos | 新增一个动物园 |
| GET    | /zoos/ID | 获取某个指定动物园的详情 |
| PUT    | /zoos/ID | 更新某个指定动物园的详情（提供该动物园的全部信息） |
| PATCH  | /zoos/ID | 更新某个指定动物园的信息（提供该动物园的部分信息） |
| DELETE | /zoos/ID | 删除某个动物园 |
| GET    | /zoos/ID/animals | 列出某个指定动物园的所有动物 |
| DELETE | /zoos/ID/animals/ID | 删除某个指定动物园的指定动物 |

### URL参数
| ?fields=name,age,sex   | 指定返回记录的字段 |
| ?limit=10              | 指定返回记录的数量 | 
| ?offset=10             | 指定返回记录的开始位置。| 
| ?page=2&size=100       | 指定第几页，以及每页的记录数。| 
| ?sort=name,desc        | 指定返回结果按照哪个属性排序，以及排序顺序。| 
| ?sort=name&order=asc   | 指定返回结果按照哪个属性排序，以及排序顺序。| 


