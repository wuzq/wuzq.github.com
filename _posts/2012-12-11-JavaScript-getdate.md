---
layout : post
category : tech-javascript
tags : javascript

---
代码如下：
	<html> 
	<body> 
	<script type="text/javascript"> 
	function getCurrentDate(){ 
		var oDate = new Date(); 
		return oDate.getFullYear() + "-" + 
		checkTime((oDate.getMonth() + 1)) + "-" + 
		checkTime(oDate.getDate()) + " " + 
		checkTime(oDate.getHours()) + ":" + 
		checkTime(oDate.getMinutes()) + ":" + 
		checkTime(oDate.getSeconds()); 
	} 
	//如果小于10则，前面加0 
	function checkTime(i){ 
		if(i<10){ 
		return "0" + i; 
		} 
		return i; 
	} 

	function getWeekDay(){ 
		var aWeekDay = new Array("周日", "周一", "周二", "周三", "周四", "周五", "周六"); 
		return aWeekDay[new Date().getDay()]; 
	} 

	document.write("现在是 " + getCurrentDate() + " " + getWeekDay()); 
	</script> 
	<body> 
	</html> 


