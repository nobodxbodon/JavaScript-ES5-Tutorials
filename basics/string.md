## 字符串的声明
我们之前使用过的数据类型只有数字类型，那种类型的数据用来表示数学里或生活中的数字。而我们即将学习一种新的数据类型——**字符串类型**。字符串类型的数据可以用来表示一小段话，一段文字，人名，一篇文章等等由文字组成的内容。在 JavaScript 中我们可以使用 `'......'` 或者 `"......"` 的形式声明一个字符串类型的数据，例如：

``` javascript
  var a = '包好，包好！这样的趁热吃下。'; // 用 ' （单引号）将文字包裹，声明一个字符串
  var b = "这样的人血馒头，什么痨病都包好！"; // 用 " （双引号）将文字包裹，声明一个字符串
  var c = ''; // 空字符串，既没有任何内容的字符串
  var d = ""; // 同上
```

但凡用 `'` 或者 `"` 包裹起来的东西，都会变成字符串的内容，包括数字和标点符号，空格等等等等，例如：

``` javascript
  var a = '10086'; // 字符串，内容是数字
  var b = "10010"; // 字符串，内容是数字
  
  var c = "10010 + 10086"; // 字符串，内容是一个和式
  
  var d = '@#$%^&*()'; // 字符串，内容是一堆符号
  var d = "     "; // 字符串，内容是一串空格
```

## 单引号和双引号的错误配对
大多数情况下，在声明字符串的时候使用 `'` 或者 `"` 包裹内容的效果是一样的，但如内容中包含 `'` 或者 `"` 则需要小心 JavaScript 的错误配对：

``` javascript
  // 有如下一个字符串
  // He says:"so far so good。"

  // 包裹字符串的 " 和内容中的 " 产生了错误的配对
  // 于是字符串被错误的分割成了 "He says:" 和 ""(空字符串)，
  // 而 so far so good 被当成了代码。
  var a = "He says:"so far so good。"";
  
  // 此时用 ' 包裹就可以避免这个问题
  var a = 'He says:"so far so good。"';
  
  // 在内容中的 " 之前加上 \ 也可以避免这个问题
  var a = "He says:\"so far so good。\"";
  
  
  
  // 同样的，有如下字符串。
  // I'm starving.
  
  // 如果直接用 ' 包裹也会出错
  // 包裹字符串的 ' 和字符串内容中的 ' 产生了错误的配对
  var b = 'I'm starving.';
  
  // 解决的方式是用 " 包裹
  var b = "I'm starving.";
  
  // 或是在 ' 前加上 \
  var b = 'I\'m starving.';
```

虽然 JavaScript 并不介意我们在声明字符串的时候使用的是 `'` 还是 `"` 。但是我们人类往往是介意的，时而用 `'` 时而用 `"` 总归会让代码看起来不那么工整，所以往后的实例代码中会优先使用 `'` ， 而 `"` 只有在内容中出现 `'` 的时候使用`。

## 拼接字符串
对于字符串，我们可以使用 `+` 操作符来将字符串拼接到一块。 `+` 操作符作用于数字就是数学上的相加，而作用于字符串时则是将字符串拼接，例如：

``` javascript
  var a = '两个黄鹂鸣翠柳，';
  var b = '一行白鹭上青天。';
  
  var c = a + b; // 将 a 和 b 拼接到一起
  console.log(c); // 得到“两个黄鹂鸣翠柳，一行白鹭上青天。”
  
  var d = b + a; // 将 b 和 a 拼接
  console.log(d); // 得到“一行白鹭上青天。两个黄鹂鸣翠柳，”
  
  var e = '窗含西岭千秋雪，' + '门泊东吴万里船。';
  console.log(e); // 得到“窗含西岭千秋雪，门泊东吴万里船。”
