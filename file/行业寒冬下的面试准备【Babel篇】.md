## 行业寒冬下的面试准备【Babel篇】

<br>

在2022年行业异常严峻的大前提下，笔者有幸能够跳槽成功，这段经历还是收获满满的。近期利用点时间将自己在跳槽过程中的记录整理对应的知识点集合，以供大家参考，如果发现有遗漏的知识点，欢迎大家补充~~~

根据自己的面试情况，对整理的面试的掌握要求做出对应的划分，不一定准确，供大家参考 

- ⭐：基本了解，面试中基本没被问到
- ⭐⭐：基本了解，偶尔在面试中遇到，但是频次较低
- ⭐⭐⭐：熟练掌握，在面试中高频遇到，要求将所有的知识点讲透
- ⭐⭐⭐⭐：深入了解，在面试中高频遇到，不仅要求掌握所有知识点，还需要进行扩展

本篇文章是 Babel 相关的面试题

### 1、聊一聊 Babel 原理吧(⭐⭐)

大多数 JavaScript 遵循 `estree` 规范，Babel 最初基于 `acorn` 项目（轻量级现代 JavaScript 解析器），Babel 大概分为三大部分：

-   **解析（Parse）**：将代码转换成 `AST`
    -   词法分析：将代码（字符串）分割成 `token` 流，即语法单元生成的数组
    -   语法分析：分析 `token` 流（上面生成的数组）并生成 `AST`
-   **转换（Transform）**：对于 `AST` 进行变换一系列的操作，`babel` 接受得到 `AST` 并通过 `babel-traverse` 对其遍历，在此过程中进行添加、更新及移除等操作
    -   `Taro` 就是利用 `babel` 完成的小程序语法转换
-   **生成（Generate）**：将变换后的 `AST` 再转换为 JS 代码，使用到的模块是 `babel-generator`

### 2、如何写一个 Babel 插件(⭐⭐)

`Babel` 解析成 `AST`，然后插件更改 `AST`，最后由 `Babel` 输出代码。那么 `Babel` 的插件模块需要你暴露一个 `function`，`function` 内返回 `visitor`

```js
module.export = function (babel) { 
    return {
        visitor: {}
    } 
}
```
`visitor` 是对各类型的 `AST` 节点做处理的地方，那么我们怎么知道 `Babel` 生成的 `AST` 有哪些节点呢？

很简单，你可以把 `Babel` 转换的结果打印出来，或者这里有传送门 [AST explorer](https://astexplorer.net/)

> 在 [行业寒冬下的面试准备【Babel篇】](https://github.com/Mohan710/file-collection/blob/dev/file/%E8%A1%8C%E4%B8%9A%E5%AF%92%E5%86%AC%E4%B8%8B%E7%9A%84%E9%9D%A2%E8%AF%95%E5%87%86%E5%A4%87%E3%80%90Babel%E7%AF%87%E3%80%91.pdf) 下载对应的PDF文件

## 相关文章

- [行业寒冬下的面试准备【JavaScript篇】](https://juejin.cn/post/7124575225278103559)
- [行业寒冬下的面试准备【Vue篇】](https://juejin.cn/post/7123908796048474120)
- [行业寒冬下的面试准备【Webpack篇】](https://juejin.cn/post/7124214145515257893)
