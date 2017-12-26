# MarkDown语法初步

## 这篇文章将实验基础的md控件

>这里有一篇 [MarkDown语法说明（中文简体版）](https://www.appinn.com/markdown/ "点击跳转")
>我将以这个教程来练习并抽取我认为重要的部分。

## 基础知识

### 兼容HTML

不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。不需要额外标注这是 HTML 或是 Markdown；只要直接加标签就可以了。

要制约的只有一些 HTML 区块元素――比如

    <div>、<table>、<pre>、<p>

等标签，必须在前后加上空行与其它内容区隔开，还要求它们的开始标签与结尾标签不能用制表符或空格来缩进。Markdown 的生成器有足够智能，不会在 HTML 区块标签外加上不必要的

    *\<p\>*

标签。

在 HTML 区块标签间的 Markdown 格式语法将不会被处理。比如，你在 HTML 区块内使用 Markdown 样式的*强调*会没有效果。

### 特殊字符自动转换

*<* 与 *&* 自动转换，无需特殊标记，
如版权符号 *&copy;* 只需直接写 *\&copy;* 即可。

### 标题

Markdown 支持两种标题的语法，类 Setext 和类 atx 形式。

类 Setext 形式是用底线的形式，利用 = （最高阶标题）和 - （第二阶标题），例如：

    This is an H1
    =============

    This is an H2
    -------------
任何数量的 = 和 - 都可以有效果。

类 Atx 形式则是在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶，例如：

    # 这是 H1

    ## 这是 H2

    ###### 这是 H6
你可以选择性地「闭合」类 atx 样式的标题，这纯粹只是美观用的，若是觉得这样看起来比较舒适，你就可以在行尾加上 #，而行尾的 # 数量也不用和开头一样（行首的井字符数量决定标题的阶数）：

    # 这是 H1 #

    ## 这是 H2 ##

    ### 这是 H3 ######

### 区块引用 Blockquotes

在每行的最前面加上 *>* ：

    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    > consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
    >
    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    > id sem consectetuer libero luctus adipiscing.

效果如下：
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
>
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.

Markdown 也允许你偷懒只在整个段落的第一行最前面加上 *>*。
区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 *>*。
引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等。

### 列表

无序列表使用星号、加号或是减号作为列表标记，*+-后面记得空格。

有序列表则使用数字接着一个英文句点，数字是多少无所谓，最好从1开始。

1. A
1. B
1. C

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符。

如果要在列表项目内放进引用，那 *>* 就需要缩进。

如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符。

如果在行首出现数字-句点-空白，要避免这样的状况，你可以在句点前面加上反斜杠。

98\. 99. 100. He made it!

### 代码区块

和程序相关的写作或是标签语言原始码通常会有已经排版好的代码区块，通常这些区块我们并不希望它以一般段落文件的方式去排版，而是照原来的样子显示，Markdown 会用 \<pre\> 和 \<code\> 标签来把代码区块包起来。
缩进 4 个空格或是 1 个制表符就可以，例

    <p>这是代码区块。<p>

一个代码区块会一直持续到没有缩进的那一行（或是文件结尾）。

代码区块中，一般的 Markdown 语法不会被转换，像是星号便只是星号，这表示你可以很容易地以 Markdown 语法撰写 Markdown 语法相关的文件。

### 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。

---

## 区段元素

### 链接

Markdown 支持两种形式的链接语法： 行内式和参考式两种形式。

不管是哪一种，链接文字都是用 [方括号] 来标记。

要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：

    This is [an example](http://example.com/ "Title") inline link.

    [This link](http://example.net/) has no title attribute.

如果你是要链接到同样主机的资源，你可以使用相对路径。

参考式的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：

    This is [an example][id] reference-style link.

接着，在文件的任意处，你可以把这个标记的链接内容定义出来：

    [id]: http://example.com/  "Optional Title Here"

链接内容定义的形式为：

* 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
* 接着一个冒号
* 接着一个以上的空格或制表符
* 接着链接的网址
* 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着

链接网址也可以用方括号包起来。

链接辨别标签可以有字母、数字、空白和标点符号，但是并不区分大小写。

隐式链接标记功能让你可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号[]。

    Search in this [baidu][] page.

