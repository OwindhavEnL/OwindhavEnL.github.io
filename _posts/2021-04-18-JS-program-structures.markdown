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
### **Binding**

- To catch and hold values, JavaScript provides a thing called a binding, or variable.
- 為了捕獲和保留值，JavaScript提供了一種稱為綁定或變量的東西。
<br/>

### **var**
- var 是 function scope 的。只要在 function 中使用 var 宣告變數，該變數就僅存在於 function 中。
- 如果變數是在 function 外部建立的的，則它將存在於 outer scope 中。

{% highlight JavaScript %}
var hours = 1;

function Sleep()
{		
  {
    var hours = 2;
  }
  console.log(hours); // logs 2
}

Sleep();
console.log(hours); // logs 1

{% endhighlight %}
<br/> 

### **let vs const**

{% highlight JavaScript %}
let x = 1;
{
  let x = 2; // x = 2 被限制在該 block 的 scope 中
}
console.log(x); // → 1 

{% endhighlight %}
<br/>

{% highlight JavaScript %}
let one = 1, two = 2;
{% endhighlight %}
- let 可以同時定義多個變數
- 只作用在當前區塊的變數
- 不同於 var，let 和 const 沒有 Hoisting
- 不同於 var，let 和 const 不能在同個 block 下重複宣告變數，但在不同 block 可以
- const 不能被重新 assign 值，但 const 物件的內容可以修改


{% highlight JavaScript %}

const me = {name : 'John', age : 20}

const me = {name : 'Chip', age : 40}
// Uncaught SyntaxError: Identifier 'obj' has already been declared

{
    const me = {name : 'Chip', age : 40} // 可以在 block 中重新定義 const/let
}

me = {name : 'Mike', age : 10} 
// Uncaught TypeError: Assignment to constant variable.

me.name = 'Tom';
console.log(me.name); // → 'Tom' const 物件的內容可以修改 

var x = 1;
let y = 1;

if (true) {
  var x = 2;
  let y = 2;
}

console.log(x); // → 2 
console.log(y); // → 1

{% endhighlight %}

<br/>   

