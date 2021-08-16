---
layout: post
title:  "MasterCard"
date:   2019-07-11 13:42:00 +0800
categories: Business
tags: MasterCard
---

DE 3 (Processing Code)
資料長度固定6，分成3個 subfields

系統沒有帶值28，所以不存在IRD=20, 21的情況

Process Code = 00 購貨 Purchase (Goods and Services)
Process Code = 20 退貨 Credit (Purchase Return)
Process Code = 30 預借現金 Cash Disbursement
Process Code = 19 Fee Collection (Credit to Transaction Originator)

系統沒有CAB = I001，所以不存在IRD=2A的情況

EC交易會帶ECI值(VISA)，UCAF為MC所有

05 : ECI 5 , UCAF 2
06 : ECI 6 , UCAF 1
07 : ECI 7 , UCAF 0 