```

也可以同时拼接多个字符串。

``` javascript
  var a = '从前的日色变得慢。' + '车，马，邮件都慢。' + '一生只够爱一个人。';
  console.log(a); // 得到“从前的日色变得慢。车，马，邮件都慢。一生只够爱一个人。”
  
  var b = '从前的锁也好看。' + '钥匙精美有样子。' + '你锁了，人家就懂了。';
  console.log(b); // 得到“从前的锁也好看。钥匙精美有样子。你锁了，人家就懂了。”
  
  var c = '钥匙精美有样子。';
  var d = '你锁了，人家就懂了。';
  
  var e = '从前的锁也好看。' + c + d + '——《从前慢》作者：木心';
  console.log(e); // 得到“从前的锁也好看。钥匙精美有样子。你锁了，人家就懂了。——《从前慢》作者：木心”
```

## 字符串和数字的拼接
如果把字符串和数字用拼接操作符拼接， JavaScript 会将数字变为字符串然后进行拼接操作，得到的结果是一个字符串。

```javascript
  var a = 1 + 2 + 3;
  var b = '1 + 2 + 3 的结果是 ' + a;
  console.log(b); // 输出 “1 + 2 + 3 的结果是 6”
  
  var c = '我爱你就是 ' + 5 + 2 + 0; // #1
  console.log(c); // “我爱你就是 520”
  
  var d = 100 + 86 + ' 是中国移不动的服务电话。'; // #2
  console.log(d); // “186 是中国移不动的服务电话。”
```
* 在操作符优先级相同的情况下 JavaScript 是从左到右求值。
* \#1 这里先计算 `'我爱你就是 ' + 5` 得到一个字符串，然后使用该字符串拼接数字 `2` 又得到一个字符串，然后再用上一步的结果拼接数字 `0` 得到最后的结果。
* \#2 这里先计算 `100 + 86` 是一个数值的相加， 得到结果数字 `186` 再将这个数字跟后边的字符串拼接。


## 转义字符
字符串中有些特殊的字符可以让 JavaScript 对其进行特殊处理，例如我们已经见过的 `\'` 和 `\"`，这类字符叫转义字符，它们算作**一个**字符。 JavaScript 中的转义字符跟许多编程语言一样，是在字符前加一个 `\` 实现。包括前面介绍的 `\'` 和 `\"`，这里再继续介绍 `\n` 和 `\\`。

前面介绍的字符串都是显示在一行以内的，实际上字符串是可以换行显示的，只要在字符串中加入 `\n` ，所以 `\n` 又叫做换行符。

```javascript
  var a = '从前的日色变得慢。\n' + '车，马，邮件都慢。\n' + '一生只够爱一个人。\n';
  console.log(a);
  // 从前的日色变得慢。
  // 车，马，邮件都慢。
  // 一生只够爱一个人。
```

如果字符串中需要显示 `\` ，我们直接在字符串中用 `\\`，代替单个的 `\`。

```javascript
  var a = '英文的反斜杠是 \'; // 报错， JavaScript 把结尾的 \' 当成了一个整体。
  
  var a = '英文的反斜杠是 \\';
  console.log(a); // 输出 “英文的反斜杠是 \”
  
  var b = '换行符是 \n 。';
  console.log(b); // 输出 “换行符是 ” 和它的下一行 “ 。”
  
  var b = '换行符是 \\n 。';
  console.log(b); // 输出 “换行符是 \n 。”
```

这里介绍了最常用的转义字符，更多的转义字符，可以自行查找相关资料了解。

## 查看字符串长度

一个字符串由几个字符组成，我们就说这个字符串的长度是几。JavaScript 里我们可以通过字符串的`length`属性查看一个字符串的长度，访问某个东西的属性使用`.`操作符，于是通过`'zifuchuan'.length`之类的写法，就能得到一个字符串的长度。

```javascript
console.log('12345'.length); // 5

var str = 'abcdefg';
console.log(str.length); // 7

var str = 'abcdefg\n';
console.log(str.length); // 8

var len = '987654321'.length;
console.log(len); // 9

