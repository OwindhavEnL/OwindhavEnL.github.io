---
layout: post
title:  "Objects & Array"
date:   2021-04-21 1:03:00 +0800
categories: Programming
tags: JavaScripts

---

### **Property**

- 在 JavaScript 中存取屬性(property)有兩種方式，value.x跟value[x]，value[x]會試著評估 expression x 並將結果轉為字串作為屬性名稱
- 屬性名稱為字串，所以可以是任何字串，但.僅能適用如正常的 binding 名稱，所以如果要存取屬性名稱像是 2 或是 John Doe， 則只能用 value[2] 或是 value ["John Doe"]
- 陣列的元素是儲存成陣列的屬性，使用數字做為屬性名稱，因數字無法以.存取，所以用[]存取
- 包含方法 (function) 的屬性通常稱為該 value 的 methods，如同 "toUpperCase 是 string 的 method"
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

屬性名稱非有效的 binding name 時須加上括號
{% highlight JavaScript %}
let descriptions = {
    work: "Went to work",
    "touched tree": "Touched a tree"
  };
{% endhighlight %}

物件的 delete 方法可以移除屬性
{% highlight JavaScript %}
  delete anObject.left; // 移除屬性
{% endhighlight %}


 
