# js-this

[阮一峰的网络日志](http://www.ruanyifeng.com/blog/2010/04/using_this_keyword_in_javascript.html)

this  跟运行时 ，而不是定义时
情况一 
符合  谁调用就指向谁
调用纯粹的函数  this 指向global

情况二
谁调用就跟谁
o 对象下添加了test()方法，this 就是o 对象

情况三 作为构造函数调用的时候

被挂到对象上 就跟对象，函数单独调用的时候就跟函数
　　
情况四 传谁跟谁，不传就是全局，类似于反射调用方法吧
   var x = 0;
　　function test(){
　　　　alert(this.x);
　　}
　　var o={};
　　o.x = 1;
　　o.m = test;
　　o.m.apply(o); //1
　  o.m.apply();  //0


但是上边的几个例子没有说明 函数在对象中的情况  
[Javascript中this关键字详解](http://www.cnblogs.com/justany/archive/2012/11/01/the_keyword_this_in_javascript.html)
如文中开头所说的

* 一般而言，在Javascript中，this指向函数执行时的当前对象。
* 值得注意，该关键字在Javascript中和执行环境，而非声明环境有关。

这几个例子更加结实清楚

```
var someone = {
    name: "Bob",
    showName: function(){
        alert(this.name);
    }
};

var other = {
    name: "Tom",
    showName: someone.showName
}

other.showName();　　//Tom
```

```
var someone = {
    name: "Bob",
    showName: function(){
        alert(this.name);
    }
};
someone.showName();//Bob
```

```
var name="tom"
var someone = {
    name: "Bob",
    showName: function(){
        alert(this.name);
    }
};
var a =someone.showName;
a();//tom
```
a 相当于独立调用函数了


```
var name = "window";

var Bob = {
    name: "Bob",
    showName: function(){
        alert(this.name);
    }
};

var Tom = {
    name: "Tom",
    showName: function(){
        var fun = Bob.showName;
        fun();
    }
};

Tom.showName();　　//window

```


```
var name = "window";

var Bob = {
    name: "Bob",
    showName: function(){
        alert(this.name);
    }
};

var Tom = {
    name: "Tom",
    showName: function(){
        var fun = Bob.showName;
        return fun();
    }
};

var a=Tom.showName;　　
a();//window

```

```
var name = "Bob"; 
var nameObj ={ 
    name : "Tom", 
    showName : function(){ 
        alert(this.name); 
    }, 
    waitShowName : function(){
        var that = this;
        setTimeout(that.showName(), 1000);
    }
};
  
nameObj.waitShowName();//tom
```