```
> 转义字符算作「一个字符」。

## 使用 [] 操作符取单个字符

一个字符串由多个字符组成，其中的每个字符，都是这个字符串的**成员**。例如在字符串`'abcde'`中`'a'`、`'b'`、`'c'`、`'d'`、`'e'`就是它的成员。成员在字符串中的位置叫**索引**，JavaScript 中索引从`0`开始计数，也就是说，字符串中的第一个字符的索引是`0`，第二个字符的索引是`1`，第三个字符的索引是`2`以此类推，下表给出了字符串`'staturday'`中各个字符的索引。

<table>
 <thead>
  <tr>
   <td><strong>成员</strong></td>
   <td>s</td>
   <td>t</td>
   <td>a</td>
   <td>t</td>
   <td>u</td>
   <td>r</td>
   <td>d</td>
   <td>a</td>
   <td>y</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><strong>索引</strong></td>
   <td>0</td>
   <td>1</td>
   <td>2</td>
   <td>3</td>
   <td>4</td>
   <td>5</td>
   <td>6</td>
   <td>7</td>
   <td>8</td>
  </tr>
 </tbody>
</table>

在操作字符串的时候，如果我们想要得到一个字符串中的单个的字符，可以在字符串后使用`[]`操作符把想要获取的成员的索引包裹住，例如：

```javascript
console.log('abc'[0]); // 'a'

var str = 'staturday';
console.log(str[1]); // 't';
```

`[]`的内部还能是表达式，以方便我们在编程的时候动态的获取单个成员，例如：

```javascript
var str = 'staturday';

console.log(str[1 + 2]); // 't'

var a = 2;
var b = 2;
console.log(str[a + b]); // 'u'
console.log(str[a - 1]); // 't'

console.log(str[str.length - 1]); // 'y'
```
> 小技巧：一个字符串的`length - 1`恰好就是这个字符串最后一个成员的索引。

## 字符串切片
获取一个字符串中的一部分内容，叫做**字符串切片**。JavaScript 提供了`slice`方法让我们对字符串进行切片。`slice`方法的用法如下伪代码描述。

```
字符串.slice(开始的索引, 结束的索引);
```

例如下列表格标注出了字符串`'sunday'`各个成员和索引。

<table>
 <thead>
  <tr>
   <td><strong>成员</strong></td>
   <td>s</td>
   <td>u</td>
   <td>n</td>
   <td>d</td>
   <td>a</td>
   <td>y</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><strong>索引</strong></td>
   <td>0</td>
   <td>1</td>
   <td>2</td>
   <td>3</td>
   <td>4</td>
   <td>5</td>
  </tr>
 </tbody>
</table>

下列代码中从`'sunday'`中获取，`'sun'`、`'day'`、`'und'`、`'nda'`。

```javascript
var str = 'sunday';

var part1 = str.slice(0, 3); // 获取从索引 0 开始到索引 3 之前的内容
console.log(part1); // 'sun'

var part2 = str.slice(3, 6); // 获取从索引 3 开始到索引 6 之前的内容
console.log(part2); // 'day'

var part3 = str.slice(1, 4); // 获取从索引 1 开始到索引 4 之前的内容
console.log(part2); // 'und'

var part4 = str.slice(2, 5); // 获取从索引 2 开始到索引 5 之前的内容
console.log(part2); // 'nda'
```

方法`字符串.slice(开始的索引, 结束的索引)`中，括号里的「开始的索引」和「结束的索引」叫做这个方法的**参数**，例如：

```javascript
var str = 'sunday';

var part1 = str.slice(0, 3); // 第一个参数是 0， 第二个参数是 3
console.log(part1); // 'sun'

var part2 = str.slice(3, 6); // 第一个参数是 3， 第二个参数是 6
console.log(part2); // 'day'
```
> 小练习：其实`console.log`也是一个方法，你能说出上边代码中各个`console.log`它们的参数分别是什么么。

在`slice`方法中我们可以省略第二个参数「结束的索引」，那么此时它的行为就变成，获取从「开始的索引」开始一直到字符串结束之前的内容，例如下列代码中从`'sunday'`中获取，`'day'`、`'unday'`、`'sunday'`。

```javascript
var str = 'sunday';

var part1 = str.slice(3); // 获取从索引 3 一直到字符串结束之前的内容
console.log(part1); // 'day'

