---
layout: post
title:  "JavaScript Functions"
date:   2021-04-20 10:03:00 +0800
categories: Programming
tags: JavaScripts

---

JavaScript 有 6 種資料型別 (Data Type) 為原始值 (primitive values)，
- undefined
- Boolean
- Number
- String
- BigInt
- Symbol

JavaScript 有 2 種結構型別 (Structural Type)
- Object
- Function

當 function 產生 value 時，因為在 JavaScript 中，有產生值(produces a value)的都稱為 expression，這表示 function calls 可以被當成 expression 使用。每個 function 呼叫會建一個新的 binding，呼叫同個方法不同次都會是一個新的 instance
      

{% highlight JavaScript %}

let x = 10;
if (true) {
  let y = 20;
  var z = 30;
  console.log(x + y + z);
  // → 60
}

console.log(x + z); // → 40
// 在此無法存取 y，y 屬於 if block 建立的 scope

{% endhighlight %}

{% highlight JavaScript %}

function foo() {
  // The function scope
  let count = 0;
  console.log(count); // → 0
}

foo();
console.log(count); // 在此無法存取 count 屬於 foo() 方法建立的 scope
{% endhighlight %}
<br/>

### **Lexical Scoping**

每個 local scope 可以看見包含他的其他 local scopes，每個 scope 都可以看見 global scope

語彙範疇的意思是變數的可存取性是由變數在巢狀範疇的位置所決定
> Lexical scoping means that the accessibility of variables is determined by the position of the variables inside the nested scopes. 

簡單來說，在內層範疇中，程式可以存取外層範疇的變數
> Simpler, the lexical scoping means that inside the inner scope you can access variables of outer scopes.

{% highlight JavaScript %}
const myGlobal = 0;

// func()的 lexical scope 僅包含 global scope。在 func()中，可以存取 lexical scope 變數 myGlobal
function func() {
  const myVar = 1;
  console.log(myGlobal); // → "0"
    
  function innerOfFunc() {
    const myInnerVar = 2;
    console.log(myVar, myGlobal); // → "1 0"
    
    // innerOfInnerOfFunc() 的 lexical scope 包含 innerOfFunc()，func()和 global scope
    // 在 innerOfInnerOfFunc() 中，可以存取 lexical scope 變數 myInnerVar、myVar、myGlobal
    function innerOfInnerOfFunc() {
      console.log(myInnerVar, myVar, myGlobal); // → "2 1 0"
    }

    innerOfInnerOfFunc();
  }

  innerOfFunc();
}

func();
{% endhighlight %}
<br/>   

### **Function As Value**

{% highlight JavaScript %}
let test = function(para){
  console.log(para + " success");
}

let test2 = test; // 將 function value 存在一個新的 binding 

// Function Declaration
function test_Function(para1, para2){
  para2(50);
}

test_Function('0', test2); // 將 function value 當參數傳遞 
{% endhighlight %}

Function Declaration 回被移到 scope 的最上方，且可以被該 scope 的成員使用
<br/>

### **Arrow Functions**

一個參數的 Arrow Function 可以省略左側()
{% highlight JavaScript %}
const square1 = base => {  
  return base * base;
} 
{% endhighlight %}

Arrow Function 方法內容只有一行可以省略大括號{}
{% highlight JavaScript %}
const square2 = base =>  base * base;
{% endhighlight %}

多參數的 Arrow Function，要使用空的括號()
{% highlight JavaScript %}
const square3 = (base, multi) => {  
  return base * multi;
}
{% endhighlight %}

無參數的 Arrow Function，使用空的括號()
{% highlight JavaScript %}
const horn = () => {
  console.log("Toot");
}; 
{% endhighlight %}

<br/>   

### **Function 參數**

多給參數不會錯
{% highlight JavaScript %}
function square4(x) { return x * x; }
console.log(square4(4, true, "hedgehog")); // 
{% endhighlight %}

參數預設值
{% highlight JavaScript %}
function square5(x, y = 2) { return x * y; }
console.log(square5(4));  // 8
console.log(square5(4, 3)); // 12
{% endhighlight %}

<br/>   

### **Closure**

要使用 Closure，在一個方法中定義一個內部方法並回傳出來，內部方法可以存取外部方法 scope 中的變數，即便外部方法已經回傳
> To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to anot//her function. The inner function will have access to the variables in the outer function scope, even after the outer function has returned. 
<br><br/>
{% highlight JavaScript %}
function outerFunc() {
  let outerVar = 'I am outside!';

  function innerFunc() {
    console.log(outerVar); // => logs "I am outside!"
  }

  innerFunc();
}

outerFunc();
{% endhighlight %}
在 innerFunc() 的 scope 中, 變數 outerVar 可以從 lexical scope 中存取，innerFunc() 呼叫的時候是在 outerFunc() 的 scope 之內  
<br><br/>

{% highlight JavaScript %}
function outerFunc() {
  let outerVar = 'I am outside!';

  function innerFunc() {
    console.log(outerVar); // => logs "I am outside!"
  }

  return innerFunc;
}

const myInnerFunc = outerFunc();
myInnerFunc();
{% endhighlight %}

當 innerFunc() 呼叫的時候不在 outerFunc() 的 scope 之中，innerFunc() 仍舊可以從 lexical scope 中存取 outerVar 變數，即便是在 lexical scope 的外面，換句話說 innerFunc() closes over(capture, remember) 他的 lexical scope 中的變數 outVar
<br><br/>

Closure 就是一個方法，即使是在他的 lexical scope 之外執行，仍舊可以存取他的 lexical scope
> The closure is a function that accesses its lexical scope even executed outside of its lexical scope.

簡單來說，closure 記得定義當下的變數，不論何時呼叫

為什麼需要 Closure ? 
主要是為了資料隱私性，無法從 scope 之外存取資料，除非透過該物件的特權方法
> When you use closures for data privacy, the enclosed variables are only in scope within the containing (outer) function. You can’t get at the data from an outside scope except through the object’s privileged methods.

