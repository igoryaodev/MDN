### String

> String 全局对象是一个用于字符串或一个字符序列的构造函数。

### 语法

> 'text 语法'

> 你也能使用 String 函数将其他值生成或转换成字符串：

`String(thing) or new String(thing)`

### 参数

thing
任何可以被转换成字符串的值。

### 模板字面量
从 ECMAScript 2015 开始，字符串字面量也可以称为模板字面量：

> `hello world` `hello! world!` `hello ${who}` escape `<a>${who}</a>`

### 转义字符

除了普通的可打印字符以外，一些特殊有特殊功能的字符可以通过转义字符的形式放入字符串中：

|Code|Output|
|:---:|:---:|
|\0	|空字符|
|\'	|单引号|
|\"	|双引号|
|\\	|反斜杠|
|\n	|换行|
|\r	|回车|
|\v	|垂直制表符|
|\t	|水平制表符|
|\b	|退格|
|\f	|换页|
|\uXXXX	|unicode 码|
|\u{X} ... \u{XXXXXX}	|unicode codepoint |
|\xXX	Latin-1 |字符(x小写)|

### 长字符串(字符串拼接)

> '+

> +=

let longString = "This is a very long string which needs " +
                 "to wrap across multiple lines because " +
                 "otherwise my code is unreadable.";

> /

let longString = "This is a very long string which needs \
to wrap across multiple lines because \
otherwise my code is unreadable.";

> 从字符串中获取单个字符

return 'cat'.charAt(1); // returns "a"

`另一种 (在ECMAScript 5中有所介绍) 是把字符串当作一个类似数组的对象，其中的每个字符对应一个数值索引：`

return 'cat'[1]; // returns "a"

### 字符串比较

熟练使用 C 语言的开发者经常使用 strcmp 函数来比较字符串，但在 JavaScript 中，你只需要使用比较操作符(>/</>=/<=)：

```
var a = "a";
var b = "b";
if (a < b) // true
  print(a + " is less than " + b);
else if (a > b)
  print(a + " is greater than " + b);
else
  print(a + " and " + b + " are equal.");
```

### 基本字符串和字符串对象的区别

`类型强转：基本字符串强转字符串对象并调用字符串对象的方法`

请注意区分 JavaScript 字符串对象和基本字符串值 . ( 对于 Boolean 和Numbers 也同样如此.)

字符串字面量 (通过单引号或双引号定义) 和 直接调用 String 方法(没有通过 new 生成字符串对象实例)的字符串都是基本字符串。`JavaScript会自动将基本字符串转换为字符串对象，`只有将基本字符串转化为字符串对象之后才可以使用字符串对象的方法。当基本字符串需要调用一个字符串对象才有的方法或者查询值的时候(基本字符串是没有这些方法的)，JavaScript 会自动将基本字符串转化为字符串对象并且调用相应的方法或者执行查询。

```
var s_prim = "foo";
var s_obj = new String(s_prim);

console.log(typeof s_prim); // Logs "string"
console.log(typeof s_obj);  // Logs "object"
```
`不能通过eval将new String(thing)生成的字符串对象转换为基本字符串，可以利用valueOf转换`
`当使用 eval时，基本字符串和字符串对象也会产生不同的结果。eval 会将基本字符串作为源代码处理; 而字符串对象则被看作对象处理, 返回对象。 例如：`

```
s1 = "2 + 2";               // creates a string primitive
s2 = new String("2 + 2");   // creates a String object
console.log(eval(s1));      // returns the number 4
console.log(eval(s2));      // returns the string "2 + 2"
```

`利用 valueOf 方法，我们可以将字符串对象转换为其对应的基本字符串。`

```
console.log(eval(s2.valueOf())); // returns the number 4
```

### 属性节

String.prototype
可以为 String 对象增加新的属性。