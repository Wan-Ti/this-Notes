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

```
