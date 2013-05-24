---

layout : post

category : manage

tags : [javascript 数组对象中的迭代方法]

title : javascript 数组对象中的迭代方法

---

/* javascript 数组对象中的迭代方法  
 * ECMAScript5为数组定义了5个迭代方法。每个方法都接受两个参数，第一个是进行迭代的函数，第二个是该函数的作用域对象【可选】。  
 * 进行迭代的函数接受三个参数，第一个是数组中要进行迭代的元素的值，第二个是数组候总要进行迭代的元素的位置，第三个是迭代数组本身。  
 * 1. every()   对数组中的每一项运行给定的函数，如果该函数对每一项都返回true，则返回true   
 * 2. filter()  对数组中的每一项运行给定的函数，返回该函数返回true的项组成的数组。  
 * 3. forEach() 对数组中的每一项运行给定的函数，这个方法没有返回值  
 * 4. map()     对数组中的每一项运行给定的函数，返回每次函数调用的结果组成的数组  
 * 5. some()    对数组中的每一项运行给定的函数，如果该函数对任意一项返回true，则返回true  
 *  
 * 这些迭代方法支持的浏览器有，IE9+，Firefox2+，Safari3+，Opera 9.5+，chrome  
 */ 
var num = [1,2,3,4,5,6,7,8,9];  
var everyResult = num.every(function(item, index, array) {  
    if(item > 2) {  
        return true;  
    }  
});  
alert(everyResult);  
 
var someResult = num.some(function(item) {  
    if(item > 2) {  
        return true;  
    }  
});  
alert(someResult);  
 
var filterResult = num.filter(function(item) {  
    if(item > 2) {  
        return true;  
    }  
});  
alert(filterResult);  
 
var mapResult = num.map(function(item) {  
    if(item > 2) {  
        return true;  
    }  
});  
alert(mapResult);  
var forEachResult = num.forEach(function(item) {  
    if(item > 2) {  
        return true;  
    }  
});  
alert(forEachResult); 
