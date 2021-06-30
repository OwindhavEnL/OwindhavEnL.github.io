---
layout: post
title:  "Objects"
date:   2021-04-26 23:15:00 +0800
categories: Programming
tags: JavaScripts

---
### **private**
通常在屬性名稱的開頭加上_符號，表示這些屬性是 private 的。
<br>

### **Methods**

Methods 僅為接 function value 的屬性
> Methods are nothing more than properties that hold function values.

{% highlight JavaScript %}
function speak(line) {
  console.log(`The ${this.type} rabbit says '${line}'`);
}
let whiteRabbit = {type: "white", speak}; // speak 為 method
let hungryRabbit = {type: "hungry", speak}; // speak 為 method
{% endhighlight %}
<br>

### **this**

{% highlight JavaScript %}
whiteRabbit.speak("White"); // this 指向呼叫方法的物件 whiteRabbit
hungryRabbit.speak("Hungry"); // this 指向呼叫方法的物件 hungryRabbit
{% endhighlight %}

換句話說，可以將 <code>this</code> 想成一個額外除傳入的參數
> You can think of this as an extra parameter that is passed in a different way. 

如果需要明確的將 this 傳入方法，可以使用該方法的 <code>call()</code> method
{% highlight JavaScript %}
speak.call(hungryRabbit, "Burp!"); // hungryRabbit 為物件
{% endhighlight %}

每個方法都有自己的 this，其值視呼叫方式而定
> Since each function has its own this binding, whose value depends on the way it is called

<br/>

### **Arrow Functions**

<code>Arrow Function</code> 表示式適合 <code>non-method</code> 方法

{% highlight JavaScript %}
'use strict';

var obj = { // var 沒有建立一個新的 scope
  i: 10,
  b: () => console.log(this.i, this),
  c: function() {
    console.log(this.i, this);
  }
}

obj.b(); // → undefined, Window {...} (or the global object)
obj.c(); // → 10, Object {...}
{% endhighlight %}


{% highlight JavaScript %}
var obj = {
    num: 100
}

window.num = 2020; // yikes!

var add = function (a, b, c) {
  return this.num + a + b + c;
}

// call
var result = add.call(obj, 1, 2, 3) // 傳入 obj 的 scope
console.log(result) // → 106

// apply
const arr = [1, 2, 3]
var result = add.apply(obj, arr) // 傳入 obj 的 scope
console.log(result) // → 106

// bind
var result = add.bind(obj) // 傳入 obj 的 scope
console.log(result(1, 2, 3)) // → 106

// Arrow Function
var add = (a, b, c) => this.num + a + b + c;

// call
console.log(add.call(obj, 1, 2, 3)) // → 2026

// apply
const arr = [1, 2, 3]
console.log(add.apply(obj, arr)) // → 2026

// bind
const bound = add.bind(obj)
console.log(bound(1, 2, 3)) // → 2026
{% endhighlight %}

<br/>

### **Prototype**

{% highlight JavaScript %}
console.log(Object.getPrototypeOf({}) == Object.prototype);
// → true

console.log(Object.getPrototypeOf(Object.prototype));
// → null

console.log(Object.getPrototypeOf(Math.max) == Function.prototype);
// → true

console.log(Object.getPrototypeOf([]) == Array.prototype);
// → true

{% endhighlight %}
<br/>

### **Classes**

{% highlight JavaScript %}
{% endhighlight %}
<br/>

### ****

{% highlight JavaScript %}
{% endhighlight %}
<br/>

### ****

{% highlight JavaScript %}
{% endhighlight %}
<br/>

### ****

{% highlight JavaScript %}
{% endhighlight %}
<br/>
