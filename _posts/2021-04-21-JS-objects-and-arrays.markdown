---
layout: post
title:  "Objects & Array"
date:   2021-04-21 1:03:00 +0800
categories: Programming
tags: JavaScripts

---
### **Object**

使用大括號建立物件，由逗號隔開屬性
{% highlight JavaScript %}
let day1 = {
    squirrel: false,
    events: ["work", "touched tree", "pizza", "running"]
  };
{% endhighlight %}
<br>

### **Property**

- 在 JavaScript 中存取屬性 (property) 有兩種方式，假設物件為 <code>value</code>，需要存取屬性 x，存取方式為 value.x 跟 value[x]，value[x]會試著評估 expression x 並將結果轉為字串作為屬性名稱
- 屬性名稱為字串，所以可以是任何字串，但僅能適用如正常的 binding 名稱，所以如果要存取屬性名稱像是 2 或是 John Doe， 則只能用 value[2] 或是 value ["John Doe"] 存取屬性
- 陣列的元素是儲存成陣列的屬性，使用數字做為屬性名稱，因數字無法以.存取，所以用 [ ] 存取
- 包含方法 (function) 的屬性通常稱為該 value 的 methods，如同 toUpperCase 是 string 的 method
- 物件型別的值為任意屬性的集合
<br/>

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
<br/>

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

### **push**

將物件加入陣列的末端

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

### **陣列相關方法**
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
console.log(journal[0].events); 
//["touched tree", "pizza", "running", "television"]
{% endhighlight %}
<br/>

從陣列起始位置增加元素
{% highlight JavaScript %}
journal[0].events.unshift('trader');
console.log(journal[0].events); 
//["touched tree", "pizza", "running", "television"]
{% endhighlight %}
<br/>

indexOf
{% highlight JavaScript %}
console.log([1, 2, 3, 2, 1].indexOf(3)); // → 2
{% endhighlight %}
<br/>

lastIndexOf
{% highlight JavaScript %}
console.log([1, 2, 3, 2, 1].lastIndexOf(1)); // → 4 
{% endhighlight %}
<br/>

slice()，它採用開始索引和結束索引，並返回僅包含元素之間的陣列。含起始索引，不含結束索引。
{% highlight JavaScript %}
console.log([0, 1, 2, 3, 4].slice(2, 4)); // → [2, 3]
console.log([0, 1, 2, 3, 4].slice(2)); // → [2, 3, 4]
console.log([0, 1, 2, 3, 4].slice()); // → [0, 1 2, 3, 4]
{% endhighlight %}
<br/>

### **字串相關方法**
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
<br/>

split
{% highlight JavaScript %}
let sentence = "Secretarybirds specialize in stomping";
let words = sentence.split(" ");

console.log(words); 
// → ["Secretarybirds", "specialize", "in", "stomping"]

console.log(words.join(". ")); 
// → Secretarybirds. specialize. in. stomping

console.log("LA".repeat(3));// → LALALA

{% endhighlight %}
<br/>

### **Rest 參數**
rest 參數會被組合成一個陣列。如果前面還有其他參數，則它們的值不屬於該陣列。

{% highlight JavaScript %}
function max(tmp, ...numbers) {
  console.log(numbers);
  let result = -Infinity;
  for (let number of numbers) {
    if (number > result) result = number;
  }
  return result;
}
console.log(max(4, 1, 9, -2));// → 9

let numbers = [5, 1, 7];
console.log(max(...numbers)); // → 7
{% endhighlight %}

可以使用類似的...符號來呼叫有陣列參數的方法。這會將陣列展開，將其元素作為單獨的參數傳遞來呼叫方法。
{% highlight JavaScript %}
function max_t(t1, t2) {
    
  return Math.max(t1,t2);
}

console.log(max_t(...numbers));
{% endhighlight %}
<br/>

### **Destructuring Assignment 解構指派**

Destructuring Assignment 語法是一個 JavaScript 表達式，可以將陣列中的值或物件的屬性解構為不同的變數。
{% highlight JavaScript %}
let a, b, rest;
[a, b] = [10, 20];

console.log(a); // → 10

console.log(b); // → 20

// 搭配 Rest 參數
[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest); // → [30,40,50]
{% endhighlight %}
<br/>

{% highlight JavaScript %}
const x = [1, 2, 3, 4, 5];
const [y, z] = x;
console.log(y); // → 1
console.log(z); // →  2
{% endhighlight %}
<br/>

{% highlight JavaScript %}
const foo = ['one', 'two', 'three'];

const [red, yellow, green] = foo;
console.log(red); // → "one"
console.log(yellow); // → "two"
console.log(green); // → "three"
{% endhighlight %}
<br/>

預設值
{% highlight JavaScript %}
let a, b;

[a=5, b=7] = [1];
console.log(a); // → 1
console.log(b); // → 7
{% endhighlight %}
<br/>

解構方法回傳的陣列
{% highlight JavaScript %}
function f() {
  return [1, 2];
}

let a, b;
[a, b] = f();
console.log(a); // → 1
console.log(b); // → 2
{% endhighlight %}
<br/>

忽略部分回傳值
{% highlight JavaScript %}
function f() {
  return [1, 2, 3];
}

const [a, , b] = f();
console.log(a); // → 1
console.log(b); // → 3

const [c] = f();
console.log(c); // → 1
{% endhighlight %}
<br/>

解構陣列時，可以將剩餘的元素使用 rest 模式打包成一個變數(需置於最右側)
{% highlight JavaScript %}
const [a, ...b] = [1, 2, 3];
console.log(a); // → 1
console.log(b); // → [2, 3]
{% endhighlight %}
<br/>

### **Destructuring Objects 解構物件**
{% highlight JavaScript %}
const user = {
    id: 42,
    is_verified: true
};

// 解構中的屬性名稱必須相同於原本物件的屬性名稱
const {id, is_verified} = user;

console.log(id); // → 42 
console.log(is_verified); // → true
{% endhighlight %}
<br/>

值派時無宣告
{% highlight JavaScript %}
let a, b;

({a, b} = {a: 1, b: 2});
{% endhighlight %}
<br/>

值派新變數名稱
{% highlight JavaScript %}
const o = {p: 42, q: true};
const {p: foo, q: bar} = o;

console.log(foo); // → 42
console.log(bar); // → true

{% endhighlight %}
<br/>

值派變數預設值
{% highlight JavaScript %}
const {a = 10, b = 5} = {a: 3};

console.log(a); // → 3
console.log(b); // → 5
{% endhighlight %}
<br/>

值派新變數名稱並給預設值
{% highlight JavaScript %}
const {a: aa = 10, b: bb = 5} = {a: 3};

console.log(aa); // → 3
console.log(bb);
{% endhighlight %}
<br/>

解構物件屬性傳至方法參數
{% highlight JavaScript %}
const user = {
  id: 42,
  displayName: 'jdoe',
  fullName: {
    firstName: 'John',
    lastName: 'Doe'
  }
};

function userId({id}) {
  return id;
}

function whois({displayName, fullName: {firstName: name}}) {
  return `${displayName} is ${name}`;
}

console.log(userId(user)); // → 42
console.log(whois(user));  // → "jdoe is John"
{% endhighlight %}
<br/>

{% highlight JavaScript %}

{% endhighlight %}
<br/>

{% highlight JavaScript %}

{% endhighlight %}
<br/>

{% highlight JavaScript %}

{% endhighlight %}
<br/>

{% highlight JavaScript %}

{% endhighlight %}
<br/>
