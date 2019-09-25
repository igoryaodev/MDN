### String Function Outline
|function|description|demo|
|:---|:---|:---|
|String.fromCharCode()|`(方法返回由指定的UTF-16代码单元序列创建的字符串。)该方法返回一个字符串，而不是一个  __String__ 对象。由于 fromCharCode() 是  String 的静态方法，所以应该像这样使用：__String.fromCharCode()__，而不是作为你创建的  String 对象的方法。`|`console.log(String.fromCharCode(189, 43, 190, 61));`\/\/ expected output: "½+¾="|
|String.fromCodePoint()|`(静态方法返回使用指定的代码点序列创建的字符串。)该方法返回一个字符串，而不是一个 __String__ 对象。因为 fromCodePoint() 是 String 的一个静态方法，所以只能通过 __String.fromCodePoint()__ 这样的方式来使用，不能在你创建的 String 对象实例上直接调用。`|`console.log(String.fromCodePoint(9731, 9733, 9842, 0x2F804));`\/\/ expected output: "☃★♲你"|
|String.prototype.charAt()|`字符串中的字符从左向右索引，第一个字符的索引值为 0，最后一个字符（假设该字符位于字符串 stringName 中）的索引值为 stringName.length - 1。 如果指定的 index 值超出了该范围，则返回一个空字符串。不支持[多文种平面（BMP）字符](https://zh.wikipedia.org/wiki/Unicode%E5%AD%97%E7%AC%A6%E5%B9%B3%E9%9D%A2%E6%98%A0%E5%B0%84#.E5.9F.BA.E6.9C.AC.E5.A4.9A.E6.96.87.E7.A7.8D.E5.B9.B3.E9.9D.A2)`|`var str = 'test';str.charAt(1);// output: e`|
|String.prototype.charCodeAt()|`Unicode 编码单元（code points）的范围从 0 到 1,114,111（0x10FFFF）。开头的 128 个 Unicode 编码单元和 ASCII 字符编码一样。关于 Unicode 的更多信息，可查看 JavaScript Guide。注意，charCodeAt 总是返回一个小于 65,536 的值。这是因为高位编码单元（higher code point）使用一对（低位编码 lower valued）代理伪字符（"surrogate" pseudo-characters）来表示，从而构成一个真正的字符。因此，为了查看或复制（reproduce）65536 及以上编码字符的完整字符，需要在获取 charCodeAt(i) 的值的同时获取 charCodeAt(i+1) 的值（如同查看/reproducing 拥有两个字符的字符串一样），或者改为获取 codePointAt(i) 的值。参看下面例 2 和例 3。如果指定的 index 小于 0 或不小于字符串的长度，则 charCodeAt 返回 NaN。向后兼容：在历史版本中（如 JavaScript 1.2），charCodeAt 返回一个数字，表示给定 index 处字符的 ISO-Latin-1 编码值。ISO-Latin-1 编码集范围从 0 到 255。开头的 0 到 127 直接匹配 ASCII 字符集。`|`返回值是一表示给定索引处（String中index索引处）字符的 UTF-16 代码单元值的数字；如果索引超出范围，则返回 NaN。var str = 'test';str.charCodeAt(1);// output: 101`|
|String.prototype.codePointAt()|`__(ES6)__如果在指定的位置没有元素则返回 undefined 。如果在索引处开始没有UTF-16 代理对，将直接返回在那个索引处的编码单元。Surrogate Pair是UTF-16中用于扩展字符而使用的编码方式，是一种采用四个字节(两个UTF-16编码)来表示一个字符，称作代理对。`|`'ABC'.codePointAt(1);'\uD800\uDC00'.codePointAt(0);'XYZ'.codePointAt(42); // 66 65536 undefined`|
|String.prototype.concat()||
|String.prototype.endsWith()||
|String.prototype.includes()||
|String.prototype.indexOf()||
|String.prototype.lastIndexOf()||
|String.prototype.localeCompare()||
|String.prototype.match()||
|String.prototype.matchAll()||
|String.prototype.normalize()||
|String.prototype.padEnd()||
|String.prototype.padStart()||
|String.prototype.repeat()||
|String.prototype.replace()||
|String.prototype.search()||
|String.prototype.slice()||
|String.prototype.split()||
|String.prototype.startsWith()||
|String.prototype.substring()||
|`!String.prototype.substr()`||
|String.prototype.toLocaleLowerCase()|`toLocaleLowerCase()方法返回调用该方法的字符串被转换成小写之后的值，转换规则根据任何本地化特定的大小写映射。toLocaleLowerCase()并不会影响字符串自身的值。在大多数情况下，该方法产生的结果和调用toLowerCase()的结果相同，但是在某些本地环境中，比如土耳其语，它的大小写映射并不遵循在Unicode中的默认的大小写映射，因此会有一个不同的结果。`|
|String.prototype.toLocaleUpperCase()|`同上。toLocaleUpperCase() 使用本地化（locale-specific）的大小写映射规则将输入的字符串转化成大写形式并返回结果字符串。`|
|String.prototype.toUpperCase()||
|String.prototype.toLowerCase()||
|String.prototype.toString()||
|String.prototype.trim()||
|String.prototype.trimRight()||
|String.prototype.trimLeft()||
|String.prototype.valueOf()||
|String.prototype[@@iterator]()||
|String.raw()||
||
||
||


### 方法

>String.fromCharCode()  
 
  通过一串 Unicode 创建字符串。

  静态 String.fromCharCode() 方法返回由指定的UTF-16代码单元序列创建的字符串。

  `String.fromCharCode(num1, ..., numN) `

  `num1, ..., numN
一系列UTF-16代码单元的数字。 范围介于0到65535（0xFFFF）之间。 大于0xFFFF的数字将被截断。 不进行有效性检查。`

```
console.log(String.fromCharCode(189, 43, 190, 61));
// expected output: "½+¾="

console.log(String.fromCharCode(189))
// ½

String.fromCharCode(65, 66, 67);  // returns "ABC"
String.fromCharCode(0x2014)       // returns "—"
String.fromCharCode(0x12014)      // also returns "—"; the digit 1 is truncated and ignored
```

>作用于高位编码（higher values）

尽管绝大部分常用的 Unicode 值可以用一个 16-bit 数字表示（正如JavaScript标准化早期所预期的那样），而fromCharCode()可用于返回最常见值的单个字符（即UCS-2值，即 UTF-16的子集具有最常见的字符），但是为了处理所有的 Unicode 值（最多 21位），只用 fromCharCode() 是不够的。  由于高位编码字符是用两个低位编码（lower value）表示形成的一个字符，因此可以使用String.fromCodePoint() （ES2015标准的一部分）返回这样一对低位编码，从而可以完全表示这些高位编码字符。

### String.fromCodePoint() 静态方法返回使用指定的代码点序列创建的字符串。