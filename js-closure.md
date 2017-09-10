## [阮一峰的教程](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)

```
　function f1(){
　　　　n=999;
　　}
　　f1();
　　alert(n); // 999
```
以上代码文章中说 n，未在var n = 999;
则n 默认的是全局变量，但是运行过程中必须先调用f1(); 如果不调用的话，n 会提示未定义，同样的下边的这段代码的nAdd这个函数变量也存在这个问题
```
function f1(){
　　　　var n=999;
　　　　nAdd=function(){n+=1}
　　　　function f2(){
　　　　　　alert(n);
　　　　}
　　　　return f2;
　　}
　　var result=f1();
　　result(); // 999
　　nAdd();
　　result(); // 1000
```
这个问题也有可能是浏览器的加载问题，目前不清楚，
关于介绍变量的作用域跟其他编程语言差不多，没有什么区别.

思考题
1
```
var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　return function(){
　　　　　　　　return this.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()());
```
2
```
var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　var that = this;
　　　　　　return function(){
　　　　　　　　return that.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()());
```
尝试解答代码段一：
getNameFunc: function() {//假设函数名为Ａ
return function()/*假设函数名为Ｂ*/ { return this.name; };
}
在函数里面构建函数的时候，闭包产生。
在函数Ｂ内调用函数Ａ的this.name,由于函数Ａ没有name属性，所以就去找全局变量name，找到了，所以返回“The Window”，要是没有找到，则返回“undefined”。
代码段二可以尝试将代码更改为：
var _this = this;
return function() { return _this.name +"__"+ this.name; };

第一个this window
第二个this 指的是 object？