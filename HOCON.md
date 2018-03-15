<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [HOCON（人性化配置对象表示法，Human-Optimized Config Object Notation）](#hocon%E4%BA%BA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE%E5%AF%B9%E8%B1%A1%E8%A1%A8%E7%A4%BA%E6%B3%95human-optimized-config-object-notation)
  - [目标/背景](#%E7%9B%AE%E6%A0%87%E8%83%8C%E6%99%AF)
  - [定义](#%E5%AE%9A%E4%B9%89)
  - [语法](#%E8%AF%AD%E6%B3%95)
    - [和JSON一样的地方](#%E5%92%8Cjson%E4%B8%80%E6%A0%B7%E7%9A%84%E5%9C%B0%E6%96%B9)
    - [注释](#%E6%B3%A8%E9%87%8A)
    - [对根结构更宽松的要求](#%E5%AF%B9%E6%A0%B9%E7%BB%93%E6%9E%84%E6%9B%B4%E5%AE%BD%E6%9D%BE%E7%9A%84%E8%A6%81%E6%B1%82)
    - [键值分隔符](#%E9%94%AE%E5%80%BC%E5%88%86%E9%9A%94%E7%AC%A6)
    - [逗号](#%E9%80%97%E5%8F%B7)
    - [空白](#%E7%A9%BA%E7%99%BD)
    - [重复键与对象合并](#%E9%87%8D%E5%A4%8D%E9%94%AE%E4%B8%8E%E5%AF%B9%E8%B1%A1%E5%90%88%E5%B9%B6)
    - [不加引号的字符串](#%E4%B8%8D%E5%8A%A0%E5%BC%95%E5%8F%B7%E7%9A%84%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [多行字符串](#%E5%A4%9A%E8%A1%8C%E5%AD%97%E7%AC%A6%E4%B8%B2)
    - [值连结](#%E5%80%BC%E8%BF%9E%E7%BB%93)
      - [字符串值连结](#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%80%BC%E8%BF%9E%E7%BB%93)
      - [数组值连结和对象值连结](#%E6%95%B0%E7%BB%84%E5%80%BC%E8%BF%9E%E7%BB%93%E5%92%8C%E5%AF%B9%E8%B1%A1%E5%80%BC%E8%BF%9E%E7%BB%93)
      - [注意：引用之间含有空白的值连结](#%E6%B3%A8%E6%84%8F%E5%BC%95%E7%94%A8%E4%B9%8B%E9%97%B4%E5%90%AB%E6%9C%89%E7%A9%BA%E7%99%BD%E7%9A%84%E5%80%BC%E8%BF%9E%E7%BB%93)
      - [注意：不含有逗号或换行符的数组](#%E6%B3%A8%E6%84%8F%E4%B8%8D%E5%90%AB%E6%9C%89%E9%80%97%E5%8F%B7%E6%88%96%E6%8D%A2%E8%A1%8C%E7%AC%A6%E7%9A%84%E6%95%B0%E7%BB%84)
    - [路径表达式](#%E8%B7%AF%E5%BE%84%E8%A1%A8%E8%BE%BE%E5%BC%8F)
    - [作为键的路径表达式](#%E4%BD%9C%E4%B8%BA%E9%94%AE%E7%9A%84%E8%B7%AF%E5%BE%84%E8%A1%A8%E8%BE%BE%E5%BC%8F)
    - [引用](#%E5%BC%95%E7%94%A8)
      - [自引用](#%E8%87%AA%E5%BC%95%E7%94%A8)
      - [键值分隔符 `+=`](#%E9%94%AE%E5%80%BC%E5%88%86%E9%9A%94%E7%AC%A6-)
      - [自引用举例](#%E8%87%AA%E5%BC%95%E7%94%A8%E4%B8%BE%E4%BE%8B)
    - [跨文件引用](#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8)
      - [跨文件引用语法](#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E6%B3%95)
      - [跨文件引用语义：合并](#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E4%B9%89%E5%90%88%E5%B9%B6)
      - [Include semantics: substitution](#include-semantics-substitution)
      - [Include semantics: missing files and required files](#include-semantics-missing-files-and-required-files)
      - [Include semantics: file formats and extensions](#include-semantics-file-formats-and-extensions)
      - [Include semantics: locating resources](#include-semantics-locating-resources)
    - [Conversion of numerically-indexed objects to arrays](#conversion-of-numerically-indexed-objects-to-arrays)
  - [MIME类型](#mime%E7%B1%BB%E5%9E%8B)
  - [对于API的建议](#%E5%AF%B9%E4%BA%8Eapi%E7%9A%84%E5%BB%BA%E8%AE%AE)
    - [Automatic type conversions](#automatic-type-conversions)
    - [Units format](#units-format)
    - [Duration format](#duration-format)
    - [Period Format](#period-format)
    - [Size in bytes format](#size-in-bytes-format)
    - [Config object merging and file merging](#config-object-merging-and-file-merging)
    - [Java properties mapping](#java-properties-mapping)
    - [Conventional configuration files for JVM apps](#conventional-configuration-files-for-jvm-apps)
    - [Conventional override by system properties](#conventional-override-by-system-properties)
    - [Substitution fallback to environment variables](#substitution-fallback-to-environment-variables)
    - [hyphen-separated vs. camelCase](#hyphen-separated-vs-camelcase)
  - [Note on Java properties similarity](#note-on-java-properties-similarity)
  - [Note on Windows and case sensitivity of environment variables](#note-on-windows-and-case-sensitivity-of-environment-variables)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# HOCON（人性化配置对象表示法，Human-Optimized Config Object Notation）

这并非正式文档，不过我觉得我讲得比较清楚了。

## 目标/背景

HOCON的主要目标是：保证JSON的语义（如树形结构；类型集合；编码/转义等）的同时，作为一个供人类编辑的配置文件，使其编辑起来更方便。

我们为方便编辑添加了以下新特性：

 - 减少格式符等不必要的噪音
 - 允许配置文件中的一处引用另一处（设置一个值为另一个值）
 - 允许在当前配置文件中导入或包含其他配置文件
 - 提供到Java等处使用的扁平化properties列表格式的映射
 - 允许从环境变量中取值
 - 允许写注释

实现上，这一格式需要满足以下特征：

 - JSON格式的超集，也就是说所有有效的JSON格式都应该是合法的，同时在内存中的解析结果应与JSON解析器的输出一致。
 - 结果唯一；换言之，即使HOCON格式本身非常灵活，但它也不应模棱两可。HOCON应该划定哪些形式是不合法的，不合法的形式在解析时应该报错。
 - 解析时探测的字符应该尽可能少；换言之，对HOCON格式配置的Tokenize操作不应依赖超过三个字符的探测。（目前探测三个字符的唯一原因只是探测“//”开头的注释；不然的话只需探测两个字符就够了。）

HOCON比JSON难描述也难解析得多。想象一下一些维护配置文件的工作，本来是人类负责，结果被转移到机器负责，会发生什么。

## 定义

 - 我们使用 _键（key）_ 代指JSON中`:`左侧的字符串部分，而 _值（value）_ 代指JSON中`:`右侧的部分。比如：对象的一个 _键值对（field）_ 的两部分。
 - 我们使用 _值（value）_ 代指JSON规范中被定义为“value”的东西，以及本规范中定义的未加引号的字符串和引用等。
 - 我们使用 _简单值（simple value）_ 代指对象和数组以外的所有值。
 - 我们使用 _键值对（field）_ 代指一个键、一个诸如“:”等形式的分隔符、和一个值的排列。
 - 当我们使用 _文件（file）_ （正在被解析的文件）这一代称时，可能正在被解析的是一串字节流，不一定总是文件系统中的字面意思上的文件。

## 语法

这部分的大量内容都一定程度上借用了JSON的相关概念；当然你可以在<https://json.org/json-zh.html>找到JSON的语法规范。

### 和JSON一样的地方

 - 文件必须是合法的UTF-8格式
 - 加引号的字符串格式和JSON中的字符串相同
 - 值类型可以是：字符串、数值、对象、数组、布尔值、以及空（null）
 - 允许的数字格式和JSON相同；在JSON中一些可能的浮点数值，如`NaN`等，是不允许出现的

### 注释

所有以`//`或`#`开头，并以一个新的换行符结尾的部分将被视作注释处理，除非`//`或`#`出现在了加引号的字符串中。

### 对根结构更宽松的要求

JSON格式要求根结构必须为数组或者对象。空文件不合法，只含有字符串等既不是数组也不是对象的元素的文件，也不合法。

HOCON文件如果不以方括号或花括号开头，那么它将以被`{}`包围的方式解析。

一个省略了开头`{`却没有省略结尾`}`的HOCON文件不合法；HOCON格式要求括号必须匹配。

### 键值分隔符

字符`=`可以被用在所有JSON要求使用`:`的场合，例如：用于分隔键值。

如果一个键随后的字符为`{`，那么中间的`=`可以省略。也就是说，`"foo" {}`和`"foo" : {}`是一样的。

### 逗号

对于数组里的值，以及对象里的键值对，只要它们之间有至少一个ASCII回车（`\n`，ASCII码为10）分隔，那么逗号就是可有可无的。

最后一个数组里的元素后，或者最后一个对象里的键值对后，可以跟一个逗号。多出来的逗号将被忽略。

 - `[1,2,3,]`和`[1,2,3]`代表同一个数组。
 - `[1\n2\n3]`和`[1,2,3]`代表同一个数组。
 - `[1,2,3,,]`不合法，因为它在最后有两个逗号。
 - `[,1,2,3]`不合法，因为它在开头有一个逗号。
 - `[1,,2,3]`不合法，因为两个元素中间有两个逗号。
 - 上面针对逗号的规则同样适用于对象。

### 空白

JSON 语法规范只简单提到了“空白”（"whitespace"）一词；在 HOCON 中，“空白”定义如下：

 - 任何 Unicode 中的空格符（Zs 分类下字符）、换行符（Zl 分类）、或分段符
   （Zp 分类），包含不换行空格（例如 0x00A0、0x2007 和 0x202F）。
   字节顺序记号（BOM，0xFEFF）也必须视作空白。
 - 制表符（`\t`，0x0009）、换行符（`\n`，0x000A）、垂直定位（`\v`，
   0x000B）、换页符（`\f`，0x000C）、回车符（`\r`，0x000D)、
   文件分隔符（0x001C）、分组符（0x001D）、记录分隔符（0x001E）
   和单元分隔符（0x001F）。

在 Java 中，`isWhitespace()` 方法可以覆盖除了不换行空格和 BOM以外的上述所有字符。

尽管所有 Unicode 中定义的分隔符都应视作空格，本规范中所称“换行符”（"newline"）指且仅指 ASCII 换行符 0x000A。

### 重复键与对象合并

JSON 规范中并没有明确同一个对象下重复键的处理方式。在 HOCON 中，重复的键的处理方式是以后来者为准，即后出现的键的值覆盖先前出现的；但如果重复的键对应的值都是对象，那么两个对象会合并在一起。

注意：如果你假定 JSON 中重复的键有特定行为，HOCON 将不再是 JSON 的超集。本规范中假定 JSON 不允许重复的键。

合并对象的过程如下：

 - 将两个对象中其中一个下的所有键值对加入另一个中。
 - 对于两个对象中的同名非对象键值对，必须使用第二个对象中的键值对。
 - 对于两个对象中的同名对象键值对，须遵循一样的规则递归合并。

对象的合并可以通过预先给键赋另外一个值来避免。这是因为，合并总是围绕两个值进行的。如果你先给一个键赋值为对象，然后赋一个非对象的值，接着再赋值为另一个对象，那么首先第一个对象会被那个非对象的值覆盖（非对象总是会覆盖对象），然后第二个对象将原本的值覆盖掉（没有合并，直接赋值）。因此两个对象之间什么事也没有发生。

下面两段 HOCON 是等价的：

    {
        "foo" : { "a" : 42 },
        "foo" : { "b" : 43 }
    }

    {
        "foo" : { "a" : 42, "b" : 43 }
    }

下面两段 HOCON 也是等价的：

    {
        "foo" : { "a" : 42 },
        "foo" : null,
        "foo" : { "b" : 43 }
    }

    {
        "foo" : { "b" : 43 }
    }

注意中间为 `"foo"` 赋值为 `null` 的操作阻止了对象的合并。

### 不加引号的字符串

不被引号括起来的字符串序列（Unquoted string），在符合下列条件时，会被认为是字符串值：

 - 不包含下列“非法字符”：'$'、'"'、'{'、'}'、'['、']'、':'、'='、','、'+'、'#'、'\`'、'^'、'?'、'!'、'@'、'\*'、'&'、'\\'（反斜杠）、或者空白。
 - 不包含由两个正斜杠组成的字符串"//"（它代表注释的开始）。
 - 其开头没有被解析为`true`、`false`、`null`或数字。

不加引号的字符串将按其字面值解析，也就是说不支持转义。如果你想要使用特殊字符，而这种特殊字符不允许在不加引号的字符串中出现的话，那你或许总是要加上引号的。

`truefoo`将被解析面一个布尔值`true`跟随着一个字符串`foo`。不过，`footrue`将被解析成不加引号的`footrue`。类似的情况还有，`10.0bar`将被解析成数值`10.0`和不加引号的`bar`的组合，而`bar10.0`将被解析成不加引号的`bar10.0`。（实际情况是，由于值连结的存在，这种区别无关紧要；请看后续章节。）

通常情况下，不加引号的字符串将在出现"//"这种两字符字符串，或者不允许在不加引号的字符串中出现的字符串结束。在其中（非开头）出现的布尔值，空值（null），以及数值等将不会被特殊对待，而是被看作字符串的一部分。

不加引号的字符串不能以数字0-9或连字符（`-`，0x002D） _开头_ ，因为它们作为JSON数值开头是合法的。开始的数字字符以及随后的所有在JSON中作为数值合法的字符，都一定会被解析成数值。再强调一次，这种字符在不加引号的字符串 _中间_ 是不被特别对待的；只有在开头出现的情况才会被按照数字解析。

JSON中被引号括起来的字符串不允许包含控制字符（一些控制字符同时作为空白字符使用，如换行符等）。JSON规范规定了这一行为。不过，对于不加引号的字符串，没有针对控制字符的限制，除非控制字符同时是上面提到的不允许出现的字符。

上面提到的字符不允许出现，一部分是由于它们在JSON或HOCON中已经有其含义，另一部分作为保留字使用，以方便未来扩展这一规范。

### 多行字符串

和Python以及Scala等语言类似，多行字符串使用三个引号。如果在解析时解析到了`"""`三个字符的序列，那么在下一个用作闭合字符序列的`"""`出现之前，其中所有Unicode字符都将被不加修改地用作字符串值的组成部分。不管是空格还是换行符，都不作特殊处理。和Scala的处理方式，以及JSON对待被引号括起来的字符串的处理方式不同，转义符在被三个引号括起来的字符串中不作处理。

在Python中，诸如`"""foo""""`的形式会导致语法错误（三个引号的字符串序列后紧跟着一个悬空引号）。在Scala中，这种形式将被看作由四个字符组成的字符串`foo"`。HOCON的解析方式和Scala类似；序列中的最后三个引号被看作多行字符串的闭合字符序列，而所有“多出来的”引号将被看作多行字符串的一部分。

### 值连结

对象中键值对的值或者数组元素可能表现为多个合在一起的值的组合。有三种值连结的方式：

 - 所有简单值（不含对象或数组）的组合为字符串（字符串值连结）。
 - 所有数组的组合为合并后的单个数组（数组值连结）。
 - 所有对象的组合为合并（考虑相同键）后的单个对象（对象值连结）。

除键值对的值和数组元素外，键值对的键也支持字符串值连结。对于键值对的键来说，对象或数组的组合没有意义。

注意：Akka 2.0（因此也包括Play 2.0）针对配置文件的内置实现不支持针对数组或对象的值连结；其支持的只有字符串值连结。

#### 字符串值连结

字符串值连结保证了未加引号的字符串正常工作；字符串值连结同时提供了对引用（诸如`${foo}`的形式）的支持。

字符串值连结只允许简单值的组合。再次强调简单值的定义为除数组和对象外的其他类型值。

只要简单值仅由换行符之外的空白分隔， _它们之间的空白就会被保留_ ，使值与空白连结组成一个字符串。

字符串值连结将不会跨过换行符，或者任何不属于简单值的字符。

所有字符串可能出现的地方都可能出现字符串值连结，比如说对象的键和值以及数组元素。

无论何时，如果一个值本当出现在JSON中，那么一个HOCON解析器会在对应位置尝试收集多个值（包括它们之间的空白），并将这些值连接成一个字符串。

在第一个值前或最后一个值后的空白将会被忽略。只有值 _之间_ 的空白会被保留。

所以比如说` foo bar baz `会被解析成三个未加引号的字符串，然后这三个字符串会被连结成一个字符串。中间的空白将会被保留，但是两边的空白会被去除。因为等价的，被引号括起来的字符串形式为`"foo bar baz"`。

值连结后的`foo bar`（两个未加引号的字符串以及中间的空白）和被引号引用的`"foo bar"`在解析后内存里的形式是一样，都是七个字符的字符串。

为保证字符串值连结，非字符串类型的值将会以以下规则转换成字符串（以下转换结果使用被引号引用的形式）：

 - `true`和`false`分别转换为`"true"`和`"false"`。
 - `null`转换为`"null"`。
 - 加或不加引号的字符串转换到其本身。
 - 数值应转换为其在文件中原有的形式。比如说如果一个解析器尝试解析`1e5`，那么解析形式可能还会有包含有字母`E`的`1E5`或者`100000`。为了保证字符串值连结，解析时应保持其在文件中原有的形式。
 - 引用将会被替换成其对应值，然后再按照上面的规则转换成字符串。
 - 字符串值连结中出现数组或对象是不合法的。

单个值不应转换成字符串。换言之，如果你试图使用值连结的方式对待`true`本身，那么解析结果就会出错；因为解析时应该当作布尔值对待。只有诸如`true foo`（`true`后面同一行跟着另一个简单值）的形式才能以值连结的方式解析并转换成字符串。

#### 数组值连结和对象值连结

数组可以和数组之间值连结，对象也可以和对象之间值连结，但如果混着来就会出错。

为保证值连结，“数组”同时也包括“值为数组的引用”，同时“对象”同时也包括“值为对象的引用。”

在键值对的值或数组元素中，如果第一个数组或对象或引用的末尾，以及第二个数组或对象或引用的开头，只有换行符之外的空白分隔，那么两个值将会进行值连结。

对于对象来说，“连结”意味着“合并”，因此后一个值将会覆盖前一个。

不管是否存在值连结，数组和对象都不能成为键值对的键。

下面的几种方式定义的对象`a`是完全等价的：

    // one object
    a : { b : 1, c : 2 }
    // two objects that are merged via concatenation rules
    a : { b : 1 } { c : 2 }
    // two fields that are merged
    a : { b : 1 }
    a : { c : 2 }

下面的几种方式定义的数组`a`是完全等价的：

    // one array
    a : [ 1, 2, 3, 4 ]
    // two arrays that are concatenated
    a : [ 1, 2 ] [ 3, 4 ]
    // a later definition referring to an earlier
    // (see "self-referential substitutions" below)
    a : [ 1, 2 ]
    a : ${a} [ 3, 4 ]

一种常见的对象值连结用法和“继承”类似：

    data-center-generic = { cluster-size = 6 }
    data-center-east = ${data-center-generic} { name = "east" }

一种常见的数组值连结用法被用于文件路径集合：

    path = [ /bin ]
    path = ${path} [ /usr/bin ]

#### 注意：引用之间含有空白的值连结

如果你试图使用`${foo} ${bar}`等形式连结两个引用，那么被连结的引用可能会转换成字符串（这使得其之间的空白十分重要），可能会转换成对象或者列表（在这里其之间的空白无关紧要）。对于其值为对象或者列表的引用，其之间的空白应该被忽略。如果空白被引号括了起来，将产生语法错误。

#### 注意：不含有逗号或换行符的数组

在数组中，你可以使用换行符代替逗号，不过你不能使用空格代替逗号。因此换行符之外的空白将导致数组元素值连结而不是数组元素值分隔。

    // this is an array with one element, the string "1 2 3 4"
    [ 1 2 3 4 ]
    // this is an array of four integers
    [ 1
      2
      3
      4 ]

    // an array of one element, the array [ 1, 2, 3, 4 ]
    [ [ 1, 2 ] [ 3, 4 ] ]
    // an array of two arrays
    [ [ 1, 2 ]
      [ 3, 4 ] ]

如果你对此感到迷惑，你应该用一用逗号。在下面的情况下，值连结行为是足够有用的，而不是令人惊讶的：

    [ This is an unquoted string my name is ${name}, Hello ${world} ]
    [ ${a} ${b}, ${x} ${y} ]

换行符之外的空白不会被用作元素和键值对的分隔符。

### 路径表达式

路径表达式（Path expression）被用于表示对象树中的一个路径。一些诸如`${foo.bar}`等使用引用的场合，以及诸如`{ foo.bar : 42 }`等使用键值对的键的场合会用到路径表达式。

路径表达式在语法上与值连结相同，但不会包含引用。这意味着你不能在引用中使用引用，以及你也不能在键值对的键中使用引用。

在路径表达式中，被引号括起来的字符串外的`.`被当作分隔路径的分隔符处理，而被引号括起来的字符串内的`.`不作特殊处理。因此`foo.bar."hello.world"`代表一个有三个组成部分的路径表达式，前两个分别是`foo`和`bar`，最后一个是`hello.world`。

需要注意的一点是，数字之间的`.`将被当作分隔符处理。因此如果将数字作为路径表达式的一部分进行处理，那么必须将其以文件中出现的 _原始_ 字符串表示形式处理（而不是使用一些通用的函数将其从数字转换回字符串）。

 - `10.0foo`表现为一个数字和一个不加引号的`foo`的连结因此应以`10`和`0foo`两个元素的方式解析。
 - `foo10.0`表现为一个包含有`.`的不加引号的字符串因此应以`foo10`和`0`两个元素的方式解析。
 - `foo"10.0"`表现为一个不加引号的和一个加引号的字符串的连结因此应以单个元素的方式解析。
 - `1.2.3`应以表现为`1`、`2`、和`3`三个元素的组合方式解析。

和值连结不同，路径表达式应 _总是_ 被转换成字符串，即使其只代表一个值。

如果在解析时遇到一个数组，其中一个元素的值为单个`true`，那么解析时应当作值连结的方式处理，也就是应以布尔值的方式处理。

如果在解析（键值对的键或者引用）时遇到一个路径表达式，那么其应总是当作字符串处理，因此`true`应被当作一个字符串，其被引号括起来的形式是`"true"`。

如果路径表达式是空字符串，那么它应永远被引号括起来。换言之，`a."".b`代表一个有着三个元素的路径表达式。不过，`a..b`是不合法的，并应在解析时报错。按照这样的规则，所有在开头或者结尾时出现`.`的路径表达式，都应被当作不合法的情况在解析时报错处理。

### 作为键的路径表达式

如果一个键同时也是一个包含有多个元素的路径表达式，那么在解析时除最后一个元素外的所有元素都将被展开成对象。路径的最后一个元素与值结合，从而最后形成嵌套对象中的一个键值对。

换言之：

    foo.bar : 42

和：

    foo { bar : 42 }

是等价的。以及：

    foo.bar.baz : 42

和：

    foo { bar { baz : 42 } }

也是等价的。对象的值会进行合并；也就是说：

    a.x : 42, a.y : 43

和：

    a { x : 42, y : 43 }

是等价的。因为路径表达式和值连结类似，所以说你可以在键值对的键中使用空格，比如说：

    a b c : 42

和：

    "a b c" : 42

是等价的。此外，因为路径表达式总是被转换成字符串，因此即使是拥有其他类型含义的单个值，也会被转换成字符串类型。

   - `true : 42`和`"true" : 42`等价
   - `3 : 42`和`"3" : 42`等价
   - `3.14 : 42`和`"3" : { "14" : 42 }`等价

有一条特殊的规则，就是不加引号的`include`如果被用于键值对的键，那么它不能作为路径表达式的开头，因为其有特殊含义（见后续章节）。

### 引用

引用（Substitution）配置文件树中的其他部分是HOCON允许的一种形式。

引用的语法是这样的：`${pathexpression}` 或 `${?pathexpression}`。其中，`pathexpression` 便是上文中提及的路径表达式。这里用到的路径表达式的语法与用作对象的键的语法是一样的。

`${?pathexpression}` 中的 `?` 前不能有空格。换言之，使用这种形式的引用时，`${?` 必须原样组合在一起使用。

某个实现可以通过查询系统环境变量或其他外部配置来解析在配置树中没有找到的引用。（关于环境变量的细节将在后文中阐述。）

引用不会尝试解析包含在其中的加引号的字符串。如果你需要在字符串中使用引用，你必须使用值连结把引用和不加引号的字符串连接起来：

    key : ${animal.favorite} is my favorite animal

你也可以用引号把非引用部分括起来：

    key : ${animal.favorite}" is my favorite animal"

引用通过查询整个配置来解析。路径从根对象开始解析，换言之路径是绝对路径，而非相对路径。

引用处理是解析的最后一步，所以引用也可以向后查询。如果一个配置包含了多个文件，最终引用还可以解析到别的文件上去。

如果一个键出现了多次，引用只会解析到最后一次出现的值（换言之，它会解析到所有包含的文件中该键的最终赋值，或最终合并出来的对象）。

如果有一个选项设定为 `null`，那么解析它的键时就永远不会从外部来源中解析。不幸的是，这个操作是不可逆的；如果你的根对象中有类似 `{ "Home" : null }` 的东西，那么解析 `${HOME}` 就永远不会解析到系统环境变量上去。换言之，HOCON 中没有等价于 JavaScript 的 `delete` 的操作。

若引用无法匹配到任何配置中出现的值，同时也不能通过外部来源解析成任何值，那么这个引用会成为未定义引用。以 `${foo}` 形式出现的未定义引用是非法的，应当按照错误处理。

若形如 `${?foo}` 的引用没有定义：

 - 如果这是某个对象里的键值对，此引用不应产生新的键值对。如果此键值对会覆盖之前设定的相同键值对，则保留之前的值。
 - 如果这是某个数组元素，那么此引用不应导致新元素加入数组中。
 - 如果这是值连结的一部分，同时被值连结的另一个值是字符串，那么这个未定义引用会变成空字符串；如果被值连结的另一个值是对象或数组，则相应地变为空对象或空数组。
 - 对于 `foo : ${?bar}` 来说，在 `bar` 未定义时，`foo` 这个键不会存在。对于 `foo : ${?bar}${?baz}` 来说，如果 `bar` 和 `baz` _都_ 没有定义，那么 `foo` 这个键不会存在。

引用只能用于键值对的值或数组元素（值连结）中，不能用于键名，亦不能嵌入路径表达式等其他引用中。

引用会被任意一种值类型（数字、对象、字符串、数组、`true`、`false`、`null`）替换。如果最终值只由引用组成，值类型会保留；否则，会通过值连结组成字符串。

#### 自引用

总的来说：

 - 通常情况下，引用将“向前看”，并将其最终值用于其路径表达式
 - 如果会产生循环，如果可能，循环应通过向后看打破（从而移除了引用循环中的一条引用链）

通过这种方式我们得以允许基于键值对的旧值设置新值：

    path : "a:b:c"
    path : ${path}":d"

_自引用键值对_ 指：

 - 其值或其值连结的一部分包含一个到自身值的引用
 - 键值对的值引用了一个已有定义的键值对，该键值对中直接或间接包含了一个最终引用回自身值的引用

自引用键值对的示例：

 - `a : ${a}`
 - `a : ${a}bc`
 - `path : ${path} [ /usr/bin ]`

需注意的一点是，如果一个数组或对象中的值含有一个指向自身值的引用，在解析时将 _不_ 考虑自引用键值对的相关规则。也就是说，以下情况相关规则 _不_ 作考虑：

 - `a : { b : ${a} }`
 - `a : [${a}]`

这种形式的循环应该直接在解析时报错。（假设允许“向前看”的话，一些诸如`a={ x : 42, y : ${a.x} }`的形式会在解析`${a.x}`时试图解析不存在的`a`。）

可能的实现有：

 - 尝试解析引用的行为会试图检索整个文件中对应的路径，如果检索时发现路径对应节点是引用的父节点，那么解析时便会感知到循环。
 - 尝试解析可能会出现自引用的引用（其值或其值连结的一部分包含一个引用）时，将该键值对以及会对其产生覆盖的所有键值对移除。

最简单的实现形式会在解析时将循环当作不存在的引用处理；比如说在解析`a : ${a}`时，你会首先把`a : ${a}`本身移除然后再解析`${a}`，也就是在一个空文件中检索对应的`${a}`的值。更复杂一点的做法是在被移除的键值对处添加一个标记符，从而在发现循环时产生可读性更高的错误信息。然后，在回到标记符对应的引用本身时报错。

对于可选引用（诸如`${?foo}`的形式）来说，对待循环的解析方式应同样按照不存在的值处理。如果`${?foo}`引用了自身，那么解析时就应该当作不存在的值处理。

#### 键值分隔符 `+=`

除了 `:` 和 `=`，键与值之间还可以用 `+=` 分割。使用 `+=` 分隔的键值对会令值变为自引用数组，例如：

    a += b

会变成：

    a = ${?a} [b]

`+=` 起到了在数组结尾追加元素的作用。如果 `a` 之前的值不是数组，它会产生和 `a = ${?a} [b]` 一样的报错。注意，`a` 的值不一定必须存在（`${?a}` 而非 `${a}`），换言之 `a += b` 这样的声明可以是全文件中第一次出现 `a` 的地方（即不需要 `a = []` 这样的显式声明）。

注意：Akka 2.0（因此也包括 Play 2.0）针对配置文件的内置实现不支持`+=`。

#### 自引用举例

在没有合并的情况下，自引用的键值对是非法的，因为其具体值无法解析：

    foo : ${foo} // an error

然而，当 `foo : ${foo}` 和 `foo` 之前的值合并时，这个引用就能解析到之前的值上。合并对象时，覆盖键值对中的引用指向被覆盖的键值对。例如：

    foo : { a : 1 }

在它之后又有：

    foo : ${foo}

此时 `${foo}` 会解析为 `{ a : 1 }`，即被覆盖的键值对的值。

如果两者顺序颠倒一下，就会产生错误。比如：

    foo : ${foo}

在它之后又有：

    foo : { a : 1 }

在这里 `${foo}` 自引用出现在了 `foo` 被赋值之前，所以此时的 `foo` 是没有定义的，无异于引用一个整个文件中没有定义的路径。

概念上来说，`foo : ${foo}` 是需要查找 `foo` 之前的定义以决定具体的解析结果的，所以它的报错应当是“没有定义”（"undefined"）而非“不可跳出的循环引用“（"intractable cycle"）。也因此，使用可选引用（Optional Substitution）即可避免循环引用的问题：

    foo : ${?foo} // 这个键会静静地消失

如果引用被无法合并的值（非对象的值）隐藏起来了，那么它就不会被解析，也因此不会报错。例如：

    foo : ${does-not-exist}
    foo : 42

在这个情况下，不管 `${does-not-exist}` 解析结果如何，我们都能确定 `foo` 是 `42`，所以 `${does-not-exist}` 不会被解析，也因此不会产生任何错误。对于形如 `foo : ${foo}, foo : 42` 这样的循环引用也是如此——第一个循环引用会被直接忽略。

即便是出现在路径表达式中的自引用，它也会解析到“下一层”的值上去。举例说明：

    foo : { a : { c : 1 } }
    foo : ${foo.a}
    foo : { a : 2 }

在这里，`${foo.a}` 会指向 `{ c : 1 }` 这个对象，而非 `2` 这个数字，所以最终 `foo` 的值会是合并之后的 `{ a : 2, c : 1 }`。

回想一下，自引用键值对必须使用引用或值连结来确定最终值。举个例子，如果键值对的值是对象或数组，那么即使在这个对象或数组中有对这个键值对的引用，它也不会算作自引用。

HOCON 的实现必须小心对待在对象中引用自己的路径的情况，举例：

    bar : { foo : 42,
            baz : ${bar.foo}
          }

在种情况下，如果某个实现选项将解析整个 `bar` 对象的过程作为解析引用 `${bar.foo}` 过程的一部分，那么就会产生循环引用。这种情况下，HOCON 的实现应当只尝试解析 `bar` 对象 `foo` 中的 `foo`，而非整个 `bar` 对象。

因为没有循环继承，引用有必要“向前解析”（包括查找正在定义中的键值对）以确定解析结果。举例说明：下面的 HOCON 中，`bar.baz` 最终会解析成 `43`。

    bar : { foo : 42,
            baz : ${bar.foo}
          }
    bar : { foo : 43 }

相互引用的对象也是成立的，同时也不会认为是自引用（因为也会“向前解析”）：

    // bar.a should end up as 4
    bar : { a : ${foo.d}, b : 1 }
    bar.b = 3
    // foo.c should end up as 3
    foo : { c : ${bar.b}, d : 2 }
    foo.d = 4

另一种极端情况是值连结中的可选自引用，下面的 HOCON 中 `a` 首先会被解析为 `foo` 而非 `foofoo`，因为自引用会“向后解析”并成功解析没有定义的 `a`：

    a = ${?a}foo

总体上来说，解析引用的实现应当：

 - 对引用目标惰性求值，避免“循环引用引发的副作用”
 - “向前解析”，并以路径解析出的最终值作为引用的值
 - 出现循环时，应“向后解析”，通过合并等方式解决循环
 - 若惰性求值和“向后解析”均无法跳出循环，引用应视为未定义并产生错误，除非使用可选引用 `${?foo}` 的语法。

举例，下列 HOCON 无法解析：

    bar : ${foo}
    foo : ${bar}

像是这样由多个键值对组成的循环也应能识别为非法 HOCON：

    a : ${b}
    b : ${c}
    c : ${a}

在某些情况下，解析结果依赖于解析顺序，但具体解析顺序没有定义时，就会产生未定义行为。例如：

    a : 1
    b : 2
    a : ${b}
    b : ${a}

HOCON 的实现可以在“`a` 和 `b` 都解析为 1”、“都解析为 2”或者产生错误三种行为之间选择。理论上，这种情况应当产生错误，但这种行为可能会很难实现。令这种行为有确定结果一定需要有序表而非无序表的支撑，这也会制造一些限制。理论上，HOCON 的实现只需要追踪相同键值对的重复实例（即合并）。

然而，HOCON 的实现必须选择将 `a` 和 `b` 解析为相同的值。在实践中，这意味着所有的引用都必须存储起来（只解析一次，保存解析结果）。存储解析的方式应当以引用它本身为键，而非 `${}` 表达式中的路径，因为根据其所在文件中的位置不同，稍后的解析结果可能会有所差异。

### 跨文件引用

#### 跨文件引用语法

_跨文件引用声明_ 由未加括号的`include`和随后的空白符及之后的：
 - 单个被引号 _括起来的_ 字符串。这种声明会被启发式地解释为URL，文件名或classpath中的相关资源。
 - 被`url()`、`file()`、或者`classpath()`括起来的加了引号的字符串。这种声明会被分别解析为URL，文件名或classpath。和CSS等情况不同的是，其中的字符串必须使用引号括起来。
 - 被`required()`括起来的上述情况之一。

跨文件引用声明应用于原为键值对的地方。

如果`include`出现在一个路径表达式的开头，而该路径表达式本身作为对象的键存在，那么它将不会被以路径表达式或者键的方式解析。

作为替代键值对的声明，`include`后必须跟随一个被引号 _括起来的_ 字符串，或者一个被引号括起来，又被`url()`、`file()`、或者`classpath()`括起来的字符串。该字符串值被称为 _资源名称_ 。

总的来说，`include`以及其后的资源名称被用于原为键值对的地方，因此语法上，跨文件引用声明应通过逗号（如果有换行符的话逗号可以省略）和其他键值对分隔。

如果`include`出现在对象的键的位置，而随后没有出现被引号括起来的字符串或者`url("")`/`file("")`/`classpath("")`等形式，那么这种声明是不合法的，从而在解析时应该报错。

在`include`和资源名称之间可以有任意多的空白，包括换行符。对于`url()`等声明形式，`()`内（以及引号外）同样允许出现空白。

在`include`后或`url()`等形式中，不允许使用值连结。其值只能使用被引号括起来的字符串形式。引用形式也不被允许，换言之，除被引号括起来的字符串，其他情形都不被允许。

在对象的键的开始位置之外的`include`没有特殊意义。

`include`可以出现在对象的键的声明中：

    # this is valid
    { foo include : 42 }
    # equivalent to
    { "foo include" : 42 }

或者作为对象或者数组的值：

    { foo : include } # value is the string "include"
    [ include ]       # array of one string "include"

如果你想使用以`"include"`开头的字符串作为对象的键，你可以将其括起来，也就是`"include"`的形式，只有不加引号的`include`是特殊的：

    { "include" : 42 }

注意：Akka 2.0（因此也包括Play 2.0）针对配置文件的内置实现不支持`url()`/`file()`/`classpath()`形式的跨文件引用。相应的实现只支持启发式的`include "foo"`等形式。

#### 跨文件引用语义：合并

我们定义 _文件引用者（including file）_ 为跨文件引用声明的文件，同时定义 _被引用文件（included file）_ 为跨文件引用声明中的值对应的文件。（文件引用者和被引用文件不一定总是文件系统中的文件，不过这里我们先假设它们都是。）

被引用文件必须包含一个对象，而不是数组。这很重要，因为不管是JSON还是HOCON都允许数组或者对象作为文件的根节点。

如果被引用文件包含了一个数组，那么跨文件引用声明就是不合法的，也就是说解析时会报错。

被引用文件会被解析成一个根对象。根对象的键在概念上代替了文件引用者中的跨文件引用声明。

 - 在跨文件引用声明前出现的键值对将被覆盖或者合并，其行为和一个文件中同时出现两个相同键值对的行为等同。
 - 在跨文件引用声明后重复出现的键值对，将会覆盖或者合并被引用文件中的键值对。

#### Include semantics: substitution

Substitutions in included files are looked up at two different
paths; first, relative to the root of the included file; second,
relative to the root of the including configuration.

Recall that substitution happens as a final step, _after_
parsing. It should be done for the entire app's configuration, not
for single files in isolation.

Therefore, if an included file contains substitutions, they must
be "fixed up" to be relative to the app's configuration root.

Say for example that the root configuration is this:

    { a : { include "foo.conf" } }

And "foo.conf" might look like this:

    { x : 10, y : ${x} }

If you parsed "foo.conf" in isolation, then `${x}` would evaluate
to 10, the value at the path `x`. If you include "foo.conf" in an
object at key `a`, however, then it must be fixed up to be
`${a.x}` rather than `${x}`.

Say that the root configuration redefines `a.x`, like this:

    {
        a : { include "foo.conf" }
        a : { x : 42 }
    }

Then the `${x}` in "foo.conf", which has been fixed up to
`${a.x}`, would evaluate to `42` rather than to `10`.
Substitution happens _after_ parsing the whole configuration.

However, there are plenty of cases where the included file might
intend to refer to the application's root config. For example, to
get a value from a system property or from the reference
configuration. So it's not enough to only look up the "fixed up"
path, it's necessary to look up the original path as well.

#### Include semantics: missing files and required files

By default, if an included file does not exist then the include statement should
be silently ignored (as if the included file contained only an
empty object).

If however an included resource is mandatory then the name of the
included resource may be wrapped with `required()`, in which case
file parsing will fail with an error if the resource cannot be resolved.

The syntax for this is

    include required("foo.conf")
    include required(file("foo.conf"))
    include required(classpath("foo.conf"))
    include required(url("http://localhost/foo.conf"))


Other IO errors probably should not be ignored but implementations
will have to make a judgment which IO errors reflect an ignorable
missing file, and which reflect a problem to bring to the user's
attention.

#### Include semantics: file formats and extensions

Implementations may support including files in other formats.
Those formats must be compatible with the JSON type system, or
have some documented mapping to JSON's type system.

If an implementation supports multiple formats, then the extension
may be omitted from the name of included files:

    include "foo"

If a filename has no extension, the implementation should treat it
as a basename and try loading the file with all known extensions.

If the file exists with multiple extensions, they should _all_ be
loaded and merged together.

Files in HOCON format should be parsed last. Files in JSON format
should be parsed next-to-last.

In short, `include "foo"` might be equivalent to:

    include "foo.properties"
    include "foo.json"
    include "foo.conf"

This same extension-based behavior is applied to classpath
resources and files.

For URLs, a basename without extension is not allowed; only the
exact URL specified is used. The format will be chosen based on
the Content-Type if available, or by the extension of the path
component of the URL if no Content-Type is set. This is true even
for file: URLs.

#### Include semantics: locating resources

A quoted string not surrounded by `url()`, `file()`, `classpath()`
must be interpreted heuristically. The heuristic is to treat the
quoted string as:

 - a URL, if the quoted string is a valid URL with a known
   protocol.
 - otherwise, a file or other resource "adjacent to" the one being
   parsed and of the same type as the one being parsed. The meaning
   of "adjacent to", and the string itself, has to be specified
   separately for each kind of resource.
 - On the Java Virtual Machine, if an include statement does not
   identify a valid URL or an existing resource "adjacent to" the
   including resource, implementations may wish to fall back to a
   classpath resource.  This allows configurations found in files
   or URLs to access classpath resources in a natural way.

Implementations may vary in the kinds of resources they can
include.

For resources located on the Java classpath:

 - included resources are looked up by calling `getResource()` on
   the same class loader used to look up the including resource.
 - if the included resource name is absolute (starts with '/')
   then it should be passed to `getResource()` with the '/'
   removed.
 - if the included resource name does not start with '/' then it
   should have the "directory" of the including resource
   prepended to it, before passing it to `getResource()`.  If the
   including resource is not absolute (no '/') and has no "parent
   directory" (is just a single path element), then the included
   relative resource name should be left as-is.
 - it would be wrong to use `getResource()` to get a URL and then
   locate the included name relative to that URL, because a class
   loader is not required to have a one-to-one mapping between
   paths in its URLs and the paths it handles in `getResource()`.
   In other words, the "adjacent to" computation should be done
   on the resource name not on the resource's URL.

For plain files on the filesystem:

 - if the included file is an absolute path then it should be kept
   absolute and loaded as such.
 - if the included file is a relative path, then it should be
   located relative to the directory containing the including
   file.  The current working directory of the process parsing a
   file must NOT be used when interpreting included paths.
 - if the file is not found, fall back to the classpath resource.
   The classpath resource should not have any package name added
   in front, it should be relative to the "root"; which means any
   leading "/" should just be removed (absolute is the same as
   relative since it's root-relative). The "/" is handled for
   consistency with including resources from inside other
   classpath resources, where the resource name may not be
   root-relative and "/" allows specifying relative to root.

URLs:

 - for files loaded from a URL, "adjacent to" should be based
   on parsing the URL's path component, replacing the last
   path element with the included name.
 - file: URLs should behave in exactly the same way as a plain
   filename

Implementations need not support files, Java resources, or URLs;
and they need not support particular URL protocols. However, if
they do support them they should do so as described above.

Note that at present, if `url()`/`file()`/`classpath()` are
specified, the included items are NOT interpreted relative to the
including items. Relative-to-including-file paths only work with
the heuristic `include "foo.conf"`. This may change in the future.

### Conversion of numerically-indexed objects to arrays

In some file formats and contexts, such as Java properties files,
there isn't a good way to define arrays. To provide some mechanism
for this, implementations should support converting objects with
numeric keys into arrays. For example, this object:

    { "0" : "a", "1" : "b" }

could be treated as:

    [ "a", "b" ]

This allows creating an array in a properties file like this:

    foo.0 = "a"
    foo.1 = "b"

The details:

 - the conversion should be done lazily when required to avoid
   a type error, NOT eagerly anytime an object has numeric
   keys.
 - the conversion should be done when you would do an automatic
   type conversion (see the section "Automatic type conversions"
   below).
 - the conversion should be done in a concatenation when a list
   is expected and an object with numeric keys is found.
 - the conversion should not occur if the object is empty or
   has no keys which parse as positive integers.
 - the conversion should ignore any keys which do not parse
   as positive integers.
 - the conversion should sort by the integer value of each
   key and then build the array; if the integer keys are "0" and
   "2" then the resulting array would have indices "0" and "1",
   i.e. missing indices in the object are eliminated.

## MIME类型

在诸如Content-Type这样的场合使用“application/hocon”。

## 对于API的建议

完美的HOCON格式实现应遵守下面这些约定，并以可预测的方式正常工作。

### Automatic type conversions

If an application asks for a value with a particular type, the
implementation should attempt to convert types as follows:

 - number to string: convert the number into a string
   representation that would be a valid number in JSON.
 - boolean to string: should become the string "true" or "false"
 - string to number: parse the number with the JSON rules
 - string to boolean: the strings "true", "yes", "on", "false",
   "no", "off" should be converted to boolean values. It's
   tempting to support a long list of other ways to write a
   boolean, but for interoperability and keeping it simple, it's
   recommended to stick to these six.
 - string to null: the string `"null"` should be converted to a
   null value if the application specifically asks for a null
   value, though there's probably no reason an app would do this.
 - numerically-indexed object to array: see the section
   "Conversion of numerically-indexed objects to arrays" above

The following type conversions should NOT be performed:

 - null to anything: If the application asks for a specific type
   and finds null instead, that should usually result in an error.
 - object to anything
 - array to anything
 - anything to object
 - anything to array, with the exception of numerically-indexed
   object to array

Converting objects and arrays to and from strings is tempting, but
in practical situations raises thorny issues of quoting and
double-escaping.

### Units format

Implementations may wish to support interpreting a value with some
family of units, such as time units or memory size units: `10ms`
or `512K`. HOCON does not have an extensible type system and there
is no way to add a "duration" type. However, for example, if an
application asks for milliseconds, the implementation can try to
interpret a value as a milliseconds value.

If an API supports this, for each family of units it should define
a default unit in the family. For example, the family of duration
units might default to milliseconds (see below for details on
durations). The implementation should then interpret values as
follows:

 - if the value is a number, it is taken to be a number in
   the default unit.
 - if the value is a string, it is taken to be this sequence:

     - optional whitespace
     - a number
     - optional whitespace
     - an optional unit name consisting only of letters (letters
       are the Unicode `L*` categories, Java `isLetter()`)
     - optional whitespace

   If a string value has no unit name, then it should be
   interpreted with the default unit, as if it were a number. If a
   string value has a unit name, that name of course specifies the
   value's interpretation.

### Duration format

Implementations may wish to support a `getMilliseconds()` (and
similar for other time units).

This can use the general "units format" described above; bare
numbers are taken to be in milliseconds already, while strings are
parsed as a number plus an optional unit string.

The supported unit strings for duration are case sensitive and
must be lowercase. Exactly these strings are supported:

 - `ns`, `nano`, `nanos`, `nanosecond`, `nanoseconds`
 - `us`, `micro`, `micros`, `microsecond`, `microseconds`
 - `ms`, `milli`, `millis`, `millisecond`, `milliseconds`
 - `s`, `second`, `seconds`
 - `m`, `minute`, `minutes`
 - `h`, `hour`, `hours`
 - `d`, `day`, `days`

### Period Format

Similar to the `getDuration()` method, there is a `getPeriod()` method
available for getting time units as a `java.time.Period`.

This can use the general "units format" described above; bare
numbers are taken to be in days, while strings are
parsed as a number plus an optional unit string.

The supported unit strings for period are case sensitive and
must be lowercase. Exactly these strings are supported:

 - `d`, `day`, `days`
 - `w`, `week`, `weeks`
 - `m`, `mo`, `month`, `months` (note that if you are using `getTemporal()`
 which may return either a `java.time.Duration` or a `java.time.Period`
 you will want to use `mo` rather than `m` to prevent your unit being
 parsed as minutes)
 - `y`, `year`, `years`

### Size in bytes format

Implementations may wish to support a `getBytes()` returning a
size in bytes.

This can use the general "units format" described above; bare
numbers are taken to be in bytes already, while strings are
parsed as a number plus an optional unit string.

The one-letter unit strings may be uppercase (note: duration units
are always lowercase, so this convention is specific to size
units).

There is an unfortunate nightmare with size-in-bytes units, that
they may be in powers or two or powers of ten. The approach
defined by standards bodies appears to differ from common usage,
such that following the standard leads to people being confused.
Worse, common usage varies based on whether people are talking
about RAM or disk sizes, and various existing operating systems
and apps do all kinds of different things.  See
https://en.wikipedia.org/wiki/Binary_prefix#Deviation_between_powers_of_1024_and_powers_of_1000
for examples. It appears impossible to sort this out without
causing confusion for someone sometime.

For single bytes, exactly these strings are supported:

 - `B`, `b`, `byte`, `bytes`

For powers of ten, exactly these strings are supported:

 - `kB`, `kilobyte`, `kilobytes`
 - `MB`, `megabyte`, `megabytes`
 - `GB`, `gigabyte`, `gigabytes`
 - `TB`, `terabyte`, `terabytes`
 - `PB`, `petabyte`, `petabytes`
 - `EB`, `exabyte`, `exabytes`
 - `ZB`, `zettabyte`, `zettabytes`
 - `YB`, `yottabyte`, `yottabytes`

For powers of two, exactly these strings are supported:

 - `K`, `k`, `Ki`, `KiB`, `kibibyte`, `kibibytes`
 - `M`, `m`, `Mi`, `MiB`, `mebibyte`, `mebibytes`
 - `G`, `g`, `Gi`, `GiB`, `gibibyte`, `gibibytes`
 - `T`, `t`, `Ti`, `TiB`, `tebibyte`, `tebibytes`
 - `P`, `p`, `Pi`, `PiB`, `pebibyte`, `pebibytes`
 - `E`, `e`, `Ei`, `EiB`, `exbibyte`, `exbibytes`
 - `Z`, `z`, `Zi`, `ZiB`, `zebibyte`, `zebibytes`
 - `Y`, `y`, `Yi`, `YiB`, `yobibyte`, `yobibytes`

It's very unclear which units the single-character abbreviations
("128K") should go with; some precedents such as `java -Xmx 2G`
and the GNU tools such as `ls` map these to powers of two, so this
spec copies that. You can certainly find examples of mapping these
to powers of ten, though. If you don't like ambiguity, don't use
the single-letter abbreviations.

Note: any value in zetta/zebi or yotta/yobi will overflow a 64-bit
integer, and of course large-enough values in any of the units may
overflow. Most real-world APIs and apps will not support byte
counts that overflow a 64-bit integer. The huge units are provided
just to be complete but probably aren't useful in practice. At
least not in 2014.

### Config object merging and file merging

It may be useful to offer a method to merge two objects. If such a
method is provided, it should work as if the two objects were
duplicate values for the same key in the same file. (See the
section earlier on duplicate key handling.)

As with duplicate keys, an intermediate non-object value "hides"
earlier object values. So say you merge three objects in this
order:

 - `{ a : { x : 1 } }`  (first priority)
 - `{ a : 42 }` (fallback)
 - `{ a : { y : 2 } }` (another fallback)

The result would be `{ a : { x : 1 } }`. The two objects are not
merged because they are not "adjacent"; the merging is done in
pairs, and when `42` is paired with `{ y : 2 }`, `42` simply wins
and loses all information about what it overrode.

But if you re-ordered like this:

 - `{ a : { x : 1 } }`  (first priority)
 - `{ a : { y : 2 } }` (fallback)
 - `{ a : 42 }` (another fallback)

Now the result would be `{ a : { x : 1, y : 2 } }` because the two
objects are adjacent.

This rule for merging objects loaded from different files is
_exactly_ the same behavior as for merging duplicate fields in the
same file. All merging works the same way.

Needless to say, normally it's well-defined whether a config
setting is supposed to be a number or an object. This kind of
weird pathology where the two are mixed should not be happening.

The one place where it matters, though, is that it allows you to
"clear" an object and start over by setting it to null and then
setting it back to a new object. So this behavior gives people a
way to get rid of default fallback values they don't want.

### Java properties mapping

It may be useful to merge Java properties data with data loaded
from JSON or HOCON. See the Java properties spec here:
https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.Reader-

Java properties parse as a one-level map from string keys to
string values.

To convert to HOCON, first split each key on the `.` character,
keeping any empty strings (including leading and trailing empty
strings). Note that this is _very different_ from parsing a path
expression.

The key split on `.` is a series of path elements. So the
properties key with just `.` is a path with two elements, both of
them an empty string. `a.` is a path with two elements, `a` and
empty string.  (Java's `String.split()` does NOT do what you want
for this.)

It is impossible to represent a key with a `.` in it in a
properties file.  If a JSON/HOCON key has a `.` in it, which is
possible if the key is quoted, then there is no way to refer to it
as a Java property. It is not recommended to name HOCON keys with
a `.` in them, since it would be confusing at best in any case.

Once you have a path for each value, construct a tree of
JSON-style objects with the string value of each property located
at that value's path.

Values from properties files are _always_ strings, even if they
could be parsed as some other type. Implementations should do type
conversion if an app asks for an integer, as described in an
earlier section.

When Java loads a properties file, unfortunately it does not
preserve the order of the file. As a result, there is an
intractable case where a single key needs to refer to both a
parent object and a string value. For example, say the Java
properties file has:

    a=hello
    a.b=world

In this case, `a` needs to be both an object and a string value.
The _object_ must always win in this case... the "object wins"
rule throws out at most one value (the string) while "string wins"
would throw out all values in the object. Unfortunately, when
properties files are mapped to the JSON structure, there is no way
to access these strings that conflict with objects.

The usual rule in HOCON would be that the later assignment in the
file wins, rather than "object wins"; but implementing that for
Java properties would require implementing a custom Java
properties parser, which is surely not worth it and wouldn't help
with system properties anyway.

### Conventional configuration files for JVM apps

By convention, JVM apps have two parts to their configuration:

 - the _reference_ config is made up of all resources named
   `reference.conf` on the classpath, merged in the order they
   are returned by `ClassLoader.getResources()`; also, system
   property overrides are applied.
 - the _application_ config can be loaded from anywhere an
   application likes, but by default if the application doesn't
   provide a config it would be loaded from files
   `application.{conf,json,properties}` on the classpath and
   then system property overrides are applied.
 - the reference config may be different for different class
   loaders, since each jar may provide a `reference.conf`
   to go with the code in that jar.
 - a single JVM may have multiple application configs if
   it has multiple modules or contexts of some kind.

The reference config for a given class loader should be merged and
resolved first, and may be shared among all application configs in
that class loader. Substitutions in the reference config are not
affected by any application configs, because the reference config
should be resolved by itself.

The application config should then be loaded, have the reference
config added as a fallback, and have substitutions resolved. This
means the application config can refer to the reference config in
its substitutions.

### Conventional override by system properties

For an application's config, Java system properties _override_
settings found in the configuration file. This supports specifying
config options on the command line.

### Substitution fallback to environment variables

Recall that if a substitution is not present (not even set to
`null`) within a configuration tree, implementations may search
for it from external sources. One such source could be environment
variables.

It's recommended that HOCON keys always use lowercase, because
environment variables generally are capitalized. This avoids
naming collisions between environment variables and configuration
properties. (While on Windows getenv() is generally not
case-sensitive, the lookup will be case sensitive all the way
until the env variable fallback lookup is reached).

See also the notes below on Windows and case sensitivity.

An application can explicitly block looking up a substitution in
the environment by setting a value in the configuration, with the
same name as the environment variable. You could set `HOME : null`
in your root object to avoid expanding `${HOME}` from the
environment, for example.

Environment variables are interpreted as follows:

 - env variables set to the empty string are kept as such (set to
   empty string, rather than undefined)
 - System.getenv throws SecurityException: treated as not present
 - encoding is handled by Java (System.getenv already returns
   a Unicode string)
 - environment variables always become a string value, though
   if an app asks for another type automatic type conversion
   would kick in

### hyphen-separated vs. camelCase

Config keys are encouraged to be `hyphen-separated` rather than
`camelCase`.

## Note on Java properties similarity

You can write a HOCON file that looks much like a Java properties
file, and many valid Java properties files will also parse as
HOCON.

However, HOCON is not a Java properties superset and the corner
cases work like JSON, not like properties.

Differences include but are probably not limited to:

 - certain characters that can be unquoted in properties files
   have to be placed in JSON-style double-quoted strings in HOCON
 - unquoted strings in HOCON do not support escape sequences
 - unquoted strings in HOCON do not preserve trailing whitespace
 - multi-line unquoted strings using backslash to continue the
   line are not allowed in HOCON
 - in properties files you can omit the value for a key and it's
   interpreted as an empty string, in HOCON you cannot omit the
   value
 - properties files support '!' as a comment character
 - HOCON allows comments on the same line as a key or value, while
   properties files only recognize comment characters if they
   occur as the first character on the line
 - HOCON interprets `${}` as a substitution

## Note on Windows and case sensitivity of environment variables

HOCON's lookup of environment variable values is always case sensitive, but
Linux and Windows differ in their handling of case.

Linux allows one to define multiple environment variables with the same
name but with different case; so both "PATH" and "Path" may be defined
simultaneously. HOCON's access to these environment variables on Linux
is straightforward; ie just make sure you define all your vars with the required case.

Windows is more confusing. Windows environment variables names may contain a
mix of upper and lowercase characters, eg "Path", however Windows does not
allow one to define multiple instances of the same name but differing in case.
Whilst accessing env vars in Windows is case insensitive, accessing env vars in
HOCON is case sensitive.
So if you know that you HOCON needs "PATH" then you must ensure that
the variable is defined as "PATH" rather than some other name such as
"Path" or "path".
However, Windows does not allow us to change the case of an existing env var; we can't
simply redefine the var with an upper case name.
The only way to ensure that your environment variables have the desired case
is to first undefine all the env vars that you will depend on then redefine
them with the required case.

For example, the the ambient environment might have this definition ...

```
set Path=A;B;C
```
.. we just don't know. But if the HOCON needs "PATH", then the start script must
take a precautionary approach and enforce the necessary case as follows ...

```
set OLDPATH=%PATH%
set PATH=
set PATH=%OLDPATH%

%JAVA_HOME%/bin/java ....
```

You cannot know what ambient environment variables might exist in the ambient environment
when your program is invoked, nor what case those definitions might have.
Therefore the only safe thing to do is redefine all the vars you rely on as shown above.
