title: Python算法中的库函数

top: true

categories: 

- 笔试

tags:

- python

description: <center><h3>Python算法中的库函数，为了鄙视</h3></center>

---

<!--more-->

# 1.常用内置函数：(不用import就可以直接使用)

eval(str) 表示合法的python表达式，返回这个表达式

## 类型转换函数

　　chr(i) 把一个ASCII数值,变成字符

　　ord(i) 把一个字符或者unicode字符,变成ASCII数值

　　oct(x) 把整数x变成八进制表示的字符串

　　hex(x) 把整数x变成十六进制表示的字符串

　　str(obj) 得到obj的字符串描述

　　list(seq) 把一个sequence转换成一个list

　　tuple(seq) 把一个sequence转换成一个tuple

　　dict(),dict(list) 转换成一个dictionary

　　int(x) 转换成一个integer

　　long(x) 转换成一个long interger

　　float(x) 转换成一个浮点数

　　complex(x) 转换成复数

## 常用函数

　　max(...) 求最大值

　　min(...) 求最小值

​		abs() 函数返回数字的绝对值

​		divmod(a,b) 函数把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a // b, a % b)

​		all() 函数用于判断给定的可迭代参数 iterable 中的所有元素是否都为 TRUE，如果是返回 True，否则返回 False。

​		元素除了是 0、空、None、False 外都算 True。iterable -- 元组或列表。

​		any() 函数用于判断给定的可迭代参数 iterable 是否全部为 False，则返回 False，如果有一个为 True，则返回 True。

​		元素除了是 0、空、FALSE 外都算 TRUE。

​		enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 		for 循环当中。

```
for i, element in enumerate(seq): 
	print i, element
```

​		**set()** 函数创建一个无序不重复元素集，可进行关系测试，删除重复数据，还可以计算交集、差集、并集等。

```
>>>x = set('runoob')
>>> y = set('google')
>>> x, y
(set(['b', 'r', 'u', 'o', 'n']), set(['e', 'o', 'g', 'l']))   # 重复的被删除
>>> x & y         # 交集
set(['o'])
>>> x | y         # 并集
set(['b', 'e', 'g', 'l', 'o', 'n', 'r', 'u'])
>>> x - y         # 差集
set(['r', 'b', 'u', 'n'])
>>>
```



# 2. math

取大于等于x的最小的整数值，如果x是一个整数，则返回x
\>>> math.ceil(4.12)
5

floor()取小于等于x的最大的整数值，如果x是一个整数，则返回自身
\>>> math.floor(4.999)
4 

e表示一个常量
\>>> math.e
2.718281828459045

exp()返回math.e(其值为2.71828)的x次方
\>>> math.exp(2)
7.38905609893065

fabs()返回x的绝对值
\>>> math.fabs(-0.03)
0.03

factorial()取x的阶乘的值
\>>> math.factorial(3)
6

sqrt()求x的平方根
\>>> math.sqrt(100)

# 3.和操作系统相关的调用

## 系统相关的信息模块 import sys

sys.stdin sys.stdout  sys.stderr 分别表示标准输入输出,错误输出的文件对象.

sys.stdin.readline() 从标准输入读一行 sys.stdout.write("a") 屏幕输出a

sys.exit(exit_code) 退出程序

sys.path 是一个list,指明所有查找module，package的路径.

# 4.文件操作

### 打开文件

f = open("filename", "r") r只读 w写 rw读写 rb读二进制 wb写二进制 w+写追加

### 读写文件

f.write("a") f.write(str) 写一字符串 f.writeline() f.readlines() 与下read类同

f.read() 全读出来 f.read(size) 表示从文件中读取size个字符

f.readline() 读一行,到文件结尾,返回空串. f.readlines() 读取全部，返回一个list. list每个元素表示一行，包含" "

### 关闭文件

f.close()

# 5.[正则表达式](https://www.runoob.com/python/python-reg-expressions.html)

## import re

## re.match函数

re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()就返回none。

**函数语法**：

```
re.match(pattern, string, flags=0)
```

