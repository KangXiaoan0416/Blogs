---
title: setTimeout函数
date: 2018-06-12 17:10:25
tags: js,setTimeout
categories: JavaScript
---
## JS中setTimeout函数的坑点

```
var timeout_array = new Array();
	var timeout_map = new Map();
	function initTimeout_(array) {
		for(var i = 0; i < array.length; i++) {
			var time = array[i] * 1000;
			var timeInterval = setTimeout('printSomething()', time);    (1)
			var index = timeout_array.length;
			timeout_array[index] = timeInterval;
			timeout_map.set(i, index);
		}
	}

	function printSomething() {
		console.log('你好');
	}

	function test() {
		var test_array = [1,5,7,10,11]
		initTimeout_(test_array);
		//setInterval('printSomething("time")', 3000);
	}
	test();
```
> 在上面的代码中，函数initTimeout_实现传入一个数组变量，然后动态创建定时器执行任务，
我第一次写的时候在代码一中的位置是这么写的 setTimeout(printsomething, time)，
然后，然后代码执行了一遍，没有任何定时效果，直接就打印出来了，很明显，定时器没有成功。那么这是为什么呢？，setTimeout第一个参数到底应该怎么传呢。

### 下面是我在网上找到的一篇博客上说的
1. 第一种参数，传递的是一个global()方法，该方法会在全局变量中寻找。
2. 第二种参数，传递的是一个global函数名，该方法会在局部变量中寻找。
3. 例子如下
```
window.onload = function(){
    var local = function(){
       function global(){
            alert("这是局部变量！");
        }
        setTimeout("global()",1000);//"这是全局变量！"
        setTimeout(global,1000);//"这是局部变量！"
    };
    local();
};
function global(){
    alert("这是全局变量！")
}
```
>setTimeout("global()",1000);方法虽然写在了局部变量中，但是传入的是一个方法，它会忽略局部变量中的global()方法，直接去全局中寻找匹配项。

>setTimeout(global,1000);方法传入的就是一个函数名，所以就会直接调用局部变量中的匹配项.

>所以，setTimeout()方法的第一个参数是否加双引号，由你调用的函数的作用域决定。

### 总结，这个函数我还有一些保留疑问，比如为什么方法执行了，但执行了一次？明明定时器没有生效啊，为什么会执行呢？
