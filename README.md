# this-Notes

**this面试题1**

```
var a = {
    name:"里面的name",
    sayName:function(){
        console.log("this.name = " + this.name);
    }
};
var name = "外面的name";
function sayName(){
    var sss = a.sayName;
    sss();//this.name = ?
    a.sayName();// this.name = ?
    (a.sayName)();// this.name = ?
    (b = a.sayName)();// this.name = ?
}
sayName();
```
解题方法：将代码改写为

```
var a = {
    name:"里面的name",
    sayName:function(){
          console.log("this.name = " + this.name);
   }
};
var name = "外面的name";
function sayName(){
    var sss = a.sayName;
    sss.call(undefined);//this 是 undefined
    a.sayName.call(a);//this 是 a
    (a.sayName).call(a);//this 是 a
    b.ca;;(undefined);// this 是 undefined
}
sayName();
```

**this面试题2**

```
var length = 10;
function fn() {
    console.log(this.length);
}

var obj = {
   length:5;
   method: function(fn) {
    fn();
    arguments[0]();
   }
};

obj.method(fn,1);
提问：输出结果是什么？
```

解题方法：改写代码

```
var length = 10;
function fn() {
    console.log(this.length)
}

var obj = {
    length: 5;
    method: function(fn) {
       fn.call(undefined);
       // this是undefined;
       arguments[0].call(arguments);
       // this 是auguments,也就是[fn,1]
      }
};

obj.method.call(obj,fn,1);
```

#### 总结

**关于React的知识点**

* 两种方式引入React & ReactDOM
* React.createElement('div' | 函数 | 类) 
* 类组件、函数组件如何获取外部数据props
* 类组件、函数组件如何使用内部数据state
* 类组件如何绑定事件
* 函数组件如何绑定事件

**React V.S. Vue**

* 相同点
都是对视图的封装，React是用类和函数表示一个组件，而Vue是通过构造选项构造了一个组件。</br>
都提供了createElement的XML简写，React提供的是JSX语法，而Vue提供的是模板写法.</br>

* 不同点
React是把HTML放在JS里写(HTML in JS ),而Vue是把JS放在HTML里写(JS in HTML)