匹配成功re.match方法返回一个匹配的对象，否则返回None。

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串。                                             |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：[正则表达式修饰符 - 可选标志](https://www.runoob.com/python/python-reg-expressions.html#flags) |

| 匹配对象方法 | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| group(num=0) | 匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。 |
| groups()     | 返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。     |

## re.search方法

re.search 扫描整个字符串并返回第一个成功的匹配。

函数语法：

```
re.search(pattern, string, flags=0)
```

函数参数说明：

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串。                                             |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。 |

匹配成功re.search方法返回一个匹配的对象，否则返回None。

## re.match与re.search的区别

re.match只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回None；而re.search匹配整个字符串，直到找到一个匹配。

## 检索和替换

Python 的 re 模块提供了re.sub用于替换字符串中的匹配项。

语法：

```
re.sub(pattern, repl, string, count=0, flags=0)
```

参数：

- pattern : 正则中的模式字符串。
- repl : 替换的字符串，也可为一个函数。
- string : 要被查找替换的原始字符串。
- count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。

### re.compile 函数

compile 函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用。

语法格式为：

```
re.compile(pattern[, flags])
```

参数：

- **pattern** : 一个字符串形式的正则表达式

- **flags** : 可选，表示匹配模式，比如忽略大小写，多行模式等，具体参数为：

  1. **re.I** 忽略大小写
  2. **re.L** 表示特殊字符集 \w, \W, \b, \B, \s, \S 依赖于当前环境
  3. **re.M** 多行模式
  4. **re.S** 即为 **.** 并且包括换行符在内的任意字符（**.** 不包括换行符）
  5. **re.U** 表示特殊字符集 \w, \W, \b, \B, \d, \D, \s, \S 依赖于 Unicode 字符属性数据库
  6. **re.X** 为了增加可读性，忽略空格和 **#** 后面的注释

  ```
  >>>import re
  >>> pattern = re.compile(r'\d+')                    # 用于匹配至少一个数字
  >>> m = pattern.match('one12twothree34four')        # 查找头部，没有匹配
  >>> print m
  None
  >>> m = pattern.match('one12twothree34four', 2, 10) # 从'e'的位置开始匹配，没有匹配
  >>> print m
  None
  >>> m = pattern.match('one12twothree34four', 3, 10) # 从'1'的位置开始匹配，正好匹配
  >>> print m                                         # 返回一个 Match 对象
  <_sre.SRE_Match object at 0x10a42aac0>
  >>> m.group(0)   # 可省略 0
  '12'
  >>> m.start(0)   # 可省略 0
  3
  >>> m.end(0)     # 可省略 0
  5
  >>> m.span(0)    # 可省略 0
  (3, 5)
  ```

  

### findall

在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表。

**注意：** match 和 search 是匹配一次 findall 匹配所有。

语法格式为：

```
findall(string[, pos[, endpos]])
```

参数：

- **string** : 待匹配的字符串。
- **pos** : 可选参数，指定字符串的起始位置，默认为 0。
- **endpos** : 可选参数，指定字符串的结束位置，默认为字符串的长度。

### re.finditer

和 findall 类似，在字符串中找到正则表达式所匹配的所有子串，并把它们作为一个迭代器返回。

```
re.finditer(pattern, string, flags=0)
```

参数：

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串。                                             |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：[正则表达式修饰符 - 可选标志](https://www.runoob.com/python/python-reg-expressions.html#flags) |

## 正则表达式对象

### re.RegexObject

re.compile() 返回 RegexObject 对象。

### re.MatchObject

group() 返回被 RE 匹配的字符串。

- **start()** 返回匹配开始的位置
- **end()** 返回匹配结束的位置
- **span()** 返回一个元组包含匹配 (开始,结束) 的位置

## 正则表达式模式

模式字符串使用特殊的语法来表示一个正则表达式：

字母和数字表示他们自身。一个正则表达式模式中的字母和数字匹配同样的字符串。

多数字母和数字前加一个反斜杠时会拥有不同的含义。

标点符号只有被转义时才匹配自身，否则它们表示特殊的含义。

反斜杠本身需要使用反斜杠转义。

由于正则表达式通常都包含反斜杠，所以你最好使用原始字符串来表示它们。模式元素(如 r'\t'，等价于 '\\t')匹配相应的特殊字符。

下表列出了正则表达式模式语法中的特殊元素。如果你使用模式的同时提供了可选的标志参数，某些模式元素的含义会改变。

| 模式        | 描述                                                         |
| :---------- | :----------------------------------------------------------- |
| ^           | 匹配字符串的开头                                             |
| $           | 匹配字符串的末尾。                                           |
| .           | 匹配任意字符，除了换行符，当re.DOTALL标记被指定时，则可以匹配包括换行符的任意字符。 |
| [...]       | 用来表示一组字符,单独列出：[amk] 匹配 'a'，'m'或'k'          |
| [^...]      | 不在[]中的字符：[^abc] 匹配除了a,b,c之外的字符。             |
| re*         | 匹配0个或多个的表达式。                                      |
| re+         | 匹配1个或多个的表达式。                                      |
| re?         | 匹配0个或1个由前面的正则表达式定义的片段，非贪婪方式         |
| re{ n}      | 精确匹配 n 个前面表达式。例如， **o{2}** 不能匹配 "Bob" 中的 "o"，但是能匹配 "food" 中的两个 o。 |
| re{ n,}     | 匹配 n 个前面表达式。例如， o{2,} 不能匹配"Bob"中的"o"，但能匹配 "foooood"中的所有 o。"o{1,}" 等价于 "o+"。"o{0,}" 则等价于 "o*"。 |
| re{ n, m}   | 匹配 n 到 m 次由前面的正则表达式定义的片段，贪婪方式         |
| a\| b       | 匹配a或b                                                     |
| (re)        | 对正则表达式分组并记住匹配的文本                             |
| (?imx)      | 正则表达式包含三种可选标志：i, m, 或 x 。只影响括号中的区域。 |
| (?-imx)     | 正则表达式关闭 i, m, 或 x 可选标志。只影响括号中的区域。     |
| (?: re)     | 类似 (...), 但是不表示一个组                                 |
| (?imx: re)  | 在括号中使用i, m, 或 x 可选标志                              |
| (?-imx: re) | 在括号中不使用i, m, 或 x 可选标志                            |
| (?#...)     | 注释.                                                        |
| (?= re)     | 前向肯定界定符。如果所含正则表达式，以 ... 表示，在当前位置成功匹配时成功，否则失败。但一旦所含表达式已经尝试，匹配引擎根本没有提高；模式的剩余部分还要尝试界定符的右边。 |
| (?! re)     | 前向否定界定符。与肯定界定符相反；当所含表达式不能在字符串当前位置匹配时成功 |
| (?> re)     | 匹配的独立模式，省去回溯。                                   |
| \w          | 匹配字母数字及下划线                                         |
| \W          | 匹配非字母数字及下划线                                       |
| \s          | 匹配任意空白字符，等价于 **[ \t\n\r\f]**。                   |
| \S          | 匹配任意非空字符                                             |
| \d          | 匹配任意数字，等价于 [0-9].                                  |
| \D          | 匹配任意非数字                                               |
| \A          | 匹配字符串开始                                               |
| \Z          | 匹配字符串结束，如果是存在换行，只匹配到换行前的结束字符串。 |
| \z          | 匹配字符串结束                                               |
| \G          | 匹配最后匹配完成的位置。                                     |
| \b          | 匹配一个单词边界，也就是指单词和空格间的位置。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。 |
| \B          | 匹配非单词边界。'er\B' 能匹配 "verb" 中的 'er'，但不能匹配 "never" 中的 'er'。 |
| \n, \t, 等. | 匹配一个换行符。匹配一个制表符。等                           |
| \1...\9     | 匹配第n个分组的内容。                                        |
| \10         | 匹配第n个分组的内容，如果它经匹配。否则指的是八进制字符码的表达式。 |

[^abc]: 



