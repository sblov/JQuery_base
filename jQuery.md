## jQuery

### 一、基本

```javascript
<!-- https://www.bootcdn.cn/ -->
<script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.js"></script>
```

#### 	1.入口函数

​		js的入口函数执行要比jQuery的入口函数晚
		jQuery与js的入口函数都会等页面加载完后执行，但对于图片等资源访问加载，jQuery不会等待
		jQuery不会覆盖事件

#### 	2.jQuery核心函数/对象

​		jQuery核心函数（$/jQuery）
		jQuery核心对象（执行jQuery函数返回的对象）

​		1.作为函数调用：$(param)
			参数为函数：当DOM加载完后，执行此回调函数
			参数为选择器字符串：查找所有匹配的标签，并将它们封装为jQuery对象
			参数为DOM对象：将DOM对象封装为jQuery对象
			参数为html标签字符串：创建标签对象并封装成jQuery对象
		2.作为对象使用：$.xx()
			$.each();
			$.trim();

#### 	3.jQuery与DOM对象区别

​		DOM对象（js对象）：使用js的方式获取到的元素对象
		jQuery对象：使用jq方式获取到的元素对象
		jQuery对象就是js对象的集合，伪数组

```html

	<input type="text" name="text" id="text">
	<button id="but-1" >jsBut</button>
	<button id="but-2" >jQueryBut</button>

	<ul>
		<li>demo-1</li>
		<li>demo-2</li>
		<li>demo-3</li>
		<li>demo-4</li>
		<li>demo-5</li>
		<li>demo-6</li>
		<li>demo-7</li>
		<li>demo-8</li>
		<li>demo-9</li>
		<li>demo-10</li>
	</ul>
```

```javascript
//入口函数
	/*
		js的入口函数执行要比jQuery的入口函数晚
		jQuery与js的入口函数都会等页面加载完后执行，但对于图片等资源访问加载，jQuery不会等待
		jQuery不会覆盖事件
	 */
	/*window.onload = function(){
		console.log("window.onload")
	};
	$(document).ready(function() {
		console.log("$(document)");
	});
	$(function(){	
		console.log("$();");
	});*/
	
	//DEMO
	window.onload = function(){
		document.getElementById('but-1').onclick = function(){
			var input = document.getElementById("text").value;
			alert(input);
		};
	};
	$(function(){
		$('#but-2').click(function(){
			alert($('#text').val());
		});
		var but = $('#but-2');
		console.log(but.html());
	
		/*
			DOM对象（js对象）：使用js的方式获取到的元素对象
			jQuery对象：使用jq方式获取到的元素对象
			jQuery对象就是js对象的集合，伪数组
		 */
		var btn = document.getElementById("but-1");
		var $btn = $("#but-1");
		console.log($btn);
		//DOM转换为jQuery对象
		console.log($(btn));

		var $lis = $("li");
		for(var i = 0;i<$lis.length ;i++){
			if(i %2 ==0){
				$lis[i].style.backgroundColor = "pink";
			}else{
				$lis[i].style.backgroundColor = "yellow";
			}
		}

	});
	
```

### 三、选择器

#### 	1.基本选择器

| 名称       | 用法              | 描述                               |
| :--------- | ----------------- | ---------------------------------- |
| ID选择器   | $("#id")          | 获取指定ID的元素                   |
| 类选择器   | $(".class")       | 获取同一类class的元素              |
| 标签选择器 | $("div")          | 获取同一类标签的所有元素           |
| 并集选择器 | $("div,p,li")     | 使用逗号分隔，只有符合条件之一即可 |
| 交集选择器 | $("div.redClass") | 获取class为redClass的div元素       |

> 和css选择器用法一样	

#### 	2.层级选择器

| 名称       | 用法       | 描述                       |
| :--------- | ---------- | -------------------------- |
| 子代选择器 | $("ul>li") | 使用>号，获取子层级元素    |
| 后代选择器 | $("ul li") | 使用空格，获取所有后代元素 |

> 和css选择器用法一样	

#### 	3.过滤选择器

| 名称       | 用法                             | 描述                         |
| ---------- | -------------------------------- | ---------------------------- |
| :eq(index) | $("li:eq(2)").css("color","red") | 获取li元素中索引为2的元素    |
| :odd       | $("li:odd").css("color","red")   | 获取li元素中索引为奇数的元素 |
| :even      | $("li:even").css("color","red")  | 获取li元素中索引为偶数的元素 |

```html

	<ul>
		<li id="l1">1</li>
		<li class="green">2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
		<li>10</li>
	</ul>

	<div class="green">
		<p>aaaaa</p>
		<p>aaaaa</p>
		<div>
			<p>bbb</p>
			<p>bbb</p>
		</div>
	</div>
```

```javascript
$(function(){

		/*
			基本选择器
		 */
		//jQquery设置样式
		//css(name,value)
		
		//$("#l1").css('backgroundColor', 'red');//id选择器

		//$(".green").css('backgroundColor', 'green');//class选择器


		//交集 并集
		//$("li.green").css('backgroundColor', 'green');
		//$("#l1,.green").css('backgroundColor', 'pink');

		/*
			层级选择器
		 */
		//$("div.green>p").css('backgroundColor', 'pink');//子代选择器
		//$("div.green p").css('backgroundColor', 'pink');//后代选择器 
		

		/*
			过滤选择器
		 */
		$("li:even").css('backgroundColor', 'yellow');
		$("li:odd").css('backgroundColor', 'pink');
		$("li:first").css('color', 'red');
		$("li:last").css('color', 'red');
		$("li:eq(2)").css('color', 'red');
		$("li:gt(5)").css('color', 'red');
		$("li:lt(5)").css('color', 'red');

		/**/

	});
```



#### 	4.筛选选择器

| 名称               | 用法                       | 描述                |
| ------------------ | -------------------------- | ------------------- |
| children(selector) | $("ul").children("li")     | 相当于$("ul>li")    |
| find(selector)     | $("ul").find("li")         | 相当于$("ul li")    |
| siblings(selector) | $("#first").siblings("li") | 查找兄弟节点        |
| parent()           | $("#first").parent()       | 查找父节点          |
| eq(index)          | $("li").eq(2)              | 相当于$("li:eq(2)") |
| next()             | $("li").next()             | 找下一个兄弟节点    |
| prev()             | $("li").prev()             | 找上一个兄弟节点    |

#### DEMO：

jQuery_2.html