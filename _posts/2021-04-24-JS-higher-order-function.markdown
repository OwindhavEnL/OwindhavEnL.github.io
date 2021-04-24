---
layout: post
title:  "Higher Order Function"
date:   2021-04-24 10:41:00 +0800
categories: Programming
tags: JavaScripts

---
### **Higher Order Function**

通過將其他函數作為參數或通過將其回傳，稱為高階函數。

{% highlight JavaScript %}

function repeat(n, action) {
  for (let i = 0; i < n; i++) {
    action(i);
  }
}

let labels = [];
repeat(5, i => {
  labels.push(`Unit ${i + 1}`);
});
console.log(labels);

// 單行不用大括號
repeat(5, i => labels.push(`Unit ${i + 1}`));
console.log(labels);

{% endhighlight %}
<br>

### ****
