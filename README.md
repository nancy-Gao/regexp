# regexp
正则表达式特殊字符



## 修饰符
| 修饰符 | 描述 |
|---------| --- |
|[i](#i)|	ignore，执行对大小写不敏感的匹配。|
|[g](#g)|	global，执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。|
|[m](#m)|	multi line，执行多行匹配。|
|[s](#s)|	默认情况下的圆点 . 是 匹配除换行符 \n 之外的任何字符，加上 s 修饰符之后, . 中包含换行符 \n。|
|[u](#u)|	u使用unicode码的模式进行匹配。 es6语法|
|[y](#y)|	执行“粘性(sticky)”搜索,匹配从目标字符串的当前位置开始。 es6语法|


## 元字符
| 字符	| 描述 |
| ---- | ---- |
| [\\](#\\) | 将下一个字符标记为一个特殊字符、或一个原义字符、或一个 向后引用、或一个八进制转义符。例如，'n' 匹配字符 "n"。'\n' 匹配一个换行符。序列 '\\' 匹配 "\" 而 "\(" 则匹配 "("。|
| [^](#^)   | 匹配输入字符串的开始位置。如果设置了 RegExp 对象的 Multiline 属性，^ 也匹配 '\n' 或 '\r' 之后的位置。|
| [$](#起始)  |匹配输入字符串的结束位置。如果设置了RegExp 对象的 Multiline 属性，$ 也匹配 '\n' 或 '\r' 之前的位置。|
|[*](#*)|	匹配前面的子表达式零次或多次。例如，zo* 能匹配 "z" 以及 "zoo"。* 等价于{0,}。|
|[+](#+)| 匹配前面的子表达式一次或多次。例如，'zo+' 能匹配 "zo" 以及 "zoo"，但不能匹配 "z"。+ 等价于 {1,}。|
|[?](#?)|	匹配前面的子表达式零次或一次。例如，"do(es)?" 可以匹配 "do" 或 "does" 。? 等价于 {0,1}。|
|[{n}](#{n})| n 是一个非负整数。匹配确定的 n 次。例如，'o{2}' 不能匹配 "Bob" 中的 'o'，但是能匹配 "food" 中的两个 o。|
|[{n,}](#{n,})| n 是一个非负整数。至少匹配n次。例如，'o{2,}' 不能匹配 "Bob" 中的 'o'，但能匹配 "foooood" 中的所有 o。'o{1,}' 等价于 'o+'。'o{0,}' 则等价于 'o*'。|
|[{n,m}](#{n,m})| m 和 n 均为非负整数，其中n <= m。最少匹配 n 次且最多匹配 m 次。例如，"o{1,3}" 将匹配 "fooooood" 中的前三个 o。'o{0,1}' 等价于 'o?'。请注意在逗号和两个数之间不能有空格。|
|[?](#非贪婪)| 当该字符紧跟在任何一个其他限制符 (*, +, ?, {n}, {n,}, {n,m}) 后面时，匹配模式是非贪婪的。非贪婪模式尽可能少的匹配所搜索的字符串，而默认的贪婪模式则尽可能多的匹配所搜索的字符串。例如，对于字符串 "oooo"，'o+?' 将匹配单个 "o"，而 'o+' 将匹配所有 'o'。|
|[.](#.)| 匹配除换行符（\n、\r）之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用像"(.|\\n)"的模式。|
|[(pattern)](#(pattern))|匹配 pattern 并获取这一匹配。所获取的匹配可以从产生的 Matches 集合得到，在JScript 中则使用 $1…$9 属性。要匹配圆括号字符，请使用 '\\(' 或 '\\)'。|
|[(?:pattern)](#(?pattern))| 匹配 pattern 但不获取匹配结果，也就是说这是一个非获取匹配，不进行存储供以后使用。这在使用 "或" 字符 (\|) 来组合一个模式的各个部分是很有用。例如， 'industr(?:y\|ies) 就是一个比 'industry\|industries' 更简略的表达式。|
|[(?=pattern)](#(?=pattern))| 先行断言（look ahead positive assert），在任何匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如，"Windows(?=95\|98\|NT\|2000)"能匹配"Windows2000"中的"Windows"，但不能匹配"Windows3.1"中的"Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。|
|[(?!pattern)](#(?!pattern))| 先行否定断言(negative assert)，在任何不匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如"Windows(?!95\|98\|NT\|2000)"能匹配"Windows3.1"中的"Windows"，但不能匹配"Windows2000"中的"Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。|
|[(?<=pattern)](#(?<=pattern))| 后行断言(look behind)，与先行断言类似，只是方向相反。例如，"(?<=95\|98\|NT\|2000)Windows"能匹配"2000Windows"中的"Windows"，但不能匹配"3.1Windows"中的"Windows"。|
|[(?<!pattern)](#(?<!pattern))| 后行否定断言，与先行否定断言类似，只是方向相反。例如"(?<!95\|98\|NT\|2000)Windows"能匹配"3.1Windows"中的"Windows"，但不能匹配"2000Windows"中的"Windows"。|
|[x\|y](#xy)|匹配 x 或 y。例如，'z\|food' 能匹配 "z" 或 "food"。'(z\|f)ood' 则匹配 "zood" 或 "food"。|
|[\[xyz\]](#xyz)	| 字符集合。匹配所包含的任意一个字符。例如， '[abc]' 可以匹配 "plain" 中的 'a'。|
|[\[^xyz\]](#^xyz)	| 负值字符集合。匹配未包含的任意字符。例如， '[^abc]' 可以匹配 "plain" 中的'p'、'l'、'i'、'n'。|
|[\[a-z\]](#a-z)	| 字符范围。匹配指定范围内的任意字符。例如，'[a-z]' 可以匹配 'a' 到 'z' 范围内的任意小写字母字符。|
|[\[^a-z\]](#^a-z))	| 负值字符范围。匹配任何不在指定范围内的任意字符。例如，'[^a-z]' 可以匹配任何不在 'a' 到 'z' 范围内的任意字符。|
|\b	| 匹配一个单词边界，也就是指单词和空格间的位置。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。|
|\B	| 匹配非单词边界。'er\B' 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。|
|\cx | 匹配由 x 指明的控制字符。例如， \cM 匹配一个 Control-M 或回车符。x 的值必须为 A-Z 或 a-z 之一。否则，将 c 视为一个原义的 'c' 字符。|
|\d	| 匹配一个数字字符。等价于 [0-9]。|
|\D	|匹配一个非数字字符。等价于 [^0-9]。|
|\f	|匹配一个换页符。等价于 \x0c 和 \cL。|
|\n	|匹配一个换行符。等价于 \x0a 和 \cJ。|
|\r	|匹配一个回车符。等价于 \x0d 和 \cM。|
|\s	|匹配任何空白字符，包括空格、制表符、换页符等等。等价于 [ \f\n\r\t\v]。|
|\S	|匹配任何非空白字符。等价于 [^ \f\n\r\t\v]。|
|\t	|匹配一个制表符。等价于 \x09 和 \cI。|
|\v	|匹配一个垂直制表符。等价于 \x0b 和 \cK。|
|\w	|匹配字母、数字、下划线。等价于'[A-Za-z0-9_]'。|
|\W	|匹配非字母、数字、下划线。等价于 '[^A-Za-z0-9_]'。|
|\xn	|匹配 n，其中 n 为十六进制转义值。十六进制转义值必须为确定的两个数字长。例如，'\x41' 匹配 "A"。'\x041' 则等价于 '\x04' & "1"。正则表达式中可以使用 ASCII 编码。|
|\num	|匹配 num，其中 num 是一个正整数。对所获取的匹配的引用。例如，'(.)\1' 匹配两个连续的相同字符。|
|\n	|标识一个八进制转义值或一个向后引用。如果 \n 之前至少 n 个获取的子表达式，则 n 为向后引用。否则，如果 n 为八进制数字 (0-7)，则 n 为一个八进制转义值。|
|\nm	|标识一个八进制转义值或一个向后引用。如果 \nm 之前至少有 nm 个获得子表达式，则 nm 为向后引用。如果 \nm 之前至少有 n 个获取，则 n 为一个后跟文字 m 的向后引用。如果前面的条件都不满足，若 n 和 m 均为八进制数字 (0-7)，则 \nm 将匹配八进制转义值 nm。|
|\nml	|如果 n 为八进制数字 (0-3)，且 m 和 l 均为八进制数字 (0-7)，则匹配八进制转义值 nml。|
|\un	|匹配 n，其中 n 是一个用四个十六进制数字表示的 Unicode 字符。例如， \u00A9 匹配版权符号 (?)。|


## 运算符优先级

正则表达式从左到右进行计算，并遵循优先级顺序，这与算术表达式非常类似。
相同优先级的从左到右进行运算，不同优先级的运算先高后低。下表从最高到最低说明了各种正则表达式运算符的优先级顺序：

|运算符|描述|
|-----|---|
|\|转义符|
|(),(?:),(?=),[]|圆括号和方括号|
|*,+,?,{n},{n,}{n,m}|限定符|
|^,$,\元字符，任何字符|定位点和序列|
|\||替换，或操作|

## [i](#i)

<i id="i"></i>
执行对大小写不敏感的匹配。

```javascript
    var reg = /abc/i
    reg.test('Abc') // true
```

## [g](#g)

<i id="g"></i>
执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。

```javascript
    var reg = /abc/g;
    'abcabcabc'.match(reg); // ["abc", "abc", "abc"]
```
```javascript
    var reg = /abc/;
    'abcabcabc'.match(reg); // ["abc"]
```

## [m](#m)

<i id="m"></i>
执行多行匹配。

```javascript
    var reg = /^abc/gm;
    `abcabc
    abc`.match(reg) // ["abc", "abc"]
```
```javascript
    var reg = /^abc/g;
    `abcabc
    abc`.match(reg) // ["abc"]
```
当匹配多行开头时和只使用g修饰符有所区别


## [s](#s)

<i id="s"></i>
es6增加，默认情况下的圆点 . 是 匹配除换行符 \n 之外的任何字符，加上 s 之后, . 中包含换行符 \n。

```javascript
    var str="google\nrunoob\ntaobao";
    var n1=str.match(/google./);   // 没有使用 s，无法匹配\n null
    var n2=str.match(/runoob./s);  // 使用 s，匹配\n ["runoob\n"]，匹配直到到一行结束
```

## [u](#u)

<i id="u"></i>
ES6 对正则表达式添加了u修饰符，含义为“Unicode 模式”，用来正确处理大于\uFFFF的 Unicode 字符。也就是说，会正确处理四个字节的 UTF-16 编码

```javascript
    /^\uD83D/u.test('\uD83D\uDC2A') // false
    /^\uD83D/.test('\uD83D\uDC2A') // true
```
\uD83D\uDC2A是一个四个字节的 UTF-16 编码，代表一个字符。但是，ES5 不支持四个字节的 UTF-16 编码，会将其识别为两个字符，导致第二行代码结果为true。加了u修饰符以后，ES6 就会识别其为一个字符，所以第一行代码结果为false。

一旦加上u修饰符号，就会修改下面这些正则表达式的行为。

（1）点字符

点（.）字符在正则表达式中，含义是除了换行符以外的任意单个字符。对于码点大于0xFFFF的 Unicode 字符，点字符不能识别，必须加上u修饰符。


```javascript
    var s = '𠮷';
    /^.$/.test(s) // false
    /^.$/u.test(s) // true
```

上面代码表示，如果不添加u修饰符，正则表达式就会认为字符串为两个字符，从而匹配失败。

（2）Unicode 字符表示法

ES6 新增了使用大括号表示 Unicode 字符，这种表示法在正则表达式中必须加上u修饰符，才能识别当中的大括号，否则会被解读为量词。

```javascript
    /\u{61}/.test('a') // false
    /\u{61}/u.test('a') // true
    /\u{20BB7}/u.test('𠮷') // true
```

上面代码表示，如果不加u修饰符，正则表达式无法识别\u{61}这种表示法，只会认为这匹配 61 个连续的u。

（3）量词

使用u修饰符后，所有量词都会正确识别码点大于0xFFFF的 Unicode 字符。

```javascript
    /a{2}/.test('aa') // true
    /a{2}/u.test('aa') // true
    /𠮷{2}/.test('𠮷𠮷') // false
    /𠮷{2}/u.test('𠮷𠮷') // true
```

（4）预定义模式

u修饰符也影响到预定义模式，能否正确识别码点大于0xFFFF的 Unicode 字符。

```javascript
    /^\S$/.test('𠮷') // false
    /^\S$/u.test('𠮷') // true
```

上面代码的\S是预定义模式，匹配所有非空白字符。只有加了u修饰符，它才能正确匹配码点大于0xFFFF的 Unicode 字符。

利用这一点，可以写出一个正确返回字符串长度的函数。

```javascript
    function codePointLength(text) {
      var result = text.match(/[\s\S]/gu);
      return result ? result.length : 0;
    }
    
    var s = '𠮷𠮷';
    
    s.length // 4
    codePointLength(s) // 2
```

（5）i 修饰符

有些 Unicode 字符的编码不同，但是字型很相近，比如，\u004B与\u212A都是大写的K。

```javascript
    /[a-z]/i.test('\u212A') // false
    /[a-z]/iu.test('\u212A') // true
```

上面代码中，不加u修饰符，就无法识别非规范的K字符。

（6）转义

没有u修饰符的情况下，正则中没有定义的转义（如逗号的转义\,）无效，而在u模式会报错。

```javascript
    /\,/ // /\,/
    /\,/u // 报错 
```

上面代码中，没有u修饰符时，逗号前面的反斜杠是无效的，加了u修饰符就报错。

## [y](#y)

<i id="y"></i>
ES6 还为正则表达式添加了y修饰符，叫做“粘连”（sticky）修饰符。
y修饰符的作用与g修饰符类似，也是全局匹配，后一次匹配都从上一次匹配成功的下一个位置开始。不同之处在于，g修饰符只要剩余位置中存在匹配就可，而y修饰符确保匹配必须从剩余的第一个位置开始，这也就是“粘连”的涵义。

```javascript
    var s = 'aaa_aa_a';
    var r1 = /a+/g;
    var r2 = /a+/y;
    
    r1.exec(s) // ["aaa"]
    r2.exec(s) // ["aaa"]
    
    r1.exec(s) // ["aa"]
    r2.exec(s) // null
```


## [\\](#\\)

<i id="\"></i>
将下一个字符标记为一个特殊字符、或一个原始字符、或一个向后引用、或一个八进制转义符；
例如，"n"匹配字符"n"，"\n"匹配一个换行符。这里\是元字符的一部分，有特殊意义。
"\xxx"匹配八进制数xxx规定的字符。
串行"\\"匹配"\"，"\("匹配"("。这里\作用于特殊字符前表示后面的字符不在乎有特殊意义。

## [^](#^)

<i id="^"></i>
匹配输入的字符串开始的位置，如果是/m模式也匹配换行(\r、\n)之后的起始位置

```javascript
    'industryaaa'.match(/^industry/g); // ["industry"]
    'industryaaa\nindustrybb'.match(/^industry/mg); // ["industry", "industry"]
```

## [$](#起始)

<i id="起始"></i>
匹配输入的字符串结束的位置，如果是/m模式也匹配换行(\r、\n)之后的结束位置

```javascript
    'aaaindustry'.match(/industry$/g); // ["industry"]
    'aaaindustry\nbbbindustry'.match(/industry$/mg); // ["industry", "industry"]
```

## [*](#*)

<i id="*"></i>
匹配前面的子表达式零次或多次

```javascript
    'aaaindustry'.match(/a*industry/g); // ["aaaindustry"]
    'aaaindustry\nbbbindustry'.match(/a*industry/mg); // ["aaaindustry", "industry"]
```

## [+](#+)

<i id="+"></i>
匹配前面的子表达式1次或多次

```javascript
    'aaaindustry'.match(/a*industry/g); // ["aaaindustry"]
    'aaaindustry\nbbbindustry'.match(/a*industry/mg); // ["aaaindustry"]
    // 跟*对比可以看出区别
```

## [?](#?)

<i id="?"></i>
匹配前面的子表达式0次或1次

```javascript
    'aaaindustry'.match(/a?industry/g); // ["aindustry"]
    'aaaindustry\nbbbindustry'.match(/a?industry/mg); // ["aindustry", "industry"]
```

## [{n}](#{n})

<i id="{n}"></i>
匹配前面的子表达式n次

```javascript
    'aaaindustry'.match(/a{3}industry/g); // ["aaaindustry"]
    'aaaindustry\nbbbindustry'.match(/a{2}industry/mg); // ["aaindustry"]
```

## [{n,}](#{n,})

<i id="{n,}"></i>
匹配前面的子表达式n次或更多次

```javascript
    'aaaindustry'.match(/a{2,}industry/g); // ["aaaindustry"]
    'aaaindustry\nbbbindustry'.match(/a{3,}industry/mg); // ["aaaindustry"]
```

## [{n,m}](#{n,m})

<i id="{n,m}"></i>
匹配前面的子表达式n次至m次

```javascript
    'aaaindustry'.match(/a{2,3}industry/g); // ["aaaindustry"]
    'aaaindustry\nbbbindustry'.match(/a{3,4}industry/mg); // ["aaaindustry"]
```

## [?](#非贪婪)

<i id="非贪婪"></i>
匹配前面的子表达式包含限制以上限制符，则匹配已非贪婪模式匹配结果

```javascript
    "oooo".match(/o{1,3}?/g); // ["o", "o", "o", "o"] 全局可以匹配出四个
    "aooo".match(/ao{1,3}?/g); // ["ao"] 从左到右匹配到的最小的字符长度
    'aaaindustry'.match(/a{1,3}?industry/g); // ["aaaindustry"] 从左到右匹配到的最小的字符长度
```

## [.](#.)

<i id="."></i>
匹配除\r,\n的任意单个字符

```javascript
    "oooo".match(/.{1,3}/g); // ["ooo", "o"]
    "哈哈".match(/.{1,3}/g); // ["哈哈"] 可以匹配中文字符
    'aaaindustry\nbbbindustry'.match(/.{3,4}industry/g); // ["aaaindustry", "bbbindustry"]
```

## [(pattern)](#(pattern))

<i id="(pattern)"></i>
匹配一个pattern的表示式，并且保留该表达式匹配到的字符。

js中使用match方法
如果未使用g标志，则仅返回第一个完整匹配及其相关的捕获组（Array）。 在这种情况下，返回的项目将具有如下所述的其他属性

    groups: 一个捕获组数组 或 undefined（如果没有定义命名捕获组）
    index: 匹配的结果的开始位置
    input: 搜索的字符串
    Array第一个元素是匹配字符串，第二个元素是捕获的字符串
    
如果使用g标志，则返回都有的匹配字符数组（Array）


```javascript
    "i am happy".match(/(\S+\b)/); // ["i", "i", index: 0, input: "i am happy", groups: undefined] 未使用g标志也没有命名捕获组
    "2020-09-20".match(/(?<year>\d+)-(?<month>\d+)-(?<day>\d+)/) // (?<name>pattern) 对捕获组命名 
    // ["2020-09-20", "2020", "09", "20", index: 0, input: "2020-09-20", groups: {…}]
    // group: {year: "2020", month: "09", day: "20"}
    // 如果不进行命名也可以在RegExp对象中拿到捕获的内容
     RegExp.$1; // 2020
     "2020-09-20".replace(/(?<year>\d+)-(?<month>\d+)-(?<day>\d+)/, '$2-$3-$1') // "09-20-2020"
     // replace方法中的$1等同 RegExp.$1
```

## [(?:pattern)](#(?pattern))

<i id="(?pattern)"></i>
匹配一个pattern的表示式，非捕获，但是不保留该表达式匹配到的字符。

```javascript
    "i am happy".match(/(?:\S+\b)/); // ["i", index: 0, input: "i am happy", groups: undefined]
    "2020-09-20".match(/(?:\d+)-(?:\d+)-(?:\d+)/); // ["2020-09-20", index: 0, input: "2020-09-20", groups: undefined]
    "industry".match(/industr(?:y|ies)/) // 仅仅是为了或的字符查找，不捕获匹配类型
```

## [(?=pattern)](#(?=pattern))

<i id="(?=pattern)"></i>
先行断言，非捕获，匹配一个pattern的表示式, 然后开始匹配左边的字符串。匹配字符不包含pattern。

```javascript
    "i am happy".match(/i (?=\S+\b)/); // ["i ", index: 0, input: "i am happy", groups: undefined]
    "start 2020-09-20".match(/start (?=\d+)-(?:\d+)-(?:\d+)/); // ["2020-09-20", index: 0, input: "2020-09-20", groups: undefined]
```
检测获取同一种文件后缀的文件名

```javascript
    'd.jpg'.match(/\w(?=\.jpg)/);
     // ["d"]
```

## [(?!pattern)](#(?!pattern))

<i id="(?!pattern)"></i>
先行否定断言，非捕获，不匹配一个pattern的表示式, 然后开始匹配左边的字符串。匹配字符不包含pattern。

```javascript
    "i am happy i ".match(/i (?!\S+\b)/); // ["i ", index: 16, input: "i am happy i ", groups: undefined]
    "start aa-09-20 start 2020-09-20".match(/start (?!\d+-\d+-\d+)/); // ["start ", index: 0, input: "start aa-09-20 start 2020-09-20", groups: undefined]
    // 不是日期的字符串左边匹配的内容
```

检测不是指定文件后缀的文件
```javascript
    'c.html'.match(/.+(?!=\.jpg,?)/g)
    // ["c.html"]
```


## [(?<=pattern)](#(?<=pattern))

<i id="(?<=pattern)"></i>
后行断言，非捕获，匹配一个pattern的表示式, 然后开始匹配右边的字符串。匹配字符不包含pattern。

```javascript
    "i am happy".match(/(?<=\S+) happy/); // [" happy", index: 4, input: "i am happy", groups: undefined]
    "2020-09-20 end".match(/(?<=\d+)-(?:\d+)-(?:\d+) end/); // ["-09-20 end", index: 4, input: "2020-09-20 end", groups: undefined]
    "sss\n 2020-09-20 end".match(/.*(?<=\d+)-(?:\d+)-(?:\d+) end/); // [" 2020-09-20 end", index: 4, input: "sss↵ 2020-09-20 end", groups: undefined]
```

获取ua的安卓版本号码
```javascript
    'Mozilla/5.0 (Linux; Android 5.0; SM-G900P Build/LRX21T) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.80 Mobile Safari/537.36'.match(/(?<=android\s)\d\.\d/i)
    // ["5.0", index: 28, input: "Mozilla/5.0 (Linux; Android 5.0; SM-G900P Build/LR…e Gecko) Chrome/86.0.4240.80 Mobile Safari/537.36", groups: undefined]
```
获取document
```javascript

```

## [(?<!pattern)](#(?<!pattern))

<i id="(?<!pattern)"></i>
后行否定断言，非捕获，不匹配一个pattern的表示式, 然后开始匹配右边的字符串。匹配字符不包含pattern。

```javascript
    " happy i am happy".match(/(?<!\S+) happy/); // [" happy", index: 0, input: " happy i am happy", groups: undefined]
```

## [x\|y](#xy)

<i id="xy"></i>
或，包含多种匹配表达式

```javascript
    "window2003".match(/window(?:2003|2009)/); // ["window2003", index: 0, input: "window2003", groups: undefined]
```

## [\[xyz\]](#xyz)

<i id="xyz"></i>
可包含罗列的字符集合

```javascript
    "2020-09-20".match(/[0123456789]+/) // ["2020", index: 0, input: "2020-09-20", groups: undefined]
```

## [\[^xyz\]](#^xyz)

<i id="^xyz"></i>
不包含罗列的字符集合

```javascript
    "2020-09-20".match(/[^20]+/) // ["-", index: 4, input: "2020-09-20", groups: undefined]
```

## [\[a-z\]](#a-z)

<i id="a-z"></i>
包含指定范围的字符集合

```javascript
    "2020-09-20".match(/[0-9]+/) // ["2020", index: 0, input: "2020-09-20", groups: undefined]
```

## [\[^a-z\]](#^a-z)

<i id="^a-z"></i>
不包含指定范围的字符集合

```javascript
    "2020-09-20".match(/[^0-9]+/) // ["-", index: 4, input: "2020-09-20", groups: undefined]
```


# JavaScript 的正则表达式方法

RegExp.test: 返回 true 或 false。
RegExp.exec: 它返回一个数组（未匹配到则返回 null
String.match: 返回一个数组，在未匹配到时会返回 null
String.matchAll: 回一个迭代器（iterator）
String.replace: 返回使用替换字符串替换掉匹配到的子字符串的字符串
String.search: 返回匹配到的位置索引，或者在失败时返回-1
String.split：返回分隔后的子字符串存储到数组

## 创建正则表达式

````javascript
    var re = /ab+c/;
    var re = new RegExp('ab+c');
````


##通用的一些模式匹配表达式
Email地址：^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$

日期格式：^\d{4}-\d{1,2}-\d{1,2}

一年的12个月(01～09和1～12)：^(0?[1-9]|1[0-2])$

一个月的31天(01～09和1～31)：^((0?[1-9])|((1|2)[0-9])|30|31)$
 
中文字符的正则表达式：[\u4e00-\u9fa5]

IP地址：\d+\.\d+\.\d+\.\d+

域名：/\w+\.\w+(\w+\.)+.\w+/
