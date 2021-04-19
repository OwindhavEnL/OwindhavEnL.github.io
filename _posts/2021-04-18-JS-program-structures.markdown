---
layout: post
title:  "JavaScript Program Structures"
date:   2021-04-18 08:30:00 +0800
categories: Programming
tags: JavaScripts

---



###  **運算式 Expression**

- 產生 value 的程式片段稱為 expression 
- 每個逐字寫的 value 也是一個 expression，如 22 或是 "tom"
- 最簡單的 statement 為 expression 加上分號，如 1; !false;
<br/>
<br/>

### **Binding**

- To catch and hold values, JavaScript provides a thing called a binding, or variable.
- 為了捕獲和保留值，JavaScript提供了一種稱為綁定或變量的東西。
<br/>
<br/>

### **var let const**
var 是 function scope 的。只要在 function 中使用 var 宣告變數，該變數就僅存在於 function 中。 如果變數是在 function 外部建立的的，則它將存在於 outer scope 中。

{% highlight JavaScript %}
var hours = 1;

function Sleep()
{		
  {
    var hours = 2; // 被限制在該 Sleep() 的 scope 中
  }
  console.log(hours); // → 2
}

Sleep();
console.log(hours); // → 1

{% endhighlight %}

let/const 定義的變數只作用在當前區塊(scope)中
{% highlight JavaScript %}
let x = 1;
{
  let x = 2; // x = 2 被限制在該 block 的 scope 中
}
console.log(x); // → 1 

{% endhighlight %}

let 可以同時定義多個變數
{% highlight JavaScript %}
let one = 1, two = 2;
{% endhighlight %}

const 不能被重新 assign 值，但 const 物件的內容可以修改

{% highlight JavaScript %}

const me = {name : 'John', age : 20}

me = {name : 'Mike', age : 10} 
// TypeError: 指派值到常數變數

me.name = 'Tom';
console.log(me.name); // → 'Tom' const 物件的內容可以修改 
{% endhighlight %}

let 與 var 的差異
{% highlight JavaScript %}
var x = 1;
let y = 1;

if (true) {
  var x = 2;
  let y = 2;
}

console.log(x); // → 2 
console.log(y); // → 1

{% endhighlight %}

let 變數只有在完全初始化後才能被讀取/寫入，這在宣告他們時發生（如果在宣告中未指定初始值，則該變數將使用undefined值進行初始化）。在初始化之前存取變數導致ReferenceError。這與var變量不同，var變量如果在聲明它們之前被訪問，將返回undefined的值。從該塊的開始直到初始化完成，該變量被稱為處於 “Temporal Dead Zone”（TDZ）中。

{% highlight JavaScript %}
{ 
  // TDZ starts at beginning of scope
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  var bar = 1;
  let foo = 2; // End of TDZ (for foo)
}
{% endhighlight %}

let 和 const 不能在同個 block 下重複宣告變數，但在不同 block 可以
{% highlight JavaScript %}

const me = {name : 'John', age : 20}

const me = {name : 'Chip', age : 40} // SyntaxError: 識別字 'obj' 已經被宣告

{
    const me = {name : 'Chip', age : 40} // 可以在 block 中重新定義 
}
{% endhighlight %}

let 和 const 在全域宣告時，不會在 windows 物件建立屬性
{% highlight JavaScript %}

var tmp = 1;
let tmp2 = 2;

console.log(window.tmp); // → 1
console.log(window.tmp2); // → undefined

{% endhighlight %}