var part2 = str.slice(1); // 获取从索引 1 一直到字符串结束之前的内容
console.log(part2); // 'unday'

var part3 = str.slice(0); // 获取从索引 0 一直到字符串结束之前的内容
console.log(part3); // 'sunday'
```

## 获取成员的索引

字符串的`indexOf`方法可以获取其中成员的索引，例如下列代码从字符串`'满脑子都是孩子哭了笑了'`中获取`'脑'`和`'是'`的索引：

```javascript
var str = '满脑子都是孩子哭了笑了';
var index1 = str.indexOf('脑');
console.log(index1); // 1

var index2 = str.indexOf('是');
console.log(index2); // 4
```

`indexOf`的参数除了可以是单个的字符，还可以是一个字符串，例如下列代码中从字符串`'满脑子都是孩子哭了笑了'`中获取，`'孩子'`和`'哭了笑了'`的索引：

```javascript
var str = '满脑子都是孩子哭了笑了';
var index1 = str.indexOf('孩子');
console.log(index1); // 5

var index2 = str.indexOf('哭了笑了');
console.log(index2); // 7
```

如果找不到成员，`indexOf`就会返回`-1`，例如：

```javascript
var str = '满脑子都是孩子哭了笑了';
var index = str.indexOf('404');
console.log(index); // -1
```

## 字符串练习
1. 下面声明字符串的方式，哪些是对的哪些是错的。

 ```
   var a = ' ';
   var b = " ';
   var c = '我是字符串\n';
   var d = \' 我是字符串 \';
   var e = '\'\'\'\'\'\'';
   var f = " 我是字符串 \"";
   var g = ':";
   var h = "var";
   var i = "I'd like that book.";
   var j = "I\'d like that book.";
   var k = "1000 / 1.";
 ```
2. 阅读下边的代码回答问题。
 
 ```javascript
  var a = '我打江南走过。';
  var b = '那等在季节里的容颜如莲花的开落。';
  var c = '东风不来，三月的柳絮不飞。';
  var d = '你底心如小小的寂寞的城。';
  var e = '恰若青石的街道向晚。';
  var f = '跫音不响，三月的春帷不揭。';
  var g = '你底心是小小的窗扉紧掩。';
  var h = '我达达的马蹄是美丽的错误。';
  var i = '我不是归人，是个过客。';
 ```
 * a. 获取字符串 `a` 的长度的代码。
 * b. 获取全诗长度的代码。
 * c. 通过字符串下标获取字符串 `b` 中的 “落” 字的代码。
 * d. 通过字符串下标获取字符串 `c` 中的 “三” 字的代码。
 * e. 通过字符串下标获取字符串 `d` 中的 “你” 字的代码。
 * f. 通过 `slice` 方法获取字符串 `f` 中的 “跫音不响” 的代码。
 * g. 通过 `slice` 方法获取字符串 `g` 中的 “小小” 的代码。
 * h. 通过 `slice` 方法获取字符串 `h` 中的 “美丽的错误。” 的代码。
 * i. 通过 `slice` 方法获取字符串 `i` 中的 “我不是归人” 的代码。
 
3. 阅读下边的代码并说出 `a, b, c, d, e, f, g, h` 各变量的值是什么。

  ```javascript
    var a = 1 + 2 + 3 + '木头人';
    
    var num1 = 3, num2 = 8;
    var b = ++num1 + '哈哈' + num2--; // 提示 ++ 和 -- 的优先级高于 + 
    
    var str1 = '流言像扬花一样飞着';
    var c = str1 + str1.slice(7, 9) + str1.length;
    
    var str2 = '似水流年才是一个人的一切，其余全是片刻的欢愉和不幸。';
    var d = str2.slice(0, str2.length);
    
    var str3 = '巨大的财富背后，都隐藏着罪恶', len1 = str3.length;
    var e = str3[--len1];
    
    var f = str3[0] + str3[13];
    
    var num3 = 5, str4 = '最是那一低头的温柔';
    var g = str4[num3 + 2 - 1];
    var h = str4['5'];
  ```
