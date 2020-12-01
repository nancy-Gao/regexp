# regexp
正则表达式特殊字符



## 修饰符
| 修饰符 | 描述 |
|---------| --- |
|[i](#i)|	ignore，执行对大小写不敏感的匹配。|
|[g](#g)|	global，执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。|
|[m](#m)|	multi line，执行多行匹配。|
|[s](#s)|	默认情况下的圆点 . 是 匹配除换行符 \n 之外的任何字符，加上 s 修饰符之后, . 中包含换行符 \n。|

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
默认情况下的圆点 . 是 匹配除换行符 \n 之外的任何字符，加上 s 之后, . 中包含换行符 \n。

```javascript
    var str="google\nrunoob\ntaobao";
    var n1=str.match(/google./);   // 没有使用 s，无法匹配\n null
    var n2=str.match(/runoob./s);  // 使用 s，匹配\n ["runoob\n"]，匹配直到到一行结束
```

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
|(pattern)|匹配 pattern 并获取这一匹配。所获取的匹配可以从产生的 Matches 集合得到，在VBScript 中使用 SubMatches 集合，在JScript 中则使用 $0…$9 属性。要匹配圆括号字符，请使用 '\\(' 或 '\\)'。|
|(?:pattern)	| 匹配 pattern 但不获取匹配结果，也就是说这是一个非获取匹配，不进行存储供以后使用。这在使用 "或" 字符 (\|) 来组合一个模式的各个部分是很有用。例如， 'industr(?:y\|ies) 就是一个比 'industry\|industries' 更简略的表达式。|
|(?=pattern)	| 正向肯定预查（look ahead positive assert），在任何匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如，"Windows(?=95\|98\|NT\|2000)"能匹配"Windows2000"中的"Windows"，但不能匹配"Windows3.1"中的"Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。|
|(?!pattern)	| 正向否定预查(negative assert)，在任何不匹配pattern的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如"Windows(?!95\|98\|NT\|2000)"能匹配"Windows3.1"中的"Windows"，但不能匹配"Windows2000"中的"Windows"。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。|
|(?<=pattern)	| 反向(look behind)肯定预查，与正向肯定预查类似，只是方向相反。例如，"(?<=95\|98\|NT\|2000)Windows"能匹配"2000Windows"中的"Windows"，但不能匹配"3.1Windows"中的"Windows"。|
|(?<!pattern)	| 反向否定预查，与正向否定预查类似，只是方向相反。例如"(?<!95\|98\|NT\|2000)Windows"能匹配"3.1Windows"中的"Windows"，但不能匹配"2000Windows"中的"Windows"。|
|x\|y|匹配 x 或 y。例如，'z\|food' 能匹配 "z" 或 "food"。'(z\|f)ood' 则匹配 "zood" 或 "food"。|
|[xyz]	| 字符集合。匹配所包含的任意一个字符。例如， '[abc]' 可以匹配 "plain" 中的 'a'。|
|[^xyz]	| 负值字符集合。匹配未包含的任意字符。例如， '[^abc]' 可以匹配 "plain" 中的'p'、'l'、'i'、'n'。|
|[a-z]	| 字符范围。匹配指定范围内的任意字符。例如，'[a-z]' 可以匹配 'a' 到 'z' 范围内的任意小写字母字符。|
|[^a-z]	| 负值字符范围。匹配任何不在指定范围内的任意字符。例如，'[^a-z]' 可以匹配任何不在 'a' 到 'z' 范围内的任意字符。|
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


通用的一些模式匹配表达式
