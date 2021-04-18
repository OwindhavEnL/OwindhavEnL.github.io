---
layout: post
title:  "JavaScript Program Structures"
date:   2021-04-18 08:30:00 +0800
categories: Programming
tags: JavaScripts

---



####  運算式 Expression

- 產生 value 的程式片段稱為 expression 
- 每個逐字寫的 value 也是一個 expression，如 22 或是 "tom"
- 最簡單的 statement 為 expression 加上分號，如 1; !false;
<br>  
   
#### Binding

> To catch and hold values, JavaScript provides a thing called a binding, or variable.  

為了捕獲和保留值，JavaScript提供了一種稱為綁定或變量的東西。
<br>  
   
#### let
{% highlight JavaScript %}
let one = 1, two = 2;
{% endhighlight %}
- let 可以同時定義多個變數
- 只作用在當前區塊的變數
- let 定義變數存在於 block statement 的 scope
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
- var 用於宣告全域變數，或是
<br>   

