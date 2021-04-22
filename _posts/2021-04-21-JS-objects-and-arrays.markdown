---
layout: post
title:  "Objects & Array"
date:   2021-04-21 1:03:00 +0800
categories: Programming
tags: JavaScripts

---

### **Property**

- 在 JavaScript 中存取屬性 (property) 有兩種方式，假設物件為 value，需要存取屬性 x，存取方式為 value.x 跟 value[x]，value[x]會試著評估 expression x 並將結果轉為字串作為屬性名稱
- 屬性名稱為字串，所以可以是任何字串，但僅能適用如正常的 binding 名稱，所以如果要存取屬性名稱像是 2 或是 John Doe， 則只能用 value[2] 或是 value ["John Doe"] 存取屬性
- 陣列的元素是儲存成陣列的屬性，使用數字做為屬性名稱，因數字無法以.存取，所以用[]存取
- 包含方法 (function) 的屬性通常稱為該 value 的 methods，如同 toUpperCase 是 string 的 method
- 物件型別的值為任意屬性的集合

<br><br>

### **Object**

使用大括號建立物件，由逗號隔開屬性
{% highlight JavaScript %}
let day1 = {
    squirrel: false,
    events: ["work", "touched tree", "pizza", "running"]
  };
{% endhighlight %}
<br>
屬性名稱非有效的 binding name 時須加上括號
{% highlight JavaScript %}
let descriptions = {
    work: "Went to work",
    "touched tree": "Touched a tree"
  };
{% endhighlight %}
<br>
物件的 delete 方法可以移除屬性
{% highlight JavaScript %}
  delete anObject.left; // 移除屬性
{% endhighlight %}
<br>
檢查是否有屬性
{% highlight JavaScript %}
let father = {name: 'Tom'};
let years = 18 // 取得 immutable 18 的一個參考
let son = {dad: father, age: years};

father.name =  'Chris'
years = 9 // assign a new reference to the immutable 9
console.log('son.dad' + son.dad); // {name : 'Chris'} 因為屬性的 value 值已經變更了
console.log(son.age); // 18，因為 number 為 immutable

console.log("dad" in son); // 檢查是否有屬性
console.log("age" in son); // → true
{% endhighlight %}
<br>
取得物件的屬性陣列可以用
{% highlight JavaScript %}
console.log(Object.keys({x: 0, y: 0})); // → ["x", "y"]
{% endhighlight %}
<br>
複製所有屬性至另一個物件
{% highlight JavaScript %}
let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
{% endhighlight %}
<br><br/>

 ### **Immutable**
 
數字、字串、布林值為不可改變的
> numbers, strings, and Booleans, are all immutable
數字本身為不可改變的，但變數儲存數字的參考是可以改變的
> The numbers themselves are immutable. The references to them that are stored in the variable are not.
<br>

{% highlight JavaScript %}
let object1 = {value: 10};
let object2 = object1;
let object3 = {value: 10};

console.log(object1 == object2);// → true
console.log(object1 == object3);// → false

object1.value = 15;
console.log(object2.value);// → 15
console.log(object3.value);// → 10
{% endhighlight %}
<br>

push 到陣列的物件不像一般的物件有冒號 events : events，傳進來的 events 就變成屬性名稱，value 就是傳進來的 event
{% highlight JavaScript %}
let journal = [];

function addEntry(events, squirrel) {
  journal.push({events, squirrel});
}

addEntry(["work", "touched tree", "pizza", "running",
          "television"], false);
		  
console.log(journal);
// events: (5) ["work", "touched tree", "pizza", "running", "television"]
// squirrel: false
{% endhighlight %}
<br>

loop 陣列
{% highlight JavaScript %}
for(let entry of journal)
{
	console.log(`${entry.events.length} events.`);
}
{% endhighlight %}
<br/>

從陣列起始位置移除元素
{% highlight JavaScript %}
journal[0].events.shift();
console.log(journal[0].events); //["touched tree", "pizza", "running", "television"]
{% endhighlight %}
<br/>

從陣列起始位置增加元素
{% highlight JavaScript %}
journal[0].events.unshift('trader');
console.log(journal[0].events); //["touched tree", "pizza", "running", "television"]
{% endhighlight %}
<br/>

indexOf & lastIndexOf
{% highlight JavaScript %}
console.log([1, 2, 3, 2, 1].indexOf(3)); // → 2
console.log([1, 2, 3, 2, 1].lastIndexOf(1)); // → 4 
{% endhighlight %}
<br/>

另一個基本的陣列方法是 slice()，它採用開始索引和結束索引，並返回僅包含元素之間的陣列。含起始索引，不含結束索引。
{% highlight JavaScript %}
console.log([0, 1, 2, 3, 4].slice(2, 4)); // → [2, 3]
console.log([0, 1, 2, 3, 4].slice(2)); // → [2, 3, 4]
console.log([0, 1, 2, 3, 4].slice()); // → [0, 1 2, 3, 4]
{% endhighlight %}
<br/>

字串也有 slice 和 indexOf
{% highlight JavaScript %}
console.log("coconutss".slice(4, 7)); // → nut
console.log("coconut".indexOf("con")); // 可搜尋
{% endhighlight %}
<br/>

trim() 方法從字符串的開頭和結尾刪除空格（空格，換行符號，tab）
{% highlight JavaScript %}
console.log(String(6).padStart(1, "0")); // → 006
{% endhighlight %}



