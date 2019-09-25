### String Function Outline
|function|description| -- | -- | -- |
|:---|:---|:---|:---|:---|
|String.fromCharCode()|`(方法返回由指定的UTF-16代码单元序列创建的字符串。)该方法返回一个字符串，而不是一个  String 对象。由于 fromCharCode() 是  String 的静态方法，所以应该像这样使用：String.fromCharCode()，而不是作为你创建的  String 对象的方法。`|`console.log(String.fromCharCode(189, 43, 190, 61));`\/\/ expected output: "½+¾="|
|String.fromCodePoint()|`(静态方法返回使用指定的代码点序列创建的字符串。)该方法返回一个字符串，而不是一个 String 对象。因为 fromCodePoint() 是 String 的一个静态方法，所以只能通过 String.fromCodePoint() 这样的方式来使用，不能在你创建的 String 对象实例上直接调用。`|`console.log(String.fromCodePoint(9731, 9733, 9842, 0x2F804));`\/\/ expected output: "☃★♲你"|
|String.prototype.charAt()|`字符串中的字符从左向右索引，第一个字符的索引值为 0，最后一个字符（假设该字符位于字符串 stringName 中）的索引值为 stringName.length - 1。 如果指定的 index 值超出了该范围，则返回一个空字符串。`不支持[多文种平面（BMP）字符](https://zh.wikipedia.org/wiki/Unicode%E5%AD%97%E7%AC%A6%E5%B9%B3%E9%9D%A2%E6%98%A0%E5%B0%84#.E5.9F.BA.E6.9C.AC.E5.A4.9A.E6.96.87.E7.A7.8D.E5.B9.B3.E9.9D.A2)|`var str = 'test';str.charAt(1);// output: e`|
|String.prototype.charCodeAt()|`Unicode 编码单元（code points）的范围从 0 到 1,114,111（0x10FFFF）。开头的 128 个 Unicode 编码单元和 ASCII 字符编码一样。关于 Unicode 的更多信息，可查看 JavaScript Guide。注意，charCodeAt 总是返回一个小于 65,536 的值。这是因为高位编码单元（higher code point）使用一对（低位编码 lower valued）代理伪字符（"surrogate" pseudo-characters）来表示，从而构成一个真正的字符。因此，为了查看或复制（reproduce）65536 及以上编码字符的完整字符，需要在获取 charCodeAt(i) 的值的同时获取 charCodeAt(i+1) 的值（如同查看/reproducing 拥有两个字符的字符串一样），或者改为获取 codePointAt(i) 的值。参看下面例 2 和例 3。如果指定的 index 小于 0 或不小于字符串的长度，则 charCodeAt 返回 NaN。向后兼容：在历史版本中（如 JavaScript 1.2），charCodeAt 返回一个数字，表示给定 index 处字符的 ISO-Latin-1 编码值。ISO-Latin-1 编码集范围从 0 到 255。开头的 0 到 127 直接匹配 ASCII 字符集。`|`返回值是一表示给定索引处（String中index索引处）字符的 UTF-16 代码单元值的数字；如果索引超出范围，则返回 NaN。var str = 'test';str.charCodeAt(1);// output: 101`|
|String.prototype.codePointAt()|`(ES6)如果在指定的位置没有元素则返回 undefined 。如果在索引处开始没有UTF-16 代理对，将直接返回在那个索引处的编码单元。Surrogate Pair是UTF-16中用于扩展字符而使用的编码方式，是一种采用四个字节(两个UTF-16编码)来表示一个字符，称作代理对。`|`'ABC'.codePointAt(1);'\uD800\uDC00'.codePointAt(0);'XYZ'.codePointAt(42); // 66 65536 undefined`|
|String.prototype.concat()|`concat 方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。 concat 方法并不影响原字符串。(提升性能建议使用 赋值操作符（+, +=）代替 concat )`|`str.concat(string2, string3[, ..., stringN])`|
|String.prototype.startsWith()|`(ES6)用来判断当前字符串是否以另外一个给定的子字符串开头，并根据判断结果返回 true 或 false。`|
|String.prototype.endsWith()|`(ES6)方法用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false。`|
|String.prototype.includes()|`(ES6)方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回 true 或 false。索引默认值为0`|
|String.prototype.indexOf()|`字符串中的字符被从左向右索引。首字符的索引（index）为 0，字符串 stringName 的最后一个字符的索引是 stringName.length - 1`|`str.indexOf(searchValue, fromIndex);表示开始查找的位置。可以是任意整数，默认值为 0。如果 fromIndex 小于 0，则查找整个字符串（等价于传入了 0）。如果 fromIndex 大于等于 str.length，则必返回 -1。若被查找的字符串是一个空字符串，则返回值在0---str.length 之间，即：fromIndex 小于等于 0 时，返回 0；fromIndex 大于 0 且小于等于 str.length 时，返回 fromIndex；fromIndex 大于字符串长度 str.length 时，返回 str.length。`|
|String.prototype.lastIndexOf()|`字符串中的字符被从左向右索引。首字符的索引（index）是 0，最后一个字符的索引是 stringName.length - 1。`|`str.lastIndexOf(searchValue[, length]);个字符串，表示被查找的值。如果searchValue是空字符串，则返回fromIndex。字符串中最后一个字符的索引，将被视为匹配的开始。fromIndex默认值是 +Infinity。如果 fromIndex >= str.length ，则会搜索整个字符串。如果 fromIndex >= str.length ，则等同于 fromIndex == 0。`|
|String.prototype.localeCompare()|`方法返回一个数字来指示一个参考字符串是否在排序顺序前面或之后或与给定字符串相同。新的 locales 、 options 参数能让应用程序定制函数的行为即指定用来排序的语言。  locales 和 options 参数是依赖于具体实现的，在旧的实现中这两个参数是完全被忽略的。`|https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare|
|String.prototype.match()|`如果正则表达式不包含 g 标志，str.match() 将返回与 RegExp.exec(). 相同的结果。groups: 一个捕获组数组 或 undefined（如果没有定义命名捕获组）。index: 匹配的结果的开始位置.input: 搜索的字符串.`|`var s1 = 'abcababababababa';console.log(s1.match(/a/), s1.match(/a/g)); // output: [0: "a",groups: undefined,index: 0,input: "abcababababababa",length: 1];    ["a","a","a","a","a","a","a","a"]`|
|String.prototype.matchAll()|` 方法返回一个包含所有匹配正则表达式及分组捕获结果的迭代器。`|`var s1 = 'abcababababababa';var a = [...s1.matchAll(/a/g)];var b = Array.from(s1.matchAll(/a/g), s => s[0]); console.log(a, b); // output: [[0: "a"groups: undefined,index: 0,input: "abcababababababa"], ....]; ["a","a","a","a","a","a","a","a"]`|
|String.prototype.normalize()|`按照指定的一种 Unicode 正规形式将当前字符串正规化.`|`str.normalize([form]);form: 四种 Unicode 正规形式 "NFC", "NFD", "NFKC", 以及 "NFKD" 其中的一个, 默认值为 "NFC".NFC - Normalization Form Canonical Composition.NFD - Normalization Form Canonical Decomposition.NFKC - Normalization Form Compatibility Composition.NFKD - Normalization Form Compatibility Decomposition.`var str = "\u1E9B\u0323"; str.normalize("NFD"); // "\u017F\u0323\u0307"|
|String.prototype.padEnd()|`(ES2017)用一个字符串填充当前字符串（如果需要的话则重复填充），返回填充后达到指定长度的字符串。从当前字符串的末尾（右侧）开始填充。`|`str.padEnd(targetLength [, padString]);targetLength当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。padString 可选填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）。`|'abc'.padEnd(10);  "'abc'.padEnd(10, "foo");   'abc'.padEnd(6, "123456"); 'abc'.padEnd(1);  // "abc// "abcfoofoof" // "abc123" // "abc"|
|String.prototype.padStart()|`方法用另一个字符串填充当前字符串(重复，如果需要的话)，以便产生的字符串达到给定的长度。填充从当前字符串的开始(左侧)应用的。`|同上|
|String.prototype.repeat()|`构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串的副本。`|let resultString = str.repeat(count);RangeError: 重复次数不能为负数。RangeError: 重复次数必须小于 infinity，且长度不会大于最长的字符串。|
|String.prototype.replace()|`方法返回一个由替换值（replacement）替换一些或所有匹配的模式（pattern）后的新字符串。模式可以是一个字符串或者一个正则表达式，替换值可以是一个字符串或者一个每次匹配都要调用的回调函数。`|__$$__	插入一个 "$"。$&	插入匹配的子串。__$`__	插入当前匹配的子串左边的内容。__$'__	插入当前匹配的子串右边的内容。__$n__	假如第一个参数是 RegExp对象，并且 n 是个小于100的非负整数，那么插入第 n 个括号匹配的字符串。提示：索引是从1开始|
|String.prototype.search()|`当你想要知道字符串中是否存在某个模式（pattern）时可使用 search()，类似于正则表达式的 test() 方法。当要了解更多匹配信息时，可使用 match()（但会更慢一些），该方法类似于正则表达式的 exec() 方法。`|
|String.prototype.slice()|`方法提取某个字符串的一部分，并返回一个新的字符串，且不会改动原字符串。`|`beginIndex: 从该索引（以 0 为基数）处开始提取原字符串中的字符。如果值为负数，会被当做 strLength + beginIndex 看待，这里的strLength 是字符串的长度（例如， 如果 beginIndex 是 -3 则看作是：strLength - 3）| endIndex: 可选。在该索引（以 0 为基数）处结束提取字符串。如果省略该参数，slice() 会一直提取到字符串末尾。如果该参数为负数，则被看作是 strLength + endIndex，这里的 strLength 就是字符串的长度(例如，如果 endIndex 是 -3，则是, strLength - 3)。`|例 1：str.slice(1, 4) 提取第二个字符到第四个字符（被提取字符的索引值（index）依次为 1、2，和 3）。例 2：str.slice(2, -1) 提取第三个字符到倒数第一个字符。|
|String.prototype.split()|`找到分隔符后，将其从字符串中删除，并将子字符串的数组返回。如果没有找到或者省略了分隔符，则该数组包含一个由整个字符串组成的元素。如果分隔符为空字符串，则将str转换为字符数组。如果分隔符出现在字符串的开始或结尾，或两者都分开，分别以空字符串开头，结尾或两者开始和结束。因此，如果字符串仅由一个分隔符实例组成，则该数组由两个空字符串组成。如果分隔符是包含捕获括号的正则表达式，则每次分隔符匹配时，捕获括号的结果（包括任何未定义的结果）将被拼接到输出数组中。但是，并不是所有浏览器都支持此功能。`|__separator__: 指定表示每个拆分应发生的点的字符串。separator 可以是一个字符串或正则表达式。 如果纯文本分隔符包含多个字符，则必须找到整个字符串来表示分割点。如果在str中省略或不出现分隔符，则返回的数组包含一个由整个字符串组成的元素。如果分隔符为空字符串，则将str原字符串中每个字符的数组形式返回。__limit__: 一个整数，限定返回的分割片段数量。当提供此参数时，split 方法会在指定分隔符的每次出现时分割该字符串，但在限制条目已放入数组时停止。如果在达到指定限制之前达到字符串的末尾，它可能仍然包含少于限制的条目。新数组中不返回剩下的文本。|
|String.prototype.substring()|`substring 提取从 indexStart 到 indexEnd（不包括）之间的字符。特别地：如果 indexStart 等于 indexEnd，substring 返回一个空字符串。如果省略 indexEnd，substring 提取字符一直到字符串末尾。如果任一参数小于 0 或为 NaN，则被当作 0。如果任一参数大于 stringName.length，则被当作 stringName.length。如果 indexStart 大于 indexEnd，则 substring 的执行效果就像两个参数调换了一样。`|var anyString = "Mozilla";console.lo(anyString.substring(0,3));console.log(anyString.substring(3,0));console.log(anyString.substring(3,-3));console.log(anyString.substring(3,NaN));console.log(anyString.substring(-2,3));console.log(anyString.substring(NaN,3));// 输出 "Moz";|
|`!String.prototype.substr()`|`(非规范)start 是一个字符的索引。首字符的索引为 0，最后一个字符的索引为 字符串的长度减去1。substr 从 start 位置开始提取字符，提取 length 个字符（或直到字符串的末尾）。如果 start 为正值，且大于或等于字符串的长度，则 substr 返回一个空字符串。如果 start 为负值，则 substr 把它作为从字符串末尾开始的一个字符索引。如果 start 为负值且 abs(start) 大于字符串的长度，则 substr 使用 0 作为开始提取的索引。注意负的 start 参数不被 Microsoft JScript 所支持。如果 length 为 0 或负值，则 substr 返回一个空字符串。如果忽略 length，则 substr 提取字符，直到字符串末尾。`|str.substr(start[, length])|
|String.prototype.toLocaleLowerCase()|`toLocaleLowerCase()方法返回调用该方法的字符串被转换成小写之后的值，转换规则根据任何本地化特定的大小写映射。toLocaleLowerCase()并不会影响字符串自身的值。在大多数情况下，该方法产生的结果和调用toLowerCase()的结果相同，但是在某些本地环境中，比如土耳其语，它的大小写映射并不遵循在Unicode中的默认的大小写映射，因此会有一个不同的结果。`|
|String.prototype.toLocaleUpperCase()|`同上。toLocaleUpperCase() 使用本地化（locale-specific）的大小写映射规则将输入的字符串转化成大写形式并返回结果字符串。`|
|String.prototype.toUpperCase()|`将调用该方法的字符串值转换为大写形式，并返回。toUpperCase 方法不影响字符串本身的值。`|
|String.prototype.toLowerCase()|`会将调用该方法的字符串值转为小写形式，并返回。toLowerCase 不会影响字符串本身的值。`|
|String.prototype.toString()|`String 对象覆盖了Object 对象的 toString 方法；并没有继承 Object.toString()。对于 String 对象，toString 方法返回该对象的字符串形式，和 String.prototype.valueOf() 方法返回值一样。`|
|String.prototype.trim()|`法会从一个字符串的两端删除空白字符。在这个上下文中的空白字符是所有的空白字符 (space, tab, no-break space 等) 以及所有行终止符字符（如 LF，CR）。`|if (!String.prototype.trim) {String.prototype.trim = function () {return this.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');};}|
|String.prototype.trimRight()|`trimEnd() / trimRight()方法移除原字符串右端的连续空白符并返回，trimEnd() / trimRight()方法并不会直接修改原字符串本身。`|
|String.prototype.trimLeft()|`trimStart() / trimLeft()方法移除原字符串左端的连续空白符并返回，trimStart() / trimLeft()方法并不会直接修改原字符串本身。`|
|String.prototype.valueOf()|`方法返回一个String对象的原始值（primitive value）。`|
|String.prototype[@@iterator]()|`方法返回一个新的Iterator对象，它遍历字符串的代码点，返回每一个代码点的字符串值。`|var string = 'A\uD835\uDC68';var strIter = string[Symbol.iterator]();console.log(strIter.next().value); console.log(strIter.next().value); // "A" // "\uD835\uDC68|
|String.raw()|`是一个模板字符串的标签函数，它的作用类似于 Python 中的字符串前缀 r 和 C# 中的字符串前缀 @（还是有点区别的，详见隔壁 Chromium 那边的这个 issue），是用来获取一个模板字符串的原始字符串的，比如说，占位符（例如 ${foo}）会被处理为它所代表的其他字符串，而转义字符（例如 \n）不会。`|String.raw(callSite, ...substitutions);String.raw`templateString`|


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