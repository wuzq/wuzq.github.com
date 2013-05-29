---

layout : post

category : manage

tags : [javascript]

title : javascript 获取地址栏参数

---

	var Request = { 
		QueryString:function(key){
			var reg = new RegExp('[\?\&]' + key + '=([^\&]*)(\&?)','i');
			var val = location.search.match(reg); 
			return val ? val[1] : val; 
		} 
	} 
	var key = Request.QueryString('key');