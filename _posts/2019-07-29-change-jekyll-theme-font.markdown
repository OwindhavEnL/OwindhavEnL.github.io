---
layout: post
title:  "Change Jekyll Theme Font"
date:   2019-07-29 14:22:00 +0800
categories: Jekyll
tags: Jekyll

---

## Jekyll 參考資料

https://hermens.com.au/2016/10/14/Getting-started-with-Jekyll-Part-5/  

## GitHub 圖片無法顯示的問題
在 localhost 上圖片是可以顯示，但放到 GitHub 上圖片都無法顯示，試了三天之後，發現是圖片的副檔名為 PNG，但在文章裡設定為 png，不知為何 local 端讀的到圖，將文章的圖片改為 PNG 後就解決這個問題了。


## 如何修改 Jekyll 字型


> Create a new instance at site source.  
>
>> * Create a new file at <your-site>/assets/css/style.scss    
>> * Add the frontmatter dashes, and  
>> * Add @import "minima";
>> * Add your custom CSS.  
>  
> Download the file from this repo  
>
>>  * Create a new file at <your-site>/assets/css/style.scss
>>  * Copy the contents at assets/css/style.scss onto the css/style.scss you just created, and edit away!  
> 
> Copy directly from minima gem  
>
>>  * Go to your local minima gem installation directory ( run bundle show minima to get the path to it ).  
>>  * Copy the assets/ folder from there into the root of <your-site>    
>>  * Change whatever values you want, inside <your-site>/assets/css/style.scss  

參考來源
https://github.com/jekyll/minima/blob/master/README.md

