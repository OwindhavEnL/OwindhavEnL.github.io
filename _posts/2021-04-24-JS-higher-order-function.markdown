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

### **filter()**

<code>filter()</code> 是建立新陣列回傳，而不是從現有陣列中刪除元素

{% highlight JavaScript %}
function filter(array, test) {
  let passed = [];
  for (let element of array) {
    if (test(element)) {
      passed.push(element);
    }
  }
  return passed;
}
{% endhighlight %}

{% highlight JavaScript %}
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(x => x.length > 6);

console.log(result);
// → ["exuberant", "destruction", "present"]
{% endhighlight %}
<br/>

### **map()**

<code>map()</code> 套用 function 到陣列的所有元素，並將轉換後的結果回傳，回傳的陣列長度不變

{% highlight JavaScript %}
function map(array, transform) {
  let mapped = [];
  for (let element of array) {
    mapped.push(transform(element));
  }
  return mapped;
}
{% endhighlight %}

{% highlight JavaScript %}
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1); // → [2, 8, 18, 32]
{% endhighlight %}
<br/>

### **reduce()**

reduce() 方法通過重複從陣列中取一個元素，與當前值組合加總，最後回傳一個數值。

{% highlight JavaScript %}
function reduce(array, combine, start) {
  let current = start;
  for (let element of array) {
    current = combine(current, element);
  }
  return current;
}

console.log(reduce([1, 2, 3, 4], (a, b) => a + b, 0));
// → 10
{% endhighlight %}

標準的陣列方法 reduce()。如果您的陣列包含至少一個元素，則可以不使用start參數

{% highlight JavaScript %}
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// → 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// → 15
{% endhighlight %}

Higher-order functions 真正的用途是在組合多種運算

### **charCodeAt() && codePointAt()**
<br/>

{% highlight JavaScript %}
let horseShoe = "測試";

console.log(horseShoe.length);
// → 4
console.log(horseShoe[0]);

console.log(horseShoe.charCodeAt(0));
// → 取得 UTF-16 Code Unit
console.log(horseShoe.codePointAt(0));
// → 取得 full Unicode character
{% endhighlight %}
