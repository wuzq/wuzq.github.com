---

layout : post

category : manage

tags : [javascript]

title : javascript Object对象

---

	一：Object的带参数构造函数
	var obj = new Object(value);
	 
	value是js中的元类型，返回的是该元类型的包装类。
	var aNumber= new Object(1);
	var aBoolean = new Object(true);
	var aString = new Object("str"); //与java不同，js有元类型string和string包装类String。
	 
	如果我们就是不按要求传元类型，传个对象会怎么样勒？
	var obj1 = new Object();
	var obj2 = new Object(obj1);
	这个效果和下面代码一样...
	var obj1 = new Object();
	var obj2 = obj1;
	 
	如果我们无聊一点，传null，会怎样...
	var obj = new Object(null);
	效果等同
	var obj = new Object(); //......好像有点太无聊了
	 
	二：Object的属性的属性名的讨论。
	我们都知道可以用下面的方法给js对象添加一个属性。
	obj[key] = value;
	一般情况下，这个key是一个String类型的。但是我们如果用其他的类型勒？
	obj[1] = "...";
	obj[0.1] = "...";
	obj[true] = "...";
	obj[new Object()] = "...";
	obj[null] = "...";
	有点傻眼吧，这些代码，在js中通通没有错。
	是不是js支持用这些对象做为属性的键勒？不是的！看代码
	var o1 = new Object(); 
	var o2 = new Object(); 
	var obj = new Object(); 
	obj[o1] = 1; 
	alert(obj[o2]);
	用o1做键设值，居然可以用o2做键取值。为什么？
	原因在于，当我们写obj[o1] = 1;的时候，js实际执行的是obj[o1.toString()] = 1;
	为了验证这一点，代码。
	var obj = new Object(); 
	obj[new Object()] = 1; 
	alert(obj.toString()); 
	alert(obj['[object Object]']); 
	//注意这个只在IE中有效
	那么我们可以推论出，对于数值和布尔值两种情况，js为我们做同样的事情，把数值和布尔值转换为字符串。（这里我本来猜测js先是把基本类型装箱为对象，然后调用toString方法，但是通过用prototype修改Number类的toString方法发现，并非如此，包装类的toString方法并没有被调用，js是用其他方法转换了数据类型）
	所以，当你定义obj[1]，实际上你是定义obj["1"]。
	 
	至于null的情况，权威指南中有这么一段描述。
	When null is used in a Boolean context, it converts to false. When used in a numeric context, it converts to 0. And when used in a string context, it converts to "null".
	大概意思就是，你想要字符串，null就变成字符串"null"。
	 
	结论，js对象的属性的属性名，只能是字符串，所以写在[]中的其他东西，终将转化为字符串

	转载地址：<a href="http://cymoft.blog.51cto.com/324099/63288">http://cymoft.blog.51cto.com/324099/63288</a>