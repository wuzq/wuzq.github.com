---

layout : post

category : manage

tags : [javascript]

title : javaScript 数组取最大最小值

---

	<script>
	//JavaScript数组取最大值
	Array.prototype.max = function(){
		var temp = this[0];
		for(var i=1; i<this.length; i++){
			if(this[i] > temp){
				temp = this[i];
			}
		}
		return temp;
	}
	//JavaScript数组取最小值
	Array.prototype.min = function(){
		var temp = this[0];
		for(var i=1; i<this.length; i++){
			if(this[i] < temp){
				temp = this[i];
			}
		return temp;
		}
	}
	var data = [5, 1, 9, 2, 8, 3, 7, 4, 6];
	alert("max: " + data.max() + "\nmin: " + data.min());
	</script>