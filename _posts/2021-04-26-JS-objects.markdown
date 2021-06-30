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

{% highlight JavaScript %}
let protoRabbit = {
  speak(line) {
    console.log(`The ${this.type} rabbit says '${line}'`);
  }
};
let killerRabbit = Object.create(protoRabbit);
killerRabbit.type = "killer";
killerRabbit.speak("SKREEEE!");
// → The killer rabbit says 'SKREEEE!'
{% endhighlight %}

<code>object expression</code> 中的諸如 <code>speak(line)</code> 之類的屬性 <code>property</code> 是定義方法 <code>method</code> 的一種簡寫方式，它創建了一個名為 <code>speak</code> 的屬性 <code>property</code>，並為其提供了一個函數 <code>function</code> 作為其值

<br/>


### **Classes**

因此，要建立<code>class</code>的<code>instance</code>，您必須建立一個取得 <code>derived</code>自適當<code>prototype</code> 的 <code>instance</code>，但您還必須確保它本身俱有此類的實例應該具有的屬性。這就是構造函數所做的。
{% highlight JavaScript %}
function makeRabbit(type) {
  let rabbit = Object.create(protoRabbit);
  rabbit.type = type;
  return rabbit;
}
{% endhighlight %}
<br/>

<code></code>JavaScript 提供了一種方法來使定義<code>constructor</code>更容易。如果將關鍵字 <code>new</code> 放在函數呼叫之前，則該函數將被視為 <code>constructor</code>。這表示會自動建立具有正確 <code>prototype</code> 的物件，在函數中綁定到 <code></code>this，並在函數結束時回傳。

建構物件時使用的 prototype 物件是通過存取 constructor function 的 prototype property 來找到的。

{% highlight JavaScript %}
function Rabbit(type) {
  this.type = type;
}
Rabbit.prototype.speak = function(line) {
  console.log(`The ${this.type} rabbit says '${line}'`);
};

let weirdRabbit = new Rabbit("weird");
{% endhighlight %}
<br/>

構造函數（實際上是所有函數）會自動獲得一個名為 <code>prototype</code> 的屬性 <code>property</code>，預設情況下，該屬性包含一個衍生自 <code>Object.prototype </code>的空物件。如果需要，您可以用新物件覆寫它。或者，您可以向現有物件添加屬性<code>property</code>，如上述範例所示。

按照慣例，構造函數的名稱大寫，以便於將它們與其他函數區分開來。

理解 <code>prototype</code> 與建構子關聯的方式（通過它的 <code>prototype</code> <code>property</code>）和 <code>object</code> 擁有原型的方式（可以通過 <code>Object.getPrototypeOf</code> 取得）之間的區別很重要。建構子的實際原型是 <code>Function.prototype</code>，因為建構子是函數。它的 <code>prototype</code> 屬性存放通過它創建的 <code>instance</code> 的 <code>prototype</code>。

{% highlight JavaScript %}
console.log(Object.getPrototypeOf(Rabbit) == Function.prototype); // → true
console.log(Object.getPrototypeOf(weirdRabbit) == Rabbit.prototype); // → true
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
