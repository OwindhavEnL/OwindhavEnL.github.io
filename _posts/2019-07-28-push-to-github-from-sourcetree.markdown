---
layout: post
title:  "透過 SourceTree 使用 SSH 連接 GitHub"
date:   2019-07-27 00:38:20 +0800
categories: Git,
---
使用 SSH 連接需要一組公鑰及私鑰，我們可以使用 PuTTY Key Generator 來產生，安裝 SourceTree 時會一併安裝。
![image]({{site.baseurl}}/assets/img/putty-key-generator.PNG)  
    
    
  
點選 [Save public key] 儲存公鑰。  

點選 [Save private key] 儲存私鑰。  

![image]({{site.baseurl}}/assets/img/putty-key-generator-key generated.PNG)  
  
  
  
新增 SSH 金鑰。
![image]({{site.baseurl}}/assets/img/Github.PNG)  

![image]({{site.baseurl}}/assets/img/Github-2.PNG)  
  
  
Remote 設定要用 git@ ...
![image]({{site.baseurl}}/assets/img/repo-settings.PNG)
