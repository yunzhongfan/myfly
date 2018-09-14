## Welcome to MarkdownPad 2 ##

**MarkdownPad** is a full-featured Markdown editor for Windows.

### Built exclusively for Markdown ###

Enjoy first-class Markdown support with easy access to  Markdown syntax and convenient keyboard shortcuts.

Give them a try:

- **Bold** (`Ctrl+B`) and *Italic* (`Ctrl+I`)
- Quotes (`Ctrl+Q`)
- Code blocks (`Ctrl+K`)
- Headings 1, 2, 3 (`Ctrl+1`, `Ctrl+2`, `Ctrl+3`)
- Lists (`Ctrl+U` and `Ctrl+Shift+O`)

### See your changes instantly with LivePreview ###

Don't guess if your [hyperlink syntax](http://markdownpad.com) is correct; LivePreview will show you exactly what your document looks like every time you press a key.

### Make it your own ###

Fonts, color schemes, layouts and stylesheets are all 100% customizable so you can turn MarkdownPad into your perfect editor.

### A robust editor for advanced Markdown users ###

MarkdownPad supports multiple Markdown processing engines, including standard Markdown, Markdown Extra (with Table support) and GitHub Flavored Markdown.

With a tabbed document interface, PDF export, a built-in image uploader, session management, spell check, auto-save, syntax highlighting and a built-in CSS management interface, there's no limit to what you can do with MarkdownPad.

##二、字体
**这是加粗的文字**

*这是倾斜的文字*`

***这是斜体加粗的文字***

~~这是加删除线的文字~~

##三、引用
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容

##四、分割线
---
----
***
*****

##五、图片
**语法**

![图片alt](图片地址 ''图片title'')

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

**示例**

![blockchain](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/
u=702257389,1274025419&fm=27&gp=0.jpg "区块链")

##六、超链接
**语法**

[超链接名](超链接地址 "超链接title")
title可加可不加

**示例**
[简书](http://jianshu.com)
[百度](http://baidu.com)

##七、列表

- 无序列表用 - + * 任何一种都可以

- 语法：
- 列表内容
+ 列表内容
* 列表内容

注意：- + * 跟内容之间都要有一个空格

- 有序列表

语法：数字加点

1. 列表内容
2. 列表内容
3. 列表内容

注意：序号跟内容之间要有空格

- 列表嵌套

**上一级和下一级之间敲三个空格即可**

一级无序列表内容

   二级无序列表内容
   二级无序列表内容
   二级无序列表内容


   **  设置引用图片的大小
   Markdown 文档可以使用 ![]() 这种方式来引用图片，但是无法设置大小，只有 <img src="" width=""/> 才支持设置大小。

过大的图片会造成文档内容过于粗糙，图片大小的选取以图片内的文字和文档文字大约一致为宜。

图片居中显示可以使得文档阅读体验更好，因此除了将图片引用转换为 img 标签之外，也会将图片居中显示：<div align="center"> <img src="" width=""/> </div><br>


表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略



## 表格

表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略

## 九、代码
+  语法：
>>>
单行代码：代码之间分别用一个反引号包起来
 `int a =10;`

 >>>代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行

```
function fun(){
         echo "这是一句非常牛逼的代码";
    }
    fun();
```
##十、流程图
```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&```

效果如下：
简书不支持流程图，所以截了个图
