---
title: ML&F
tags: teaching
description: View the slide with "Slide Mode".
push from hackmd(https://hackmd.io/@x2LAQ7HQR8i8O7THsvn_DA/HkIgt50mY)

---

# ML and FinTech: Project by 李柏毅

---

## Motivations (Talk 1)

---
#### Keywords: ML/DL, Financial Market, Automated Trading
希望能透過ML/DL(GAN、Q Learning)技術來預測股市
並同時做到自動交易的動作

---

## EDA (Talk 2) 
 
### (1)Data Link:[台股加權指數](https://finance.yahoo.com/quote/%5ETWII/history?p=%5ETWII)

### (2)Variable Descreptions
This regression used the following variables as explanatory variables:
1. X1:Date 時間
2. X2:Open 開盤
3. X3:High 最高
4. X4:Low  最低
5. X5:Volume  成交量
6. X6:Close  收盤
7. X7:label  若當天上漲則為1，反之則為0

### (3)EDA Result

#### data.shape = (1219, 7)
無殘缺值
![](https://i.imgur.com/LiSLuBy.png)

時間間距:
2016/10/25 - 2021/10/22(daily)

前五天資訊:
![](https://i.imgur.com/QP9NFiS.png)

各欄位的資料分析:
![](https://i.imgur.com/A9xisOE.png)

各欄位間的關係圖:
![](https://i.imgur.com/ijMQTqp.png)

熱力圖(以各欄位間的相關性為依據):
![](https://i.imgur.com/DWxtJ3t.png)


## Problem formulation (Talk 3)  

#### 使用Multiple Linear Regression 模型當benchmark預測股市漲跌
1. 前處理：將日期作為索引，並把Open High Low Close Volume 標準化至（0,1）間
2. 訓練與測試分為3:1
3. score:0.38
#### 使用LSTM 模型預測股市漲跌

1. 使用原因：LSTM適用時間序列(長序列），記住需要記憶的，並忘記不重要的
3. 操作方式：
    1. 前處理：將日期作為索引，並把Open High Low Close Volume 標準化至（0,1）間
    2. 以9天為一個window，並預測第10天是漲還是跌(有去調整window大小，大約在0.48-0.56間震盪)
    3. 訓練與測試分為3:1
    4. dropout = 20%
4. 結果
    訓練成績：0.57
    測試成績：0.47



## Analysis (Talk 4)
#### In-sample results
|Measures |LSTM|
|---|----|
| Accuracy |0.57|
| Precision|0.57|
| Recall | 0.57|
|F1-score| 0.46|


#### Out-of-sample results
|Measures |LSTM|
|---|---|
| Accuracy |0.47|
| Precision|0.47|
| Recall |0.47|
|F1-score|0.36|

##### 備註
1. Accuracy: $\dfrac{TP + TN}{TN + FP + FN + TP}$
2. Precision: $\dfrac{TP }{TP + FP}$
3. Recall: $\dfrac{TP }{TP + FN}$
4. F1-score: $\dfrac{2PR}{P + R}$





---

