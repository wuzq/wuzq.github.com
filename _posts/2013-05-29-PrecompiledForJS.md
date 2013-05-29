---

layout : post

category : manage

tags : [javascript]

title : JavaScript 的“预编译”

---

	
	先看“变量式”函数的写法，代码：
	<script type="text/javascript">
	var func = function(){
		alert(1);
	}
	func(); //第一次调用func，输出1
	
	func = function(){
		alert(2);
	}
	func(); //第二次调用func，输出2
	</script>
	这个程序的结果告诉我们：在第一次调用函数之后，函数变量又被赋予了新的函数代码体，
	使得第二次调用该函数时，出现了不同的输出。
	
	把上面的代码改成“定义式”函数的写法，代码：
	<script type="text/javascript">
	function func(){
		alert(1);
	}
	func(); //输出2而不是1
	
	function func(){
		alert(2);
	}
	func();//输出2
	</script>
	两个标识符完全相同的函数，在其他编程语言中应该是非法的(起码java中是)。
	但在javascript中，这没错，不过程序运行之后却发现两次调用都只输出了第二个函数
	里的内容，显然第一个函数没有起到任何作用。Why?
	
	JavaScript执行引擎并非一行一行地分析和执行程序，而是一段一段地分析执行。而且，
	在同一段程序的分析执行中，定义式的函数语句会被提取出来优先执行。函数定义执行
	完之后，才会按顺序执行其他语句代码。也就是说，在第一次调用func之前，第一个函
	数语句定义的代码逻辑，已被第二个函数定义语句覆盖了。所以，两次都调用都是执行
	最后一个函数逻辑了。
	
	如果把这个javascript代码分成两段，输出才是按顺序来调用的，这也证明了javascript
	的确是一段段地执行的，代码：
	<script type="text/javascript">
		function func(){
			alert(1);
		}
		func(); //输出1
	</script>
	<script type="text/javascript">
		function func(){
			alert(2);
		}
		func(); //输出2
	</script>
	
	一段代码中的定义式函数语句会优先执行，这似乎有点象静态语言的编译概念。所以，这
	一特征也被有些人称为：javascript的“预编译”。
	