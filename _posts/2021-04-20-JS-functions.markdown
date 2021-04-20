
---
layout: post
title:  "JavaScript Functions"
date:   2021-04-20 10:03:00 +0800
categories: Programming
tags: JavaScripts

---

- value 的其中一種 type 為 function
- 檔 function 產生 value 時，因為在 JavaScript 中，有產生值(produces a value)的都稱為 expression
- 這表示 function calls 可以被當成 expression 使用
- JavaScript 中，scope 是由 function 或是 code block 建立 
- 為了方法參數建立的 binding 或是在方法內宣告的 binging 只能在該方法內被參考，此稱為 local bindings
- 每個 function 呼叫會建一個新的 binding，呼叫同個方法不同次都會是一個新的 instance
<br>  
<br>   

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

function foo() {
  // The function scope
  let count = 0;
  console.log(count); // logs 0
}

foo();
console.log(count); // 在此無法存取 count 屬於 foo() 方法建立的 scope

#### Lexical Scoping

每個 local scope 可以看見包含他的其他 local scopes，每個 scope 都可以看見 global scope

Lexical scoping means that the accessibility of variables is determined by the position of the variables inside the nested scopes.
語彙範疇的意思是變數的可存取性是由變數在巢狀範疇的位置所決定

Simpler, the lexical scoping means that inside the inner scope you can access variables of outer scopes.
簡單來說，在內層範疇中，程式可以存取外層範疇的變數
