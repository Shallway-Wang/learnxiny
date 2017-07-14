1. HTML（超文本标记语言：HyperText **Markup** Language）
网站制作的基础，浏览器打开任意一个网页，查看其源码都是看到的HTML。因为HTML是网站页面最终的表现形式。网站页面所有的内容都需要通过HTML展现，所以学习PHP必学的基础首先就是HTML，HTML很简单，它甚至都不能算做一门编程语言，而是一个标记语言。HTML就是一些标签，页面的内容就放在一个个标签里面。
2. CSS（层叠样式表：Cascading **Style** Sheets）
学习了HTML，知道页面的内容是怎么展现的了。那么我们是不是可以把页面展现得更漂亮呢（毕竟这是一个看脸的时代~），平时我们看到的那些漂亮的网站页面，大多数都是通过CSS来美化的。**CSS代码都是些样式属性，这些样式属性添加到HTML元素上面，对应的HTML元素的样式就会被CSS改变**，学起来会很快，因为编写HTML和CSS可以直接在浏览器上面看到效果，非常有意思！
3. JavaScript
主要用来向HTML页面添加**交互行为**。
JavaScript会比HTML和CSS难一点，不过入门很简单，跟着教程练习学起来会更加顺利。如今JavaScript被炒得比较火（库和框架满天飞，用得最多的还是jQuery），不过学习好基础才是最重要的，正所谓万变不离其宗。学习建网站，当然就要勤动手，巩固好基础。学了JavaScript，对PHP中的很多概念也都明白了，因为编程语言里面很多东西都是相通的。
4. MySQL（结构化查询语言：Structured Query Language）
对于MySQL数据库，可以先学习基础就行了，能够熟练地对数据库进行【增删改查】操作就够用了。等学习了PHP，再来对MySQL进行加深学习，这样会事半功倍。数据库并不像想象中的那么难懂。
5. LAMP
LAMP也就是Linux、Apache、MySQL和PHP。在实验楼的实验环境中，已经搭建好了LAMP环境，学习PHP的时候题主就不用浪费时间去折腾搭建环境了，可以先看看LAMP是如何协作的。在实验楼中开始实验，就会创建一个LAMP环境，而且可以长期保存代码。等PHP学习得差不多了，再来学习如何自己搭建LAMP环境并部署到生产环境，这时就不会觉得LAMP那么抽象。
6. PHP（Hypertext Preprocessor：超文本预处理器）
PHP是一种开源的通用计算机脚本语言，尤其适用于网络开发并可嵌入HTML中使用。该语言的主要目标是允许 web 开发人员**快速编写动态生成的 web 页面**，但 PHP 的用途远不只于此。
入门了HTML、CSS和JavaScript之后，对于编程已经有自己的理解了，这时学习PHP会容易很多，至少知道变量、语句、函数、对象等等东西，学习的过程中也会自信很多。先学习基础课程实验，然后跟着实验楼多做一些小项目，实践出真知，加深对PHP的理解。这时再去看WordPress里面的代码，会发现大多数PHP代码都能看懂。想修改下WordPress主题什么的都是小case~。可以自己定制WordPress功能啦~\(≧▽≦)/~


HTML stands for HyperText Markup Language. 
It is a language which allows us to **write pages for the world wide web**.
It is a markup language, it enables us to write webpages using code to indicate **how text and data should be displayed**.
In fact, html files are simple text files.
What is this markup? It is a method of organising the page's data by **surrounding it with opening tags and closing tags**.
This markup serves to give significance to the text that it encloses. 
Like other computer languages, HTML has many versions. Here we will talk about HTML5.

**NOTE :**  You can test the different tags and elements as you progress through the tutorial on a site like [codepen](http://codepen.io/pen/) in order to see their effects, understand how they work and familiarise yourself with the language.
This article is concerned principally with HTML syntax and some useful tips.


```html
<!-- Comments are enclosed like this line! -->

<!-- #################### The Tags #################### -->
   
<!-- Here is an example HTML file that we are going to analyse. -->

<!doctype html>
	<html>
		<head>
			<title>My Site</title>
		</head>
		<body>
			<h1>Hello, world!</h1>
			<a href = "http://codepen.io/anon/pen/xwjLbZ">Come look at what this shows</a>
			<p>This is a paragraph.</p>
			<p>This is another paragraph.</p>
			<!-- unordered list -->
			<ul>
			   <!-- list -->
				<li>This is an item in a non-enumerated list (bullet list)</li>
				<li>This is another item</li>
				<li>And this is the last item on the list</li>
			</ul>
		</body>
	</html>

<!-- An HTML file always starts by indicating to the browser that the page is HTML. -->
<!doctype html>

<!-- After this, it starts by opening an <html> tag. -->
<html>

<!-- that will be closed at the end of the file with </html>. -->
</html>

<!-- Nothing should appear after this final tag. -->

<!-- Inside (between the opening and closing tags <html></html>), we find: -->

<!-- A header defined by <head> (it must be closed with </head>). -->
<!-- The header contains some description and additional information which are not displayed; this is metadata. -->

<head>
	<title>My Site</title><!-- The tag <title> indicates to the browser the title to show in browser window's title bar and tab name. -->
</head>

<!-- After the <head> section, we find the tag - <body> -->
<!-- Until this point, nothing described will show up in the browser window. -->
<!-- We must fill the body with the content to be displayed. -->

<body>
	<h1>Hello, world!</h1> <!-- The h1 tag creates a title. -->
	<!-- There are also subtitles to <h1> from the most important (h2) to the most precise (h6). -->
	<a href = "http://codepen.io/anon/pen/xwjLbZ">Come look at what this shows</a> <!-- a hyperlink to the url given by the attribute href="" -->
	<p>This is a paragraph.</p> <!-- The tag <p> lets us include text in the html page. -->
	<p>This is another paragraph.</p>
	<ul> <!-- The tag <ul> creates a bullet list. -->

	<!-- To have a numbered list instead we would use <ol> giving 1. for the first element, 2. for the second, etc. -->
		<li>This is an item in a non-enumerated list (bullet list)</li>
		<li>This is another item</li>
		<li>And this is the last item on the list</li>
	</ul>
	
	
	<!-- 有序列表，ordered list -->
	<ol>
    <li>This is an item in a non-enumerated list (bullet list)</li>
    <li>This is another item</li>
    <li>And this is the last item on the list</li>
  </ol>
</body>

<!-- And that's it, creating an HTML file can be simple. -->

<!-- But it is possible to add many additional types of HTML tags. -->

<!-- To insert an image. -->
<img src="http://i.imgur.com/XWG0O.gif"/> <!-- The source of the image is indicated using the attribute src="" -->
<!-- The source can be an URL or even path to a file on your computer. -->

<!-- It is also possible to create a table. -->

<table> <!-- We open a <table> element. -->
	<tr> <!-- <tr> allows us to create a row. -->
		<th>First Header</th> <!-- <th> allows us to give a title to a table column. -->
		<th>Second Header</th>
	</tr>
	<tr>
		<td>first row, first column</td> <!-- <td> allows us to create a table cell. -->
		<td>first row, second column</td>
	</tr>
	<tr>
		<td>second row, first column</td>
		<td>second row, second column</td>
	</tr>
</table>

```

## Usage

HTML is written in files ending with `.html`.

## To Learn More 

* [wikipedia](https://en.wikipedia.org/wiki/HTML)
* [HTML tutorial](https://developer.mozilla.org/en-US/docs/Web/HTML)
* [W3School](http://www.w3schools.com/html/html_intro.asp)


