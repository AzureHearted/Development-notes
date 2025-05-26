###### Element语法

> [!note]
>
> **参考：**
>
> - [一篇文章搞懂【Emmet】语法规则，让前端编码健步如飞！ - 掘金 (juejin.cn)](https://juejin.cn/post/701856
>   [7571876102151)
> - [Emmet 文档 (yanxyz.github.io)](https://yanxyz.github.io/emmet-docs/)

# 初始化HTML结构

新建一个html结构后可以使用`!`+`tab`建初始化HTML结构

1. 输入：

![初始HTML结构1.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6b5e6ca7dcfe45a6955859e658ddc231~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

1. 按tab或回车后：

![初始HTML结构2.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f7c105e559e147199dafc1dcc43e3711~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# id（`#`）和class（.）

生成一个带有id或者类名的emmet语法：

1. id：`div#main`+`tab`
2. class: `div.head`+`tab`；多个类可以继续追加`div.head.box`+`tab`
3. 组合：`div#main2.body`+`tab`和`div#main2.body.box`+`tab`

**注意**：**输入完一行要紧接着按`tab`！！！！**

输入

```javascript
javascript复制代码div#main
div.head
div.head.box
div#main2.body
div#main2.body.box
```

![id和class生成1.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b174a27bd36b48969038aefdaf721caf~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

每一行后面紧接着按`tab`后：

![id和class生成.jpg](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8d1e5f9e88134b9aa45c5b70907a15cb~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# 子节点（`>`）、上级节点（^)、兄弟结点（`+`）

## 子节点（`>`）

使用`>`连接两个标签名，后者会加在前者的内部（即成为前者的子元素）

例如输入如下：

```css
css复制代码div>p 
div>p>span
```

每一行按`tab`会生成：

![子节点.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d198fbd2bad643769c43ea19042b550b~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

## 上级节点（`^`）

与`>`符号常常同时使用；在`^`符号后的元素名会与前一各元素的父级元素同级。`^`可以连续使用，表示上升多级。

具体看实例：

```css
css复制代码    div>p^a

    div>ul>li^p
    
    div>ul>li^^p
```

每行会生成：

![上级结点.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e3a27dc4e252411090713646fb43e20a~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

## 兄弟结点（`+`）

被`+`符号相连的元素最后生成同级元素。

输入例子：

```css
css复制代码    div+p

    div+a+p
```

结果：

![兄弟结点.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/71d684850f5c47dbbd2eb82fdcd11ae9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# 重复（`*`）

有时候需要生成多个同样的标签，可以直接yong`*`生成而不用一个个复制。

输入例子：

```css
css复制代码    h2*5
    
    ul>li*6
```

结果：

![重复.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ab36e1d3246848f58fffb09d6b3de3fa~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# 属性（[attr]）

与id和class比较类似，是为元素添加其它任意属性的。

例子：

```css
css复制代码    div[name='main']
    
    a[href="www.baidu.com" name="baidu"]
```

结果：

![属性.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/59cfe259cbd64c66a8a2fb04ef4c1b75~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# 编号（`$`）

动态生成的序号，`$`代表一位数字，后面跟的`*`和数字代表从1递增到紧跟的数字

例子：

```css
css

复制代码ul>li.item$*6
```

结果：

![编号1.jpg](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e4259a58c5e04bdda6040ccd92e5b560~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

**补充**：

- 可以设置多位数字（一个`$`代表一位数字，就可以连写多个会在前面补0）

例子：

```css
css

复制代码ul>li.item$$$*6
```

结果：

![编号2.jpg](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ad6cba0463c94176832097195762b4e7~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

- 可以在`$`后加`@-`实现倒序

例子：

```css
css

复制代码ul>li.item$@-*6
```

结果：

![编号3.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1a4a17033ee74548bbc4621ee9281ba8~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

- 在`$` 后面添加 `@N` 改变编号的起始基数

例子：(代表从3基数开始，生成共5个)

```css
css

复制代码ul>li.item$@3*5
```

结果：

![编号4.jpg](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/08d22d4955fd4687bbb3322df781a1b1~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# 7.文本（`{}`）

元素后面使用`{}`符号可以在元素内部加入`{}`内容。

例子：

```css
p{一段文本}

a[href="www.baidu.com"]{百度}
```

结果：

![文本1.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cf927f8a2c5d48259e23ea3d331af95a~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)

# 分组（`()`）

可以组合代码块，写较长的emmet语法时用来分隔。

```css
css

复制代码div>(ul>li>a[href="www.baidu.com"])+p
```

结果：

![组合.jpg](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d6c174d4304049f88a08f2729d0a95cd~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)





# The End
