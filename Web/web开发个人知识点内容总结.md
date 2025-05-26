###### web开发个人笔记<br>~Lxs~

# Typora相关

## 主题

### `Notion`主题

> 参考:*[Notion for Typora](https://github.com/adrian-fuertes/typora-notion-theme)*_~Ye~_

### `VLOOK Thinking`主题

> 地址：[VLOOK™ ── 让你的 Markdown 有了新看(wán)法](https://github.com/MadMaxChow/VLOOK)
>
> 安装教程：[简介 - VLOOK™ - Markdown 编辑器 Typora 的主题包和增强插件](https://madmaxchow.github.io/VLOOK/index.html#安装与使用)
>
> 说明文档：[快速参考手册 (Part.I) - VLOOK™ - Markdown 编辑器 Typora 的主题包和增强插件](https://madmaxchow.github.io/VLOOK/guide.html#)


> 查找其他主题：[Themes Gallery — Typora](https://theme.typora.io/)

## 使用技巧

### 折叠内容

```html
<!-- 直接在markdown中输入这串代码(注意不能有隔行) -->
<details>
  <summary>指南1</summary>
  内容
</details>
```



### 内嵌网页

```html
<!-- 直接在markdown中输入这串代码(注意不能有隔行) -->
<iframe height='700' scrolling='no'
        title=''
        src='{{url路径}}'
        importance='low'
        frameborder='no'
        allowtransparency='true'
        allowfullscreen='true'
        style='width: 100%;'
        loading="lazy">
</iframe>
```

# 编程字体

## `Fira Code` 字体

> 参考：[`Fira Code`: 免费的编程连字等宽字体](https://github.com/tonsky/FiraCode)

<details>
    <summary>字体预览</summary>
    <img src="https://github.com/tonsky/FiraCode/raw/master/extras/ligatures.png"/>
</details>




---

# HTML、CSS 相关

## img标签下方的空隙

在HTML中，`<img>`标签下方有时会出现意外的空隙，这通常是由于行内元素的基线对齐造成的。`<img>`标签是<u>行内元素</u>，它的底部会与包含它的行内框的基线对齐，这可能导致图片下方出现看似“空隙”的空间。

### 解决方法一：使用 `vertical-align` 属性

你可以通过设置`vertical-align`属性来调整图片的垂直对齐方式。常用的值有`top`、`middle`、`bottom`或`text-bottom`。例如：

```html
<img src="your-image.png" alt="Your Image" style="vertical-align: top;">
```

### 方法二：将图片转换为块级元素

你也可以将`<img>`标签转换为块级元素，这样它就不会受到基线对齐的影响了。可以通过设置`display`属性为`block`来实现：

```html
<img src="your-image.png" alt="Your Image" style="display: block;">
```

### 方法三：使用CSS的 `line-height` 属性

另一种方法是调整包含`<img>`标签的元素的`line-height`属性。如果`<img>`标签是行内元素，减少`line-height`的值可以减少图片下方的空间。

```html
<div style="line-height: 0;">  
  <img src="your-image.png" alt="Your Image">  
</div>
```

### 方法四：使用CSS的 `font-size` 属性

将父元素的`font-size`设置为`0`也可以消除由字体基线造成的空隙。

```html
<div style="font-size: 0;">  
  <img src="your-image.png" alt="Your Image">  
</div>
```



## `offsetHeight` 和 `clientHeight`的区别

`offsetHeight` 和 `clientHeight` 是用来获取元素高度的两个属性，它们的含义有所不同：

1. **`offsetHeight`**:
   - 包括了元素的高度、垂直内边距(padding)和边框(border)，但不包括外边距(margin)。
   - 即 `offsetHeight = height + padding-top + padding-bottom + border-top + border-bottom`。
2. **`clientHeight`**:
   - 表示元素**内容区域**的高度，包括了内边距(padding)，但不包括边框(border)和外边距(margin)。
   - 如果存在滚动条，则不包括滚动条的高度。
   - 对于不可见的元素（例如`display: none`），`clientHeight` 为 0。
   - 对于行内元素和绝对定位的元素，`clientHeight` 也可以获取，但需要设置相应的 CSS 属性（例如 `display: block` 或 `position: absolute`）。

因此，当你需要获取元素的完整高度，包括边框和内边距时，应该使用 `offsetHeight`；而当你只关心元素内容区域的高度时，可以使用 `clientHeight`。

## 元素的居中

### 水平居中

对于*块级元素` `*（如 `<div>`），你可以通过设置左右外边距为 `auto` 来实现水平居中：

```css
.block-element {  
  margin-left: auto;  
  margin-right: auto;  
  width: 50%; /* 或者你需要的任何宽度 */  
}
```

对于行内元素（如 `<span>` 或文本），你可以使用 `text-align: center;` 在其父级块级元素中居中：

```css
.block-element {  
  margin-left: auto;  
  margin-right: auto;  
  width: 50%; /* 或者你需要的任何宽度 */  
}
```

对于行内元素（如 `<span>` 或文本），你可以使用 `text-align: center;` 在其父级块级元素中居中：

## CSS animation动画的暂停和播放控制

###### `animation-play-state` 属性

这个属性用于控制元素动画的运行状态。其语法如下：

```css
animation-play-state: paused | running | initial | inherit;
```

属性值解释如下：

- `paused`：表示动画将被暂停，此时元素会停止运行动画。
- `running`：表示正常播放动画。
- `initial`：表示属性被设置为它的初始值。
- `inherit`：表示属性继承父元素的属性值。

通过改变这个属性的值，可以控制动画的播放或暂停状态。例如，可以通过JavaScript在特定的事件发生时改变这个属性的值，从而控制动画的播放或暂停。

> [!warning]
>
> > 需要注意的是，虽然 `animation-play-state` 属性可以控制动画的播放状态，<u>但它并不能提供动画执行的百分比</u>。如果你需要获取动画执行的百分比，你可能需要使用JavaScript结合CSS动画事件来实现。
>
> > 此外，不同的浏览器对 `animation-play-state` 属性的支持情况可能有所不同。因此，在使用这个属性时，你需要确保目标浏览器支持这个属性，并可能需要添加浏览器前缀或使用其他兼容方案。

# 块级元素和内联元素的区别

内联元素与块级元素在HTML和CSS布局中有明显的区别，这些区别主要体现在以下几个方面：

1. **排列方式**：块级元素<u>默认会独占一行</u>，无论其内容多少，都会占据其父元素的整个宽度。而内联元素则不会独占一行，它们会在一行内显示，相邻的内联元素会排在同一行，直到行宽被占满才会换行。
2. **宽高边距设置**：块级元素可以设置宽度（width）和高度（height），同时也可以设置上下左右的边距（margin和padding）。然而，内联元素<u>不能设置宽度和高度</u>，其宽度随内容的变化而变化，同时内联元素<u>只能设置左右方向的边距（margin和padding）</u>，上下方向的边距则无效。
3. **默认宽度**：块级元素的宽度默认为<u>其父元素的100%</u>，而内联元素的宽度则是由其内容或子元素来决定。

在使用CSS进行布局时，需要注意以下几点：

1. **理解元素的显示特性**：在设计布局时，首先要理解所使用的HTML元素的默认显示特性（是块级还是内联），以便更好地控制其布局行为。
2. **避免宽度和高度冲突**：对于内联元素，设置宽度和高度通常无效，因此要避免在这些元素上设置这些属性，以免引发布局问题。
3. **边距和内填充的设置**：对于内联元素，上下方向的边距和内填充通常无效，因此在设置这些属性时要特别注意。
4. **浮动和定位的影响**：浮动（float）和定位（position）属性可以改变元素的布局行为，包括块级元素和内联元素。在使用这些属性时，要注意它们对其他元素的影响，以及可能引发的布局问题。
5. **兼容性考虑**：不同的浏览器可能对CSS的支持程度不同，因此在设计布局时要考虑兼容性问题，尽量避免使用某些不被广泛支持的CSS特性。





---

# JavaScript 相关

## MVC模式

MVC模式（`Model-View-Controller`）是一种软件设计模式，它把软件系统分为三个基本部分：模型（Model）、视图（View）和控制器（Controller）。这种模式的核心目的是将数据的存储（模型）、数据的展示（视图）以及用户交互（控制器）分离，使得软件的结构更加清晰、可维护性更好。

以下是MVC模式中每个组件的简要说明：

1. 模型（Model）：

   - 负责存储应用的数据和状态。
   - 定义数据修改和处理的逻辑。
   - 通常，模型不依赖于视图和控制器，它们可以被多个视图共享，以减少代码重复。
   
2. 视图（View）：

   - 向用户展示信息。
   - 通常从模型获取数据，并以某种形式（如图形界面）展示这些数据。
   - 视图不处理业务逻辑或用户输入，它只是显示信息。

3. 控制器（Controller）：

   - 处理用户的输入（如点击按钮、输入文本等）。
   - 根据用户的输入更新模型的状态。
   - 选择适当的视图来展示更新后的模型状态。
   - 控制器在视图和模型之间起中介作用，确保它们之间的通信是同步的。

MVC模式通过明确划分这三个组件的职责，使得开发者能够更独立地开发、测试和维护每个组件。当业务逻辑、用户界面或数据模型发生变化时，这种分离使得影响被限制在特定的组件内，从而减少了整个系统的复杂性。

MVC模式广泛应用于各种应用程序中，特别是Web应用程序和桌面应用程序。然而，它并不是唯一的设计模式，还有其他如MVVM（Model-View-ViewModel）等设计模式也用于解决类似的问题。选择哪种模式取决于具体的应用需求、开发团队的偏好以及项目的复杂性等因素。

## Javascript 类型转换规则

> js原始类型有：String、Number、Boolean、Undefined、Null、Symbol(符号)、BigInt(大整数)
>
> 这些原始类型是 JavaScript 中最基本的数据类型，除了 `Symbol` 和 `BigInt`，其他类型都是按值传递的。

### 原始类型转Number

```js
true 		// 1
false 		// 0
null 		// 0
undefined 	// NaN
// string 分两种情况
// 1. 空字符串,如:
"" 			// 0
" " 		// 0
"\t\n\r"	// 0
// 2. 去掉引号不是数字就是NaN,如:
"0"			// 0
"1"			// 1
"AB"		// NaN
" ab "		// NaN
"NaN"		// NaN
" 123 "		// 123
"\t123\r" 	// 123
"12 3"		// NaN
```



### 所有其他类型转Boolean

```js
null						// false
undefined				// false
NaN							// false
// number 类型分2种情况:为0时为false,其他都为true
0 			// false
1 			// true
3 			// true
// number 类型分2种情况:空字符串为false,其他都为true
"" 						// false
" " 					// false
"\t\n\r"			// false
"h"						// true	
"hello world"	// true
{}						// true 无论是否有属性
[]						// true 无论是否有元素
```



### 原始类型转String

```js
null					// "null"
undefined			// "undefined"
NaN						// "NaN"
1							// "1"
123						// "123"
true					// "true"
false					// "false"
```



### 对象转原始类型

```js
// 对象转原始类型的步骤：调用对象中的valueOf()方法 --> (若返回结果还是对象) --> 调用toString()方法 --> (若返回结果还是对象) --> 报错
// 情形1
let o1 = {}
console.log(+o1) 	// undefined

// 情形2
let o2 = {
    valueOf:()=>{
    	return 1
	}
}
console.log(+o2) 	// 结果为 NaN 
// 情形2的等价转换过程如下
console.log(Number(o2.valueOf().toString()))

// 情形3
let o3 = {
    valueOf:()=>{
    	return {}
	},
    toString:()={
        return {}
    }
}
console.log(+o3) 	// 报错
```



## Javascript 运算规则

### 算数运算

> `+ - * / %` 和`++ --`
>
> 先将非原始类型转为原始类型后再进行算数运算

```js
// 转为数字,然后运算
console.log(null + undefined)	// NaN 过程等价与 0 + NaN -> NaN
console.log([] + {})			// "[object Object]"
// 特殊情况1: x + y ,x和y有一个是字符串。转为字符串,然后拼接
console.log(10 + "2")			// "102"
// 特殊情况2: NaN和任何类型算数运算(也就是运算符两端都是必须是数字)得到的还是NaN
console.log(NaN + 1)		// NaN
console.log(NaN + "2")		// NaN
```



### 比较运算

> `> < >= <=`和`== != `和`=== !==`

1. `> < >= <=` 的运算，先将运算符两边转为原始类型

   - 一般规则：转为数字，然后比较

   - 特殊情况1：两端全是字符串，比较字典顺序
   - 特殊情况2：两端存在`NaN`，一定是`false`

```js
// 1
console.log(null > undefined)	// false 等价于 0 > NaN
// 2
console.log(null == undefined)	// false 等价于 0 > NaN
```

2. `==`的运算

   - 一般规则：

     - 两端类型相同，比较值

     - 两端都是原始类型，转成数字比较

     - 一端是原始类型，一端是对象类型，把对象转成原始类型后比较

   - 特殊情况1：`undefined`和`null`只有与自身比较或者相互比较时，才会返回`true`

   ``` js
   null == 0				// false
   undefined == 2			// false
   undefined == null		// true
   undefined == undefined	// true
   null == null			// true
   ```

   - 特殊情况2：两端存在`Nan`，一定返回`false`

3. `===`的运算
   - 一般规则：类型和值都必须相同
   - 特殊情况：两端存在`NaN`，一定返回`false`

### 逻辑运算

> `! && ||`和`?:`

1. `x && y`
   - `x`为`false`返回`x`
   - `x`为`true`返回`y`
2. `x || y`
   - `x`为`false`返回`y`
   - `x`为`true`返回`x`

### 位运算

1. 按位与(`&`)：将两个操作数的每一位进行与操作，只有两个操作数对应位都为 1 时结果位才为 1。
2. 按位或(`|`)：将两个操作数的每一位进行或操作，只要两个操作数对应位中有一个为 1，结果位就为 1。
3. 按位异或(`^`)：将两个操作数的每一位进行异或操作，如果两个操作数对应位不同，则结果位为 1，否则为 0。
4. 按位取反(`~`)：对操作数的每一位进行取反操作，即将 0 变为 1，将 1 变为 0。
5. 左移(`<<`)：将操作数的所有位向左移动指定的位数，右侧空出的位用 0 填充。
6. 右移(`>>`)：将操作数的所有位向右移动指定的位数，左侧空出的位用原来的符号位填充(对于正数，填充 0；对于负数，填充 1)。
7. 无符号右移(`>>>`)：将操作数的所有位向右移动指定的位数，左侧空出的位总是用 0 填充。

## JavaScript 数组实例方法

### `push()`

- 描述：向数组的末尾添加一个或多个元素，并返回新的长度。
- 示例：
  ```javascript
  const array = [1, 2, 3];
  const length = array.push(4, 5);
  console.log(array); // [1, 2, 3, 4, 5]
  console.log(length); // 5
  ```

### `pop()`

- 描述：删除并返回数组的最后一个元素。
- 示例：
  ```javascript
  const array = [1, 2, 3];
  const lastElement = array.pop();
  console.log(array); // [1, 2]
  console.log(lastElement); // 3
  ```

### `shift()`

- 描述：删除并返回数组的第一个元素。
- 示例：
  ```javascript
  const array = [1, 2, 3];
  const firstElement = array.shift();
  console.log(array); // [2, 3]
  console.log(firstElement); // 1
  ```

### `unshift()`

- 描述：向数组的开头添加一个或多个元素，并返回新的长度。
- 示例：
  ```javascript
  const array = [2, 3];
  const length = array.unshift(0, 1);
  console.log(array); // [0, 1, 2, 3]
  console.log(length); // 4
  ```

### `splice()`

- 描述：从数组中添加或删除元素。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  array.splice(2, 1, 'a', 'b');
  console.log(array); // [1, 2, "a", "b", 4, 5]
  ```

### `slice()`

- 描述：返回数组的一部分，不会改变原数组。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const newArray = array.slice(1, 3);
  console.log(newArray); // [2, 3]
  ```

### `concat()`

- 描述：用于连接两个或多个数组。
- 示例：
  ```javascript
  const array1 = [1, 2];
  const array2 = [3, 4];
  const newArray = array1.concat(array2);
  console.log(newArray); // [1, 2, 3, 4]
  ```

### `forEach()`

- 描述：对数组的每个元素执行一次提供的函数。
- 示例：
  ```javascript
  const array = [1, 2, 3];
  array.forEach(element => console.log(element));
  // 输出:
  // 1
  // 2
  // 3
  ```

### `map()`

- 描述：创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。
- 示例：
  ```javascript
  const array = [1, 2, 3];
  const newArray = array.map(element => element * 2);
  console.log(newArray); // [2, 4, 6]
  ```

### `filter()`

- 描述：创建一个新数组，包含通过所提供函数实现的测试的所有元素。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const newArray = array.filter(element => element % 2 === 0);
  console.log(newArray); // [2, 4]
  ```

### `reduce()`

- 描述：对数组中的每个元素执行一个由您提供的 reducer 函数(升序执行)，将其结果汇总为单个返回值。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const sum = array.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
  console.log(sum); // 15
  ```

### `find()`

- 描述：返回数组中满足提供的测试函数的第一个元素的值。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const found = array.find(element => element > 2);
  console.log(found); // 3
  ```

### `indexOf()`

- 描述：返回数组中第一个找到的元素索引，如果不存在则返回 -1。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const index = array.indexOf(3);
  console.log(index); // 2
  ```

### `includes()`

- 描述：如果数组中存在某个元素，则返回 true，否则返回 false。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const includesThree = array.includes(3);
  console.log(includesThree); // true
  ```

### `some()`

- 描述：检测数组中的元素是否有满足提供的测试函数。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const hasEven = array.some(element => element % 2 === 0);
  console.log(hasEven); // true
  ```

### `every()`

- 描述：检测数组中的所有元素是否都满足提供的测试函数。
- 示例：
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const allEven = array.every(element => element % 2 === 0);
  console.log(allEven); // false
  ```

### `join()`

- 描述：将数组的所有元素连接成一个字符串。
- 示例：
  ```js
  const array = ['Hello', 'world', '!'];
  const joinedString = array.join(' ');
  console.log(joinedString); // "Hello world !"
  ```

### `reverse()`

- 描述：颠倒数组中元素的顺序。
- 示例：
  ```js
  const array = [1, 2, 3];
  array.reverse();
  console.log(array); // [3, 2, 1]
  ```

### `sort()`

- 描述：对数组的元素进行排序。

- 示例：

  ```js
  const array = [3, 1, 2];
  array.sort();
  console.log(array); // [1, 2, 3]
  ```

### `fill()`

- 描述：使用一个固定值填充数组中从起始索引到终止索引内的全部元素。

- 示例：

  ```js
  const array = [1, 2, 3, 4, 5];
  array.fill(0, 1, 3);
  console.log(array); // [1, 0, 0, 4, 5]
  ```

### `findIndex()`

- 描述：返回数组中满足提供的测试函数的第一个元素的索引，如果不存在则返回 -1。

- 示例：
  ```js
  const array = [1, 2, 3, 4, 5];
  const index = array.findIndex(element => element > 2);
  console.log(index); // 2
  ```

### `splice()`

- 描述：从数组中添加或删除元素。

- 示例：

  ```js
  const array = [1, 2, 3, 4, 5];
  array.splice(2, 1, 'a', 'b');
  console.log(array); // [1, 2, "a", "b", 4, 5]
  ```

### `toString()`

- 描述：返回一个字符串，表示指定的数组及其元素。

- 示例：

  ```js
  const array = [1, 2, 3];
  const string = array.toString();
  console.log(string); // "1,2,3"
  ```

### `toString()`

- 描述：返回一个字符串，表示指定的数组及其元素。

- 示例：

  ```js
  const array = [1, 2, 3];
  const string = array.toString();
  console.log(string); // "1,2,3"
  ```

### `toLocaleString()`

- 描述：返回一个字符串表示数组中的元素。该字符串由数组中的每个元素的 toLocaleString() 返回值经调用 join() 方法连接（由逗号分隔）组成。

- 示例：

  ```js
  const array = [new Date(), 'apple', 'banana'];
  const string = array.toLocaleString();
  console.log(string); // "4/4/2024, 12:00:00 AM,apple,banana"
  ```

### `flat()`

- 描述：将所有子数组的元素连接到一个新数组中。

- 示例：

  ```js
  const array = [1, [2, [3]]];
  const flatArray = array.flat();
  console.log(flatArray); // [1, 2, [3]]
  ```

### `flatMap()`

- 描述：首先使用映射函数映射每个元素，然后将结果压缩成一个新数组。

- 示例：

  ```js
  const array = [1, 2, 3];
  const mappedArray = array.flatMap(x => [x * 2]);
  console.log(mappedArray); // [2, 4, 6]
  ```

### `reduceRight()`

- 描述：从右向左执行数组的 reduce 方法。

- 示例：

  ```js
  const array = [1, 2, 3, 4];
  const sum = array.reduceRight((accumulator, currentValue) => accumulator + currentValue, 0);
  console.log(sum); // 10
  ```

### `keys()`

- 描述：返回一个数组迭代器，包含数组中每个索引的键。

- 示例：

  ```js
  const array = ['a', 'b', 'c'];
  const iterator = array.keys();
  for (const key of iterator) {
    console.log(key); // 0, 1, 2
  }
  ```

### `values()`

- 描述：返回一个新的 Array Iterator 对象，该对象包含数组每个索引处的值。

- 示例：

  ```js
  const array = ['a', 'b', 'c'];
  const iterator = array.values();
  for (const value of iterator) {
    console.log(value); // 'a', 'b', 'c'
  }
  ```

### `entries()`

- 描述：返回一个新的 Array Iterator 对象，该对象包含数组中每个索引的键/值对。

- 示例：

  ```js
  const array = ['a', 'b', 'c'];
  const iterator = array.entries();
  for (const entry of iterator) {
    console.log(entry); // [0, 'a'], [1, 'b'], [2, 'c']
  }
  ```

## 节流和防抖

> 在 JavaScript 中，"节流"（Throttling）和"防抖"（Debouncing）是两种常用的技术，用于控制函数执行的频率，特别是在处理高频事件（如窗口滚动、鼠标移动、键盘输入等）时。

### 节流（Throttling）

> 节流的基本思想是在一段时间内只执行一次函数，如果在这段时间内再次触发事件，则不会执行函数。例如，如果你设置了一个每 100 毫秒执行一次的节流函数，那么在这 100 毫秒内，无论触发多少次事件，该函数都只会执行一次。

以下是一个简单的节流函数的实现：

```js
function throttle(func, delay) {  
  let lastCall = 0;  
  return function(...args) {  
    const now = new Date().getTime();  
    if (now - lastCall < delay) {  
      return;  
    }  
    lastCall = now;  
    return func.apply(this, args);  
  };  
}
```

### 防抖（Debouncing）

防抖的基本思想是在一段时间内，事件处理函数只执行一次，如果在这个时间内又触发了这个事件，则重新计算执行时间。也就是说，如果一个事件被频繁触发，那么只有最后一次触发的事件会执行函数。

以下是一个简单的防抖函数的实现：

```javascript
function debounce(func, delay) {  
  let timeout;  
  return function(...args) {  
    const context = this;  
    clearTimeout(timeout);  
    timeout = setTimeout(function() {  
      func.apply(context, args);  
    }, delay);  
  };  
}
```

### 使用场景

- **节流**：适用于那些<u>需要频繁触发</u>，<u>但不需要立即执行</u>的场景，如`滚动加载`、`窗口大小调整`等。通过节流，我们可以限制函数的执行频率，提高性能。
- **防抖**：适用于那些<u>需要频繁触发</u>，但<u>只需要在最后一次触发</u>后执行的场景，如`输入框实时搜索`、`按钮点击防重复提交`等。通过防抖，我们可以确保函数只在最后一次触发后执行，避免不必要的计算或操作。

这两种技术都是优化高频事件处理的有效手段，在实际开发中可以根据具体需求选择使用。

## 实时监听元素在视口的可见性

### Intersection Observer API

1. **创建 Intersection Observer 实例：**

   首先，创建一个 `Intersection Observer` 实例，并指定要观察的目标元素及其选项。

   ```js
   const observer = new IntersectionObserver(callback, options);
   ```

   - `callback` 是一个回调函数，当目标元素的可见性变化时被调用。
   - `options` 是一个配置对象，可以指定观察器的选项，比如观察器的根元素、观察器的阈值等。
     - `root`（根元素）：
       - 描述：指定一个祖先元素，*`作为视口区域`*。默认为 `null`，表示整个文档的视口。
       - 值：可以是一个 DOM 元素，也可以是 `null`。
     - `rootMargin`（根元素边距）：
       - 描述：用于扩展或缩小<u>根元素的边界框</u>。
       - 值：可以是一个指定边距的字符串，比如`"10px 20px 30px 40px"`，也可以是一个表示四个方向的数组 `[top, right, bottom, left]`，比如 `[10, 20, 30, 40]`，单位为像素。
     - `threshold`（阈值）：
       - 描述：一个或多个观察目标的交叉区域与根元素的交叉区域的比例，当交叉区域的比例达到或超过阈值时，触发回调函数。
       - 值：可以是一个单个数字或一个数字数组。每个数字表示目标元素的可见部分占根元素的可见部分的比例。
         - 例如，如果你想要观察目标元素至少 50% 可见时触发回调函数，可以将 `threshold` 设置为 `0.5`。

2. **观察目标元素：**

   将要观察的目标元素传递给 `Intersection Observer` 实例的 `observe` 方法。

   ```js
   observer.observe(targetElement);
   ```

3. **处理可见性变化的回调函数：**

   在回调函数中处理目标元素的可见性变化。

   ```js
   onst callback = (entries, observer) => {
     entries.forEach(entry => {
       // 处理可见性变化
       if (entry.isIntersecting) {
         // 元素进入视口
         console.log('Element is visible');
       } else {
         // 元素离开视口
         console.log('Element is not visible');
       }
     });
   };
   ```

4. **优化性能：**

   - 使用合适的根元素：如果目标元素位于另一个容器中，可以指定合适的根元素来提高性能。
   - 使用合适的阈值：根据实际需求设置合适的阈值，以便更精确地确定元素的可见性。
   - 批量处理：如果有大量目标元素，可以批量处理可见性变化，而不是每个元素单独处理。

## JavaScript 注释规范化

- 参考文档

  - [关于 JavaScript 之注释规范化（JSDoc）](https://knightyun.github.io/2020/03/13/js-comment-format)
  - [在 Javascript 文件里添加 JSDoc 注释](https://juejin.cn/post/6995851218543181854)

- 用 @typedef 描述自定义的变量类型

  ```js
  /**
   * 关于自定义类型的描述
   * @typedef {(string|number)} myType
   */
  
  /**
   * 关于自定义类型的描述
   * @type {myType} val - 使用自定义的类型
   */
  
  function myFn(val) {}
  ```

- 用 @typedef 和 @property 定义一个对象及其属性的类型

  ```js
  /**
   * @typedef {object} SpecialType1 - creates a new type named 'SpecialType1'
   * @property {string} prop1 - a string property of SpecialType1
   * @property {number} prop2 - a number property of SpecialType1
   * @property {number=} prop3 - an optional number property of SpecialType1
   */
  /** @type {SpecialType1} */
  var specialTypeObject1;
  ```



# Typescript 相关

## tsconfig.ts 文件的配置说明

```json
{
  "extends": "@vue/tsconfig/tsconfig.dom.json",
  "include": ["env.d.ts", "src/**/*", "src/**/*.vue"],
  "exclude": ["src/**/__tests__/*","node_modules","dist","**/*.js"],
  "compilerOptions": {
    "strict": true,
    /* 目标编译版本为最新的ECMAScript规范 */
    "target": "ESNext",
    /* 设置模块的编译方式，为ES6 */
    "module": "ESNext",
    /* 设置模块的解析方式为node */
    "moduleResolution": "node",
    /* 强制文件名称大小写值一致 */
    "forceConsistentCasingInFileNames": true,
    /* 编译是否包含默认库文件 */
    "noLib": false,
    /* 允许从没有默认导出的文件中导入模块 */
    "allowSyntheticDefaultImports": true,
    /* 是否启用严格的函数类型检查 */
    "strictFunctionTypes": false,
    /* 设置jsx的语法处理方式为保留原样 */
    "jsx": "preserve",
    /* 允许使用js */
    "allowJs": true,
    /* 是否生成映射文件 */
    "sourceMap": true,
    /* 启用ES模块与非ES模块的转换 */
    "esModuleInterop": true,
    /* 允许导入json模块 */
    "resolveJsonModule": true,
    /* 禁止未使用的局部变量 */
    "noUnusedLocals": true,
    /* 禁止未使用的函数参数 */
    "noUnusedParameters": true,
    /* 是否启用实验性的装饰语法 */
    "experimentalDecorators": true,
    /* 项目依赖的库 */
    "lib": ["dom", "esnext"],
    /* 是否允许隐式的any类型 */
    "noImplicitAny": false,
    /* 是否跳过对类型声明文件的类型检查 */
    "skipLibCheck": true,
    /* 是否移除代码中的注释 */
    "removeComments": true,
    /* 包含的额外类型声明文件 */
    "types": ["vite/client"],
    /* 是否启用typescript的composite编译模式，增量编译，加快编译速度 */
    "composite": true,
    /* 指定ts构建生成的依赖文件存储路径 */
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.app.tsbuildinfo",
    /* 项目的根目录，相对path路径 */
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}

```



# Vue 相关

## 路由

> 参考: [Vue Router (vuejs.org)](https://v3.router.vuejs.org/zh/)

### routes的配置

- 类型: `Array<RouteConfig>`

  `RouteConfig` 的类型定义：

  ```ts
  interface RouteConfig = {
    path: string, // 路由路径
    component?: Component,
    name?: string, // 命名路由
    components?: { [name: string]: Component }, // 命名视图组件
    redirect?: string | Location | Function, // 重定向
    props?: boolean | Object | Function,
    alias?: string | Array<string>,
    children?: Array<RouteConfig>, // 嵌套路由
    beforeEnter?: (to: Route, from: Route, next: Function) => void,
    meta?: any,// 元信息
  
    // 2.6.0+
    caseSensitive?: boolean, // 匹配规则是否大小写敏感？(默认值：false)
    pathToRegexpOptions?: Object // 编译正则的选项
  }
  ```



### 在路由实例创建后添加新的路由配置项

```js
import VueRouter from "vue-router";
const router = new VueRouter({...}) //假设此时创建了一个路由实例router
// 添加新的路由配置项
router.addRoute({
   path:'/target',
   name:'target'
})
```

### 重置路由

> [参考](https://blog.csdn.net/qq_42991509/article/details/91971948)

```js
const createRouter = () =>
   new VueRouter({
      mode: "history",
      base: process.env.BASE_URL,
      routes,
   });
// 创建路由实例
const router = createRouter();
// 路由重置函数
export function resetRouter() {
   const newRouter = createRouter();
   // 这一行是关键。新创建的 newRouter 实例的 matcher 属性赋值给全局 router 实例的 matcher 属性。在 Vue Router 中，matcher 是一个内部对象，它负责将 URL 路径映射到对应的路由记录。通过替换 router 的 matcher，实际上是替换了路由匹配逻辑，这相当于重置了路由配置。
   router.matcher = newRouter.matcher;
}
```

## 关于 vue2 props 定义

- 可通过在 type 中以数组形式来定义联合类型,如:`type: [String,Number]`

```js
props: {
   name: {
      type: [String,Number],
      required: true
   },
}
```

## Vue页面跳转后位置不在顶部的解决办法

- 场景：使用vue-router组件，进行页面切换，切换后的页面滚动条还停留在上一级页面的位置，没有置顶。

- 需求：每次跳转新页面时，都置顶显示。

- 解决方案：
  在vue的router目录下的`router/index.js`文件中进行配置：

```js
export default new Router({
  routes: [
    {
      path: '/',
      name: 'Index',
      component: Index 
    }
  ],
  scrollBehavior (to, from, savedPosition) {       //添加该方法
    return { x: 0, y: 0}
  }
})
```

`scrollBehavior` 方法接收 `to` 和 `from` 路由对象。第三个参数 `savedPosition` 当且仅当 `popstate` 导航 (通过浏览器的 前进/后退 按钮触发) 时才可用。

这个方法返回滚动位置的对象信息，长这样：

- `{ x: number, y: number }`
- `{ selector: string, offset? : { x: number, y: number }}` (offset 只在 2.6.0+ 支持)

参考：[Vue Router](https://link.juejin.cn/?target=https%3A%2F%2Frouter.vuejs.org%2Fzh%2F) 滚动行为，官方文档：[滚动行为 | Vue Router (vuejs.org)](https://v3.router.vuejs.org/zh/guide/advanced/scroll-behavior.html#异步滚动)

> 上图红框的s部分，为新增内容配置以后，每次页面切换都会保持置顶。

> [!note]
>
> 以上设置在vue-router模式是`history`下没什么问题。如果在hash模式下，且vue-router的版本为4+，那么返回对象的x，y就要分别修改为left，top。

## Vuex 持久化

> `Vuex`是在中大型项目中必不可少的状态管理组件，刷新会重新更新状态，但是有时候我们并不希望如此。例如全局相关的，如登录状态、`token`、以及一些不常更新的状态等，我们更希望能够固化到本地，减少无用的接口访问，以及更佳的用户体验。
>
> 页面刷新后，想保存页面未保存的数据。我们总是习惯于放在浏览器的`sessionStorage`、`localStorage`、`cookie`中。但是用了`vue`后，`vuex`便可以被应用了。

- **vuex优势：** 相比sessionStorage，存储数据更安全，sessionStorage可以在控制台被看到。
- **vuex劣势：** 在F5刷新页面后，vuex会重新更新state，所以，存储的数据会丢失。

### 手动利用HTML5的本地存储

> `vuex`的`state`在`localStorage`或`sessionStorage`或其它存储方式中取值 在`mutations`定义的方法里对`vuex`的状态操作的同时对存储也做对应的操作。这样`state`就会和存储一起存在并且与`vuex`同步
> **问题:最直观的就是，手动写比较麻烦**

### 利用*`vuex-persistedstate`*插件

> [!note]
>
> `vuex`可以进行全局的状态管理，但刷新后刷新后数据会消失，这是我们不愿意看到的。怎么解决呢，我们可以结合本地存储做到数据持久化，也可以通过插件*`vuex-persistedstate`*
>
> 插件的原理其实也是结合了存储方式,只是统一的配置就不需要手动每次都写存储方法

#### 安装



```bash
npm install vuex-persistedstate --save
// 或
npm i -S vuex-persistedstate
```

#### 配置使用

在vuex初始化时候，作为组件引入



```js
// 在store下的index.js中
import persistedState from 'vuex-persistedstate'
export default new Vuex.Store({
    // ...
    plugins: [persistedState()]
})
```

**vuex-persistedstate默认使用localStorage来固化数据（默认存储于localStorage）**

- 存储sessionStorage的情况（safari的无痕浏览模式）



```js
import createPersistedState from "vuex-persistedstate"
const store = new Vuex.Store({
  // ...
  plugins: [
    createPersistedState({
      storage: window.sessionStorage
    })
  ]
})
```

- 存储cookie的情况



```js
import persistedState from 'vuex-persistedstate'
import * as Cookies from 'js-cookie'

export default new Vuex.Store({
  // ...
  plugins: [
    persistedState({
      storage: {
        getItem: key => Cookies.get(key),
        setItem: (key, value) => Cookies.set(key, value, { 
          expires: 7 
        }),
        removeItem: key => Cookies.remove(key)
      }
    })
  ]
})
```

**默认持久化所有state**

#### 指定需要持久化的state,配置如下



```js
import createPersistedState from "vuex-persistedstate"
const store = new Vuex.Store({
  // ...
  plugins: [
    createPersistedState({
      storage: window.sessionStorage,
      reducer(val) {
        return {
          // 只储存state中的assessmentData
          assessmentData: val.assessmentData
        }
      }
     })
  ]
})
// vuex引用多个插件的写法
```

譬如：vuex提示的插件和持久化的插件一起使用，配置如下



```js
import createPersistedState from "vuex-persistedstate"
import createLogger from 'vuex/dist/logger'

// 判断环境 vuex提示生产环境中不使用
const debug = process.env.NODE_ENV !== 'production'
const createPersisted = createPersistedState({
  storage: window.sessionStorage
})

export default new Vuex.Store({
  // ...
  plugins: debug ? [
    createLogger(), 
    createPersisted
  ] : [
    createPersisted
  ]
})
// plugins要是一个一维数组不然会解析错误
```

#### API

**createPersistedState([options])使用给定的选项创建插件的新实例。可以提供以下选项来配置您的特定需求的插件：**

- `key ：` 存储持久状态的键。
  默认：`vuex`
- `paths ：` 部分持续状态的任何路径的数组。如果没有路径给出，完整的状态是持久的。
  默认：`[]`
- `reducer ：` 一个函数，将被调用来基于给定的路径持久化的状态。
  默认：都包含这些值
- `subscriber ：` 一个被调用来设置突变订阅的函数。
  默认：`store => handler => store.subscribe(handler)`
- `storage ：` 而不是（或与）getState和setState。
  默认：`localStorage`
- `getState ：` 将被调用以重新水化先前持久状态的函数。
  默认：`storage`
- `setState ：` 将被调用来保持给定状态的函数。
  默认：`storage`
- `filter ：` 将被调用来过滤将setState最终触发存储的任何突变的函数。
  默认：`() => true`

# Vue项目的创建

## 使用`vue-cli`创建

> 参考：[Home | Vue CLI (vuejs.org)](https://cli.vuejs.org/zh/#起步)
>
> CLI 服务是构建于 [webpack](http://webpack.js.org/) 和 [webpack-dev-server](https://github.com/webpack/webpack-dev-server) 之上的它。包含了：
>
> - 加载其它 CLI 插件的核心服务；
> - 一个针对绝大部分应用优化过的内部的 webpack 配置；
> - 项目内部的 `vue-cli-service` 命令，提供 `serve`、`build` 和 `inspect` 命令。

### 安装

```bash
# 全局安装 vue/cli
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

### 创建项目

```bash
vue create my-project # 普通创建方式
# OR
vue ui # 带ui的创建方式
```

### `vue-cli`的一些设置

#### 代理设置[^配置参考]

##### [devServer.proxy](https://cli.vuejs.org/zh/config/#devserver)

- Type: `string | Object`

  如果你的前端应用和后端 API 服务器没有运行在同一个主机上，你需要在开发环境下将 API 请求代理到 API 服务器。这个问题可以通过 `vue.config.js` 中的 `devServer.proxy` 选项来配置。

  `devServer.proxy` 可以是一个指向开发环境 API 服务器的字符串：

  ```js
  // vue.config.js
  module.exports = {
    devServer: {
      proxy: 'http://localhost:4000'
    }
  }
  ```

  这会告诉开发服务器将任何未知请求 (没有匹配到静态文件的请求) 代理到`http://localhost:4000`。

  如果你想要更多的代理控制行为，也可以使用一个 `path: options` 成对的对象。完整的选项可以查阅 [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware#proxycontext-config) 。

  ```js
  // vue.config.js
  module.exports = {
    devServer: {
      proxy: {
        '/api': {
          target: '<url>',
          ws: true,
          changeOrigin: true
        },
        '/foo': {
          target: '<other_url>'
        }
      }
    }
  }
  ```

[^配置参考]: [配置参考 | Vue CLI (vuejs.org)](https://cli.vuejs.org/zh/config/#devserver-proxy)↩

## 使用`vite`创建

> [Vite | 下一代的前端工具链 (vitejs.dev)](https://cn.vitejs.dev/)
>
> **兼容性注意**：Vite 需要 [Node.js](https://nodejs.org/en/) 版本 18+，20+。然而，有些模板需要依赖更高的 Node 版本才能正常运行，当你的包管理器发出警告时，请注意升级你的 Node 版本。

### 直接创建

控制台输入下面其中一条的指令后按照提示操作

```bash
# 直接创建
npm create vite@latest
# OR
yarn create vite
```

还可以通过附加的命令行选项直接指定项目名称和你想要使用的模板。例如，要构建一个 Vite + Vue 项目，运行:

```bash
# 使用vite模板创建
# npm 7+, 需要额外的双破折号
npm create vite@latest my-vue-app -- --template vue

# yarn
yarn create vite my-vue-app --template vue

# pnpm
pnpm create vite my-vue-app --template vue

# bun
bun create vite my-vue-app --template vue
```

查看 [create-vite](https://github.com/vitejs/vite/tree/main/packages/create-vite) 以获取每个模板的更多细节：`vanilla`，`vanilla-ts`, `vue`, `vue-ts`，`react`，`react-ts`，`react-swc`，`react-swc-ts`，`preact`，`preact-ts`，`lit`，`lit-ts`，`svelte`，`svelte-ts`，`solid`，`solid-ts`，`qwik`，`qwik-ts`。

### 命令行界面

在安装了 Vite 的项目中，可以在 npm scripts 中使用 `vite` 可执行文件，或者直接使用 `npx vite` 运行它。下面是通过脚手架创建的 Vite 项目中默认的 npm scripts：

```json
// package.json
{
  "scripts": {
    "dev": "vite", // 启动开发服务器，别名：`vite dev`，`vite serve`
    "build": "vite build", // 为生产环境构建产物
    "preview": "vite preview" // 本地预览生产构建产物
  }
}
```

可以指定额外的命令行选项，如 `--port` 或 `--open`。运行 `npx vite --help` 获得完整的命令行选项列表。

查看 [命令行界面](https://cn.vitejs.dev/guide/cli.html) 了解更多细节。

### 使用插件

#### 添加一个插件

若要使用一个插件，需要将它添加到项目的 `devDependencies` 并在 `vite.config.js` 配置文件中的 `plugins` 数组中引入它。例如，要想为传统浏览器提供支持，可以按下面这样使用官方插件 [@vitejs/plugin-legacy](https://github.com/vitejs/vite/tree/main/packages/plugin-legacy)：

```bash
npm add -D @vitejs/plugin-legacy
```

```typescript
// vite.config.js
import legacy from '@vitejs/plugin-legacy'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [
    legacy({
      targets: ['defaults', 'not IE 11'],
    }),
  ],
})
```

`plugins` 也可以接受包含多个插件作为单个元素的预设。这对于使用多个插件实现的复杂特性（如框架集成）很有用。该数组将在内部被扁平化。

#### 按需应用

默认情况下插件在开发 (serve) 和生产 (build) 模式中都会调用。如果插件在服务或构建期间按需使用，请使用 `apply` 属性指明它们仅在 `'build'` 或 `'serve'` 模式时调用：

```js
// vite.config.js
import typescript2 from 'rollup-plugin-typescript2'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [
    {
      ...typescript2(),
      apply: 'build',
    },
  ],
})
```

## 使用`vue3`官方的`vite`脚手架创建

> [!tip]
>
> 官方文档：[快速上手 | Vue.js (vuejs.org)](https://cn.vuejs.org/guide/quick-start.html)，[工具链 | Vue.js (vuejs.org)](https://cn.vuejs.org/guide/scaling-up/tooling.html)

```bash
yarn create vue@latest
# 实测上面的指令可能会报错，如果报错就执行下面这条指令
yarn create vue
```

这个命令会安装和执行 [create-vue](https://github.com/vuejs/create-vue)，它是 Vue 提供的官方脚手架工具。跟随命令行的提示继续操作即可。

- 要学习更多关于 Vite 的知识，请查看 [Vite 官方文档](https://cn.vitejs.dev/)。
- 若要了解如何为一个 Vite 项目配置 Vue 相关的特殊行为，比如向 Vue 编译器传递相关选项，请查看 [@vitejs/plugin-vue](https://github.com/vitejs/vite-plugin-vue/tree/main/packages/plugin-vue#readme) 的文档。



## 基于vite+vue3的油猴项目

> 参考：[vite-plugin-monkey](https://github.com/lisonge/vite-plugin-monkey/blob/main/README_zh.md)

### 创建

#### 直接创建

```bash
# 使用方式与 vite create 一致
pnpm create monkey
# npm create monkey
# yarn create monkey

# 然后根据提示进行创建
```

#### 项目中单独安装

```bash
pnpm add -D vite-plugin-monkey
# npm i -D vite-plugin-monkey
# yarn add -D vite-plugin-monkey
```

## uni-app开发

### 使用Vscode进行开发(推荐)

![VSCode开发uni-app.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/28309fd5d44343bdb154011a82612a29~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

**简述一下**这个教程能给VSCode开发`	uni-app`带来的体验

- 增强`pages.json`和`manifest.json`开发体验（语法提示、颜色块、写注释）
- 一键创建页面、组件、分包
- 完善的`API`，组件，uni.scss 变量提示
- 条件编译注释高亮

可以说，VSCode开发`uni-app`的槽点基本上都解决了，有很多地方我觉得体验还更好。

#### 全局安装 vue-cli 3.x（如已安装请跳过此步骤）

```bash
npm install -g @vue/cli
```

#### 通过 CLI 创建 uni-app 项目

```bash
vue create -p dcloudio/uni-preset-vue my-project
```

此时，会提示选择项目模板，初次体验建议选择 `hello uni-app` 项目模板，如下所示：

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/1190eb9efa120f8db46d2aa81773a8a8.png)

#### 在vscode中打开项目

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/de61885dcd3ae03bc6ae15e33e47c296.png)

###### 安装vue语法提示插件vetur

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/f98722b481a8f8bdb29163a4d248926a.png)

###### CLI 工程默认带了uni-app语法提示和5+App语法提示

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/394176e4b2b955c02a218ed6495dfe22.png)

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/6ac9e35953217e3c5f4f85baebae5730.png)

#### 安装组件语法提示

组件语法提示是uni-app的亮点，其他框架很少能提供。

```bash
npm i @dcloudio/uni-helper-json
```

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/07c7a54cb9ea8f0567ec1b2b60cac0f3.png)

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/e82ee43b2d6a1494d796d06614a73326.png)

#### 导入 HBuilderX 自带的代码块

从 github 下载 [uni-app 代码块](https://github.com/zhetengbiji/uniapp-snippets-vscode)，放到项目目录下的 `.vscode` 目录即可拥有和 HBuilderX 一样的代码块。

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/d39d378c0821a67c8bf72c7965833378.png)

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/870c114c199a93beedac79a78dde5f02.png)

![img](https://img-cdn-tc.dcloud.net.cn/uploads/article/20190827/ff0d8b9c1edd6f002657d20021def9be.png)

#### 运行项目

```bash
npm run dev:%PLATFORM%
```

#### 发布项目

```bash
npm run build:%PLATFORM%
```

*`%PLATFORM%`* 可取值如下：

| 值         | 平台         |
| ---------- | ------------ |
| h5         | H5           |
| mp-alipay  | 支付宝小程序 |
| mp-baidu   | 百度小程序   |
| mp-weixin  | 微信小程序   |
| mp-toutiao | 头条小程序   |
| mp-qq      | qq 小程序    |



>[CLI 方式参考文档](https://uniapp.dcloud.io/quickstart?id=_2-通过vue-cli命令行)

### 使用Hbuilder X进行开发(不推荐)

# Vue项目打包成单HTML文件

## webpack的项目

### 安装插件

> [!tip]
>
> 教程参考：[Vue项目打包成单个HTML文件 - 掘金 (juejin.cn)](https://juejin.cn/post/7162367209438707743)
>
> 使用到的插件 `html-webpack-inline-plugin` 和 `html-webpack-plugin`

```bash
npm install --save -dev html-webpack-plugin
npm install --save -dev html-webpack-inline-plugin
```

### 更改路由引入方式

```js
// 由
{
    path: '/index',
    component: () => import('@/views/index/Index.vue')
}

// 更改为：
import Index from '@/views/index/Index.vue'

{
    path: '/index,
    component: Index
}
```

### 更改vue.config.js配置文件









# Vue2、Vue3对比

## css样式穿透

### Vue 2 的样式穿透写法

在 Vue 2 中，你可以使用 `>>>` 或 `/deep/` 来实现样式穿透。这两个选择器在功能上是一样的，但在不同的 CSS 预处理器中可能有不同的写法要求。

**示例：**

```vue
<style scoped>  
.parent >>> .child {  
  color: red;  
}  
</style>
```

或者

```vue
<style scoped>  
.parent /deep/ .child {  
  color: red;  
}  
</style>
```

### Vue 3 的样式穿透写法

写法1：

```vue
<style scoped>  
::v-deep .child {  
  color: red;  
}  
</style>
```

写法2：

```html
<style scoped>
.a :deep(.b) {
  /* ... */
}
</style>
```



### 注意事项

1. **兼容性**：`>>>` 和 `/deep/` 在一些 CSS 预处理器中可能不被支持，所以在使用时需要确认你的构建工具是否支持这些选择器。
2. **选择器的优先级**：穿透样式可能会受到其他样式规则的影响，因此确保你的选择器具有足够的优先级来覆盖其他样式。
3. **避免过度使用**：样式穿透可能会导致样式变得难以管理和维护，因此应尽量避免在大型项目中过度使用。
4. **CSS Modules 和其他解决方案**：除了使用样式穿透外，你还可以考虑使用 CSS Modules 或其他样式解决方案来更好地组织和管理你的样式。

## Vue3中css的`v-bind()`

> 参考：[单文件组件 CSS 功能 | Vue.js (vuejs.org)](https://cn.vuejs.org/api/sfc-css-features.html#v-bind-in-css)

单文件组件的 `<style>` 标签支持使用 `v-bind` CSS 函数将 CSS 的值链接到动态的组件状态：

```vue
<template>
  <div class="text">hello</div>
</template>

<script>
export default {
  data() {
    return {
      color: 'red'
    }
  }
}
</script>

<style>
.text {
  color: v-bind(color);
}
</style>
```

这个语法同样也适用于 [`<script setup>`](https://cn.vuejs.org/api/sfc-script-setup.html)，且支持 JavaScript 表达式 (需要用引号包裹起来)：

```vue
<script setup>
const theme = {
  color: 'red'
}
</script>

<template>
  <p>hello</p>
</template>

<style scoped>
p {
  color: v-bind('theme.color');
}
</style>
```

实际的值会被编译成哈希化的 CSS 自定义属性，因此 CSS 本身仍然是静态的。自定义属性会通过内联样式的方式应用到组件的根元素上，并且在源值变更的时候响应式地更新。

## 自定义组件的v-model

### Vue2中[^自定义组件的-v-model]

> 2.2.0+ 新增

一个组件上的 `v-model` 默认会利用名为 `value` 的 prop 和名为 `input` 的事件，但是像单选框、复选框等类型的输入控件可能会将 `value` attribute 用于[不同的目的](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox#Value)。`model` 选项可以用来避免这样的冲突：

```js
Vue.component('base-checkbox', {
  model: {
    prop: 'checked',
    event: 'change'
  },
  props: {
    checked: Boolean
  },
  template: `
    <input
      type="checkbox"
      v-bind:checked="checked"
      v-on:change="$emit('change', $event.target.checked)"
    >
  `
})
```

现在在这个组件上使用 `v-model` 的时候：

```vue
<base-checkbox v-model="lovingVue"></base-checkbox>
```

这里的 `lovingVue` 的值将会传入这个名为 `checked` 的 prop。同时当 `<base-checkbox>` 触发一个 `change` 事件并附带一个新的值的时候，这个 `lovingVue` 的 property 将会被更新。

注意你仍然需要在组件的 `props` 选项里声明 `checked` 这个 prop。

### Vue3中[^组件 v-model ]

`v-model` 可以在组件上使用以实现双向绑定。

首先让我们回忆一下 `v-model` 在原生元素上的用法：

```vue
<input v-model="searchText" />
```

在代码背后，模板编译器会对 `v-model` 进行更冗长的等价展开。因此上面的代码其实等价于下面这段：

```vue
<input
  :value="searchText"
  @input="searchText = $event.target.value"
/>
```

而当使用在一个组件上时，`v-model` 会被展开为如下的形式：

```vue
<CustomInput
  :model-value="searchText"
  @update:model-value="newValue => searchText = newValue"
/>
```

要让这个例子实际工作起来，`<CustomInput>` 组件内部需要做两件事：

1. 将内部原生 `<input>` 元素的 `value` attribute 绑定到 `modelValue` prop
2. 当原生的 `input` 事件触发时，触发一个携带了新值的 `update:modelValue` 自定义事件

这里是相应的代码：

```vue
<!-- CustomInput.vue -->
<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue']
}
</script>

<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>
```

现在 `v-model` 可以在这个组件上正常工作了：

```vue
<CustomInput v-model="searchText" />
```

另一种在组件内实现 `v-model` 的方式是使用一个可写的，同时具有 `getter` 和 `setter` 的 `computed` 属性。`get` 方法需返回 `modelValue` prop，而 `set` 方法需触发相应的事件：

```vue
<!-- CustomInput.vue -->
<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue'],
  computed: {
    value: {
      get() {
        return this.modelValue
      },
      set(value) {
        this.$emit('update:modelValue', value)
      }
    }
  }
}
</script>

<template>
  <input v-model="value" />
</template>
```



[^自定义组件的-v-model]:[自定义事件 — Vue.js (vuejs.org)](https://v2.cn.vuejs.org/v2/guide/components-custom-events.html#自定义组件的-v-model)
[^组件 v-model ]:[组件 v-model | Vue.js (vuejs.org)](https://cn.vuejs.org/guide/components/v-model.html)

# 在Vue项目中引入外部svg

## 在`template`中使用svg

### 方式一：使用 `require` 导入 SVG 文件

你可以使用 `require` 函数来导入外部 SVG 文件，然后在模板中直接使用它。

首先，确保你的项目中安装了 `vue-svg-loader` 或者 `svg-inline-loader`，以便能够正确加载 SVG 文件。

```bash
npm install --save-dev vue-svg-loader
```

然后，在你的 Vue 组件中，使用 `require` 导入 SVG 文件：

```vue
<template>
  <div>
    <!-- 这里是其他内容 -->
    <img src="./path/to/your-svg-file.svg" alt="SVG Image">
  </div>
</template>

<script>
export default {
  name: 'YourComponent',
  // 这里是组件的其它逻辑
}
</script>

<style scoped>
/* 这里是组件的样式 */
</style>
```

### 方式二：直接使用 `import` 导入 SVG 文件

你也可以使用 ES6 的 `import` 语法来导入 SVG 文件，然后在模板中使用它。

```vue
<template>
  <div>
    <!-- 这里是其他内容 -->
    <img :src="svgUrl" alt="SVG Image">
  </div>
</template>

<script>
import yourSvg from './path/to/your-svg-file.svg';

export default {
  name: 'YourComponent',
  data() {
    return {
      svgUrl: yourSvg,
    };
  },
  // 这里是组件的其它逻辑
}
</script>

<style scoped>
/* 这里是组件的样式 */
</style>
```

确保将 `'./path/to/your-svg-file.svg'` 替换为你 SVG 文件的实际路径。

## 在css中标签内使用svg

### 方式一：将 SVG 文件作为背景图使用

```css
/* 在 CSS 中使用 SVG 背景图 */
.div-with-svg {
  background-image: url('path/to/your/svg/file.svg');
  background-size: contain; /* 根据需要设置背景大小 */
  /* 其他样式 */
}
```

### 方式二：直接在 CSS 中插入 SVG 代码

```css
/* 在 CSS 中直接插入 SVG 代码 */
.svg-icon {
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M10 18a8 8 0 1 1 0-16 8 8 0 0 1 0 16zM10 2a6 6 0 1 0 0 12 6 6 0 0 0 0-12zM4 10a6 6 0 1 0 12 0 6 6 0 0 0-12 0z"/></svg>');
  background-size: contain; /* 根据需要设置背景大小 */
  /* 其他样式 */
}
```

# 一些Javascript库

## numeral.js数字格式化工具库

> 参考：[Numeral.js (numeraljs.com)](http://numeraljs.com/)

`numeral.js` 是一个专门用于格式化和操作数字的 JavaScript 库，可以帮助你轻松地完成这个任务。

首先，你需要在项目中安装 `numeral.js` 库。你可以通过 npm 或 yarn 进行安装：

```bash
npm install numeral
```

或者

```bash
yarn add numeral
```

安装完成后，你可以按照下面的方式使用 `numeral.js` 来格式化数字：

```js
// 引入 numeral.js
import numeral from 'numeral';

// 格式化数字为 "100万" 的字符串
function formatNumber(number) {
    return numeral(number).format('0.00a');
}

// 示例用法
const number = 1000000;
const formattedNumber = formatNumber(number); // 输出: "1.00M"
```

在这个示例中，`'0.00a'` 是 `numeral.js` 的格式化字符串，用于指定数字的格式。具体格式化字符串的含义可以参考 `numeral.js` 的文档。

## 时间处理库

### `day.js`[^Day.js中文网]

#### 安装

```bash
npm install dayjs
# 或
yarn add dayjs
```

#### 引入

```js
var dayjs = require("dayjs");
// import dayjs from 'dayjs' // ES 2015
dayjs().format();
```

#### 使用[^Day.js参考]

```js
/** 当前时间
 * 直接调用 dayjs() 将返回一个包含当前日期和时间的 Day.js 对象。
 * 等同于 dayjs(new Date()) 的调用
 */
var now = dayjs();

/** 字符串
 *  解析传入的 ISO 860 格式的字符串并返回一个 Day.js 对象实例。
 */
dayjs("2018-04-04T16:00:00.000Z");

/** 字符串+格式
 * 如果想解析包含本地化语言的日期字符串，可以传入第三个参数。
 */
require("dayjs/locale/zh-cn");
dayjs("2018 三月 15", "YYYY MMMM DD", "zh-cn");
/** 字符串+格式
 * 如果不知道输入字符串的确切格式，但知道它可能是几种中的一种，可以使用数组传入多个格式。
 */
dayjs("12-25-2001", ["YYYY", "YYYY-MM-DD"], "es", true);
/** 格式化 */
dayjs("2018-04-04T16:00:00.000Z").format("YYYY-MM-DD"); // 2018-04-04

```

#### 解析占位符

| 输入 | 示例             | 描述                    |
| :--- | :--------------- | :---------------------- |
| YY   | 18               | 两位数的年份            |
| YYYY | 2018             | 四位数的年份            |
| M    | 1-12             | 月份，从 1 开始         |
| MM   | 01-12            | 月份，两位数            |
| MMM  | Jan-Dec          | 缩写的月份名称          |
| MMMM | January-December | 完整的月份名称          |
| D    | 1-31             | 月份里的一天            |
| DD   | 01-31            | 月份里的一天，两位数    |
| H    | 0-23             | 小时                    |
| HH   | 00-23            | 小时，两位数            |
| h    | 1-12             | 小时, 12 小时制         |
| hh   | 01-12            | 小时, 12 小时制, 两位数 |
| m    | 0-59             | 分钟                    |
| mm   | 00-59            | 分钟，两位数            |
| s    | 0-59             | 秒                      |
| ss   | 00-59            | 秒，两位数              |
| S    | 0-9              | 毫秒，一位数            |
| SS   | 00-99            | 毫秒，两位数            |
| SSS  | 000-999          | 毫秒，三位数            |
| Z    | -05:00           | UTC 的偏移量            |
| ZZ   | -0500            | UTC 的偏移量，两位数    |
| A    | AM / PM          | 上午 下午 大写          |
| a    | am / pm          | 上午 下午 小写          |
| Do   | 1st... 31st      | 带序数词的月份里的一天  |
| X    | 1410715640.579   | Unix 时间戳             |
| x    | 1410715640579    | Unix 时间戳             |

#### 格式化占位符

| 标识 | 示例             | 描述                                                         |
| :--- | :--------------- | :----------------------------------------------------------- |
| YY   | 18               | 年，两位数                                                   |
| YYYY | 2018             | 年，四位数                                                   |
| M    | 1-12             | 月，从1开始                                                  |
| MM   | 01-12            | 月，两位数                                                   |
| MMM  | Jan-Dec          | 月，英文缩写                                                 |
| MMMM | January-December | 月，英文全称                                                 |
| D    | 1-31             | 日                                                           |
| DD   | 01-31            | 日，两位数                                                   |
| d    | 0-6              | 一周中的一天，星期天是 0                                     |
| dd   | Su-Sa            | 最简写的星期几                                               |
| ddd  | Sun-Sat          | 简写的星期几                                                 |
| dddd | Sunday-Saturday  | 星期几，英文全称                                             |
| H    | 0-23             | 小时                                                         |
| HH   | 00-23            | 小时，两位数                                                 |
| h    | 1-12             | 小时, 12 小时制                                              |
| hh   | 01-12            | 小时, 12 小时制, 两位数                                      |
| m    | 0-59             | 分钟                                                         |
| mm   | 00-59            | 分钟，两位数                                                 |
| s    | 0-59             | 秒                                                           |
| ss   | 00-59            | 秒，两位数                                                   |
| S    | 0-9              | 毫秒（十），一位数                                           |
| SS   | 00-99            | 毫秒（百），两位数                                           |
| SSS  | 000-999          | 毫秒，三位数                                                 |
| Z    | -05:00           | UTC 的偏移量，±HH:mm                                         |
| ZZ   | -0500            | UTC 的偏移量，±HHmm                                          |
| A    | AM / PM          | 上/下午，大写                                                |
| a    | am / pm          | 上/下午，小写                                                |
| Do   | 1st... 31st      | 月份的日期与序号                                             |
| ...  | ...              | 其他格式 ( 依赖 [AdvancedFormat](https://dayjs.fenxianglu.cn/category/plugin.html#advancedformat) 插件 ) |

## `Device.js`检测设备平台信息的js库

> [!tip]
>
> device.js是一个可以用来检测设备的平台、操作系统和方向的JavaScript库。device.js 通过操作系统（比如 iOS，安卓，黑莓，Windows，Firefox OX），方向（横屏或者竖屏），类型（平板或者移动设备），来为设备添加 CSS Class,并且它还提供了一些Javascript 函数用来判断设备。[github地址（有使用教程）](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Fmatthewhudson%2Fcurrent-device)

### 安装

```bash
npm install current-device
```

### main.js全局引入

```js
import device from "current-device"; // device.js 获取用户设备信息
```

### 使用

```ts
device.type // 当前设备类型
device.desktop() // 是否是桌面设备
device.mobile() //是否是移动端设备
device.android() // 是否是安卓设备
device.ios() // 是否是IOS设备
device.macos() // 是否是Macos设备
device.windows() // 是否是Windows设备
```



[^Day.js中文网]: [Day.js中文网 (fenxianglu.cn)](https://dayjs.fenxianglu.cn/)
[^Day.js参考]: [解析 | Day.js中文网 (fenxianglu.cn)](https://dayjs.fenxianglu.cn/category/parse.html) 、[Dayjs使用教程_npm 下载dayjs-CSDN博客](https://blog.csdn.net/xm1037782843/article/details/127981557)

## Lodash

> [!tip]
>
> 官网：[Lodash 简介 | Lodash中文文档 | Lodash中文网 (lodashjs.com)](https://www.lodashjs.com/)

### 安装和引入

###### 安装

```bash
npm i --save lodash
# 或
yarn add lodash
```

###### 引入

```js
// Node.js 环境下 (前端项目改用中使用import语句)
// 加载完整版本
var _ = require('lodash');
// 加载核心版本
var _ = require('lodash/core');
// 加载不可变自动柯里化 iteratee-first data-last 方法的 FP 构建。
var fp = require('lodash/fp');
 
// 加载方法类别
var array = require('lodash/array');
var object = require('lodash/fp/object');
 
// 针对较小的 browserify/rollup/webpack 包的 Cherry-pick 方法。
var at = require('lodash/at');
var curryN = require('lodash/fp/curryN');
```

> [!note]
>
> - 如需在 Node.js < 6 的 REPL 环境中使用 Lodash，请安装 [n_](https://www.npmjs.com/package/n_)。
>
> - 在Vue3 + Ts的项目中使用还需要安装 ts 声明文件库
>
>   ```bash
>   npm install @types/lodash -D
>   # 或
>   yarn add @types/lodash -D
>   ```
>
>   然后在tsconfig.ts中进行如下配置：
>
>   ```ts
>   {
>     "compilerOptions": {
>       "allowSyntheticDefaultImports": true
>     }
>   }
>   ```
>
>   最后重启vscode

# 一些Vue组件

## `Viewer.js` 图片预览库

> [!tip]
>
> 官网：[Viewer.js (fengyuanchen.github.io)](https://fengyuanchen.github.io/viewerjs/)
>
> 参考1:[Viewer.js用法说明-CSDN博客](https://blog.csdn.net/qq_41057885/article/details/118406684)
>
> 

### 安装

```bash
yarn add viewerjs
```

### 引入

```js
import Viewer from 'viewerjs';
import 'viewerjs/dist/viewer.css'; // 样式
```

### 使用

```js
const ViewerDom = document.getElementById('index'); // 获取容器元素
const viewer = new Viewer(ViewerDom, {
  // 配置
  button:false, //取消右上角关闭按钮
  movable:false //关闭图片移动
})
```

## `fancyapps/ui` 图片预览库

### 安装和引入

```bash
# Usage with NPM
npm install --save @fancyapps/ui

# and with Yarn
yarn add @fancyapps/ui
```

- 安装完成后，你可以将Fancybox作为ES模块引入:

```js
import { Fancybox } from "@fancyapps/ui";
import "@fancyapps/ui/dist/fancybox/fancybox.css";
```

### 使用

### 声明式用法

##### 准备元素

- 创建元素并添加 `data-fancybox` 属性。使用 `href` 或 `data-src` 属性指定要在Fancybox中显示的内容源。

- 可选地，使用 `data-caption` 属性在内容下显示标题

```html
<a href="image-a.jpeg" data-fancybox data-caption="Single image">
  <img src="thumbnail-a.jpeg" />
</a>
```

- 通过为多个元素添加相同的属性 `data-fancybox` 值，可以创建图库。你可以在每个图库中混合图像、视频和任何HTML内容。

```html
<a href="image-a.jpeg" data-fancybox="gallery" data-caption="Caption #1">
  <img src="thumbnail-a.jpeg" />
</a>

<a href="image-b.jpeg" data-fancybox="gallery" data-caption="Caption #2">
  <img src="thumbnail-b.jpeg" />
</a>
```

##### 增加click事件处理函数

- 最后一步是使用 `Fancybox.bind()` 方法为启动Fancybox的元素的单击事件添加处理程序。
- 添加`Fancybox JS`文件后，将此代码粘贴到页面的任意位置:

```js
Fancybox.bind("[data-fancybox]", {
  // 自定义选项……
});
```

> [!tip]
>
> 此时，当用户单击与之前使用的选择器 `[data-fancybox]` 匹配的任何元素时，Fancybox就会启动。
>
> 更多配置项参考此处：[Options | Fancybox - best JavaScript lightbox alternative (fancyapps.com)](https://fancyapps.com/fancybox/api/options/)

##### 提示和技巧

- 虽然 `Fancybox.bind()` 方法接受JS `querySelectorAll` 方法支持的任何值，例如 `#gallery a` ，但使用 `[data-fancybox]` 更方便，因为这个属性也用于分组。

- 要为特定的图库设置自定义选项，只需使用适当的选择器，例如:

```js
Fancybox.bind('[data-fancybox="gallery"]', {
  // Your custom options for a specific gallery
});
```

> [!note]
>
> [JSFiddle例子](https://jsfiddle.net/u8b3x45v/)

- 也可以只向特定容器添加单击处理程序。在下例中，当用户单击ID为 `gallery-wrap` 且匹配选择器 `[data-fancybox]` 的元素时，Fancybox将被启动。

- 这种技术在为React、Vue等框架构建组件时非常有用。

```js
Fancybox.bind(document.getElementById("gallery-wrap"), "[data-fancybox]", {
  // Your custom options
});
```

> [!note]
>
> [JSFiddle例子](https://jsfiddle.net/5utk13x6/)

### 函数式用法

- 使用API在代码中的任何位置以编程方式启动Fancybox。例如，如果你想在用户第一次打开页面时显示一个通知(你只需要使用cookie或会话变量自己确定)，这是非常有用的。

```js
new Fancybox(
  [
    {
      src: "<p>Lorem ipsum dolor sit amet.</p>",
      type: "html",
    },
  ],
  {
    // Your custom options
  }
);
```

> [!note]
>
> [JSFiddle例子](https://jsfiddle.net/rh32c4Ls/)

### 额外用法

#### 通过指定选择器或元素启动

- 一个相当常见的请求是在页面加载或单击按钮时启动Fancybox。使用 `Fancybox.fromSelector()` 方法使用之前使用的选择器启动Fancybox:

```js
Fancybox.fromSelector('[data-fancybox="gallery"]');
```

> [!note]
>
> [JSFiddle例子](https://jsfiddle.net/nc5o4zp1/)

- 对于特殊用例，你可以使用 `Fancybox.fromNodes()` API方法，以编程方式从HTML元素启动Fancybox:

```js
Fancybox.fromNodes(
  Array.from(document.querySelectorAll('[data-fancybox="gallery"]')),
  {
    // Your custom options
  }
);
```

#### 使用触发器元素

- 有时，你可能需要一个额外的触发元素，比如一个按钮，点击它时，会在特定的索引处打开Fancybox画廊。或者，例如，您可能希望使用额外的预览缩略图。
- 只需使用 `data-fancybox-trigger` 属性，其值与其他元素的 `data-fancybox` 属性相同。可选地使用 `data-fancybox-index` 属性指定起始元素的索引:

html 超文本标记语言。

```html
<a href="javascript:;" data-fancybox-trigger="gallery" data-fancybox-index="0">
  <img src="https://lipsum.app/id/1/400x300" />
</a>
```

## `vue-virtual-scroller` 虚拟列组件

> [!tip]
>
> 文档(Vue2)：[vue-virtual-scroller/packages/vue-virtual-scroller at v1 · Akryum/vue-virtual-scroller (github.com)](https://github.com/Akryum/vue-virtual-scroller/tree/v1/packages/vue-virtual-scroller)
>
> 文档(Vue3):[vue-virtual-scroller/packages/vue-virtual-scroller at master · Akryum/vue-virtual-scroller (github.com)](https://github.com/Akryum/vue-virtual-scroller/tree/master/packages/vue-virtual-scroller)
>
> 下面以Vue2为例

### 安装和导入

#### 安装

```bash
npm install --save vue-virtual-scroller
```

#### 导入

##### 全局导入

```js
import Vue from 'vue'
import VueVirtualScroller from 'vue-virtual-scroller'

Vue.use(VueVirtualScroller)
```

##### 局部导入

```js
import Vue from 'vue'
import { RecycleScroller } from 'vue-virtual-scroller' // 组件
import 'vue-virtual-scroller/dist/vue-virtual-scroller.css' // 样式

Vue.component('RecycleScroller', RecycleScroller)
```

### 使用

`vue-virtual-scroller` 提供了以下几个组件:

- [RecycleScroller](https://github.com/Akryum/vue-virtual-scroller/tree/v1/packages/vue-virtual-scroller#recyclescroller) 是一个只渲染列表中可见元素的组件。它还重用了组件和dom元素，以尽可能地高效和高性能。
- [DynamicScroller](https://github.com/Akryum/vue-virtual-scroller/tree/v1/packages/vue-virtual-scroller#dynamicscroller) 是一个封装了`RecycleScroller`组件并扩展其功能以包括动态大小管理的组件。它的主要用例是当你不提前知道项目的大小时。动态滚动器在滚动过程中渲染新项目时自动“发现”项目的尺寸。
- [DynamicScrollerItem](https://github.com/Akryum/vue-virtual-scroller/tree/v1/packages/vue-virtual-scroller#dynamicscrolleritem) 必须将每个项目包装在`DynamicScrollerItem`中以处理大小计算。
- [IdState](https://github.com/Akryum/vue-virtual-scroller/tree/v1/packages/vue-virtual-scroller#idstate) 是一个mixin(混合类型)，它简化了`RecycleScroller`中复用组件的本地状态管理。

#### RecycleScroller 组件

> [!note]
>
> `RecycleScroller`是一个虚拟的`scroller`，它只渲染那些可见的元素。当用户滚动时，`RecycleScroller`会复用所有组件和DOM节点来保持最佳性能。

##### 基本用法

- 使用scoped slot渲染列表中的每个元素:

```vue
<template>
<RecycleScroller
   class="scroller"
   :items="list"
   :item-size="32"
   key-field="id"
   v-slot="{ item }">
  <div class="user">
    {{ item.name }}
  </div>
  </RecycleScroller>
</template>

<script>
  export default {
    props: {
      list: Array,
    },
  }
</script>

<style scoped>
  .scroller {
    height: 100%;
  }

  .user {
    height: 32%;
    padding: 0 12px;
    display: flex;
    align-items: center;
  }
</style>
```

##### 注意事项

- ⚠️需要设置`virtual-scrollview`元素和`items`元素的大小(例如，使用CSS)。除非你使用的是可变尺寸模式，否则所有元素都应该具有相同的高度(或水平模式下的宽度)，以防止显示故障。
- ⚠️如果`item`是对象，`scrollview`需要能够识别它们默认情况下，它会在元素项上查找 `id` 字段。如果使用其他字段名称，可以使用 `keyField` 属性来配置。
- 不建议在`RecycleScroller`中使用<u>函数式组件</u>，因为组件会被复用(所以实际上会慢一些)。
- 列表的`item`组件必须能够响应 `item` 属性的更新，而不需要重新创建(使用`computed` `props`或`watchers`来正确地响应`props`的变化!)。
- 你不需要在列表内容上设置 `key` (但你应该在所有嵌套的 `<img>` 元素上设置，以防止加载故障)。
- 浏览器对DOM元素的大小有限制，这意味着当前虚拟scrollview不能显示超过`500k`的项目，具体取决于浏览器。

- 由于DOM元素可用于`item`，因此建议使用提供的 `hover` 类来定义悬停样式，而不是使用 `:hover` 状态选择器(例如 `.vue-recycle-scroller__item-view.hover` 或 `.hover .some-element-inside-the-item-view` )。
- 如果视图离开屏幕，它们可以被停用，并且可以在任何时候为新可见的项目重用。

### Props 

`items` :你想在scrollview中显示的项目列表。

`direction` (默认值: `'vertical'` ):滚动方向,要么 `'vertical'` 或 `'horizontal'` 。

`itemSize` (默认值: `null` ):以像素为单位的<u>显示高度</u>(或水平模式下的宽度)，用于计算滚动大小和位置。如果设置为 `null` (默认值)，它将使用可变大小模式。

`gridItems` :将多个元素显示在同一行，创建一个`Grid`。你必须为 `itemSize` 设置一个值才能使用这个属性(不支持动态大小)。

`itemSecondarySize` :设置 `gridItems` 时，网格中元素的尺寸，以像素为单位(垂直模式下为宽度，水平模式下为高度)。如果未设置 `itemSecondarySize` ，则使用 `itemSize` 的值。

`minItemSize` :当`item`的高度(或宽度在水平模式下)未知时，使用的<u>最小尺寸</u>。

`sizeField` (默认值: `'size'` ):在<u>可变尺寸模式</u>下用于获取`item`尺寸的字段。

`typeField` (默认值: `'type'` ):用于区分列表中不同类型组件的字段。对于每种不同的类型，将创建一个回收`item`池。

`keyField` (默认值: `'id'` ):用于标识项目和优化管理渲染视图的字段。

`pageMode` (默认: `false` ):启用页面模式。

`prerender` (默认: `0` ):为服务器端渲染(SSR)渲染固定数量的物品。

`buffer` (默认值: `200` ):添加到滚动可见区域边缘的像素数量，以便开始渲染更远的项目。

`emitUpdate` (默认: `false` ):每次更新虚拟scrollview内容时触发一个 `'update'` 事件(会影响性能)。

`listClass` (默认值: `''` ):列表容器的自定义css类名。

`listTag` (默认值: `'div'` ):列表容器的HTML标签 。

##### 事件

`resize` :当scrollview的大小改变时触发。

`visible` :当scrollview认为自己在页面中可见时触发。

`hidden` : scrollview在页面中隐藏时触发。

`update (startIndex, endIndex, visibleStartIndex, visibleEndIndex)` :每次视图更新时触发，仅当 `emitUpdate` prop为 `true`时触发

`scroll-start` :在第一个元素被渲染时触发。

`scroll-end` :在渲染最后一个元素时触发。



##### 插槽传值 (scoped-slot)

`item` :在视图中渲染的项。

`index` :反映每个元素在 `items` 数组中的位置

`active` :表示视图是否激活。活动视图被认为是可见的，并且被定位为 `RecycleScroller` 。不活动的视图不被认为是可见的，对用户是隐藏的。如果视图处于非活动状态，则应该跳过任何与渲染相关的计算。

##### 其他插槽

```vue
<main>
  <slot name="before"></slot>
  <wrapper>
    <!-- Reused view pools here (这里是重复使用的视图池) -->
    <slot name="empty"></slot>
  </wrapper>
  <slot name="after"></slot>
</main>
```

- 例子：

```vue
<RecycleScroller
  class="scroller"
  :items="list"
  :item-size="32"
>
  <template #before>
    Hey! I'm a message displayed before the items!
		嘿！我是之前显示的一个items！
  </template>

  <template v-slot="{ item }">
    <div class="user">
      {{ item.name }}
    </div>
  </template>
</RecycleScroller>
```

## vuetify 组件库

> [!tip]
>
> 官网：[Vuetify — A Vue Component Framework (vuetifyjs.com)](https://vuetifyjs.com/)

### 安装

```bash
yarn add vuetify
```

### 引入

#### 全部引入

```ts
// main.js 或 main.ts
import { createApp } from 'vue'
import App from './App.vue'

// Vuetify
import 'vuetify/styles'
import { createVuetify } from 'vuetify'
import * as components from 'vuetify/components'
import * as directives from 'vuetify/directives'

const vuetify = createVuetify({
  components,
  directives,
})

createApp(App).use(vuetify).mount('#app')
```

#### 按需引入

##### vite中的按需引入

> [!tip]
>
> 参考：[vite-plugin-vuetify - npm (npmjs.com)](https://www.npmjs.com/package/vite-plugin-vuetify)

###### 安装`vite-plugin-vuetify`插件

```bash
yarn add -D vite-plugin-vuetify
```

###### 再配置`vite.config.js`文件

```ts
// vite.config.js
plugins: [
  vue(),
  vuetify({ autoImport: true }), // 默认是启用的
]
```

```ts
// plugins/vuetify.js
import 'vuetify/styles'
import { createVuetify } from 'vuetify'

export default createVuetify()
```

###### 一些其他设置

- 忽略部分组件或指令
  ```ts
  // vite.config.js
  plugins: [
    vue(),
    vuetify({ 
      autoImport: {
        ignore: [
          'VAlert', // 组件名
          'Ripple', // 插件名
        ]
      }
    }), 
  ]
  ```

- 自定义变量

  ```ts
  // vite.config.js
  plugins: [
    vue(),
    vuetify({ styles: { configFile: 'src/settings.scss' } }),
  ]
  ```

  ```ts
  // plugins/vuetify.js
  import 'vuetify/styles'
  import { createVuetify } from 'vuetify'
  
  export default createVuetify()
  ```

  ```ts
  // settings.scss
  @use 'vuetify/settings' with (
    $color-pack: false,
    $utilities: false,
  );
  ```

  > [!tip]
  >
  > `settings.scss` 可以在你自己的组件中使用来访问vuetify的变量。

- 删除所有样式导入

  ```ts
  // vite.config.js
  plugins: [
    vue(),
    vuetify({ styles: 'none' }),
  ]
  ```

  ```ts
  // plugins/vuetify.js
  import { createVuetify } from 'vuetify'
  
  export default createVuetify()
  ```





















### 字体图标

> [!warning]
>
> 此操作在vite中暂时无效

> [!note]
>
> 参考：[图标字体 — Vuetify (vuetifyjs.com)](https://vuetifyjs.com/zh-Hans/features/icon-fonts/)
>
> vite项目中需要使用**[vite-plugin-iconify](https://github.com/qq15725/vite-plugin-iconify)**

#### 安装

```bash
yarn add @mdi/font -D
```

#### 引入



###### 引入字体图标

```ts
import '@mdi/font/css/materialdesignicons.css' // 确保正在使用css-loader
import { createVuetify } from 'vuetify'
import { aliases, mdi } from 'vuetify/iconsets/mdi'


export default createVuetify({
  icons: {
    defaultSet: 'mdi', // 图标前缀
    aliases,
    sets: {
      mdi,
    },
  },
})
```

###### 使用字体图标

```vue
<template>
  <v-icon icon="mdi-home" />
</template>
```





## Varlet 组件库

> [!tip]
>
> 官网：[面向 Vue3 的 Material 风格移动端组件库 (gitee.io)](https://varlet.gitee.io/varlet-ui/#/zh-CN/index)

### 安装

```bash
# Webpack/Vite
# 通过 npm、yarn 或 pnpm 安装

# npm
npm i @varlet/ui -S

# yarn
yarn add @varlet/ui

# pnpm
pnpm add @varlet/ui
```

### 引入

```js
// main.js 或 main.ts
import App from './App.vue'
import Varlet from '@varlet/ui'
import { createApp } from 'vue'
import '@varlet/ui/es/style'

createApp(App).use(Varlet).mount('#app')
```

### 自动引入

通过插件 [unplugin-vue-components](https://github.com/antfu/unplugin-vue-components) 和 [unplugin-auto-import](https://github.com/antfu/unplugin-auto-import) 实现组件自动按需导入，这也是我们最推荐的方式。

#### 安装插件

```bash
# npm
npm i @varlet/import-resolver unplugin-vue-components unplugin-auto-import -D

# yarn
yarn add @varlet/import-resolver unplugin-vue-components unplugin-auto-import -D

# pnpm
pnpm add @varlet/import-resolver unplugin-vue-components unplugin-auto-import -D
```

#### Vite

```js
// vite.config.js
import vue from '@vitejs/plugin-vue'
import components from 'unplugin-vue-components/vite'
import autoImport from 'unplugin-auto-import/vite'
import { VarletImportResolver } from '@varlet/import-resolver'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [
    vue(),
    components({
      resolvers: [VarletImportResolver()]
    }),
    autoImport({
      resolvers: [VarletImportResolver({ autoImport: true })]
    })
  ]
})
```

#### Vue CLI

```js
// vue.config.js
const Components = require('unplugin-vue-components/webpack')
const AutoImport = require('unplugin-auto-import/webpack')
const { VarletImportResolver } = require('@varlet/import-resolver')

module.exports = {
  configureWebpack: {
    plugins: [
      Components.default({
        resolvers: [VarletImportResolver()]
      }),
      AutoImport.default({
        resolvers: [VarletImportResolver({ autoImport: true })]
      })
    ]
  }
}
```

#### Typescript 配置注意

为了得到良好的 IDE 语法高亮，请确保上述两个插件生成的类型声明文件被 `typescript` 识别，可在 `tsconfig.json` 中进行如下配置:

```json
{
  "include": ["auto-imports.d.ts", "components.d.ts"]
}
```

### 注意事项

- 如果要在桌面端使用Varlet组件中的拖拽功能，需要安装`@varlet/touch-emulator`，并在入口文件导入

# 一些CSS动画库

## GSAP

> [!tip]
>
> 官网：[Homepage | GSAP](https://gsap.com/)
>
> 中文wiki：[GSAP 中文教程 中文文档 ｜官方文档 官方教程翻译 ｜好奇代码出品](https://gsap.framer.wiki/)

### 安装和引入

```bash
# 安装
yarn add gsap
```

```js
// 引入
import gsap from 'gsap'
```

### 基本使用(以Vue为例)

> [!tip]
>
> 参考：[GSAP 中文教程 中文文档 ｜官方文档 官方教程翻译 ｜好奇代码出品](https://gsap.framer.wiki/)

- **在 Vue 组件中创建动画**： 在 Vue 组件的生命周期钩子函数中，或者在用户触发的事件中使用 GSAP 创建动画：

```js
export default {
  mounted() {
    const element = this.$refs.box; // 获取元素引用

    // 创建动画
    gsap.to(element, { x: 200, duration: 1, ease: 'power2.inOut' });
  }
}
```

​	上面的代码示例中，我们在组件的 `mounted` 钩子函数中创建了一个动画，将元素从当前位置水平移动 200px。

- **使用 TweenMax**： 如果你喜欢使用 TweenMax，也可以像之前一样在组件中引入和使用 TweenMax：

```js
import { TweenMax, Power2 } from 'gsap';

export default {
  mounted() {
    const element = this.$refs.box;

    TweenMax.to(element, 1, { x: 200, ease: Power2.easeInOut });
  }
}
```

















# The End
