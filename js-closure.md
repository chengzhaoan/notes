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
