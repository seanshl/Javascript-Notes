### Promise

1. **JS的异步执行**
	1. **概述**
		* js为**单线程执行**环境, 将任务的执行分成两种, **Synchronous**和**Asynchronous**。
		* 以下为js的异步编程的几种模式
	2. **Callback**
		* 	```
				function f1(f2) {
					f2();
				}
			```
		* pros * cons
			* +: 简单，容易理解和不熟
			* -: 不利于代码阅读和维护，耦合度高
	3. **Event listen**
	4. **Subscribe/Publish**

3. **Promise对象**
	1. **定义**
		Promise是一个对象，它起到proxy的作用, 充当异步操作与回调函数之间的中介. 使得异步操作具备同步操作的接口2，使得程序具备正常的同步运行的流程，回调函数不必一层层嵌套. 
	2. **理念**
		每一个异步任务立刻返回一个Promise对象, 由于是立刻返回 ，可以采用同步操作的流程。这个Promise有一个叫做**then**的方法, 允许指定回调函数，在异步任务完成后调用. 传统的回调写法使得代码横向发展而不是向下发展. 目标是使用正常的程序流程(同步)，来处理异步操作. 它先返回一个Promise对象，后面的操作以同步的方式，寄存在这个对象上面，等到异步操作有了结果再执行前期寄放在它上面的其他操作. 
	2. **与传统写法对比**
		* 传统写法
			```
				step1(function (value1) {
					step2(value1, funciton(value2) {
						step3(value2, funciton(value3) {
							step4(value3, function(value4) {
							//...
							});
						});
					});
				});
			```
		* Promise写法
			``` 
				(new Promise(step1))
					.then(step2)
					.then(step3)
					.then(step4);
			```
	3. **Promise接口**
		1. 三种状态
			* pending
			* resolved/fulfilled
			* rejected
		2. 变化路径
			* pending -> resolved
			* pending -> rejected
			* 变化只能发生一次，一旦状态变成后两者就不能再变了
		3. 使用then方法添加回调函数，可以接受两个回调函数，第一个是变成成功的，第二个是变成失败的.可以链式使用.
