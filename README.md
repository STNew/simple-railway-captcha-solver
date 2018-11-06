本網站引用：[simple-railway-captcha-solver]( https://github.com/JasonLiTW/simple-railway-captcha-solver ) 進行延伸

#### 溫馨提醒  鐵路法第65條中提到：「...以不正方法將虛偽資料或不正指令輸入電腦或其相關設備而購買車票、取得訂票或取票憑證者，處五年以下有期徒刑或科或併科新臺幣三百萬元以下罰金。」，我想使用程式辨識驗證碼來自動訂票，應該也在其中"不正方法"的範疇中。

# Imporve
前一個作者使用的方法是分別判斷驗證碼為5碼還是6碼，再用相對應的去分析裡面數字。
而此版本則是可以直接輸出驗證圖的輸出裡面之**所有數字與英文**

# Method
在原作者 [JasonLiTW](https://github.com/JasonLiTW)model下，之底層加入雙向GRU神經元。


# Imporve step
- 驗證碼種類，增加空白 (或以* 代替) 
- 原model下，加一層Dense與雙向GRU
- 透過不停製造新的 Train data，來提升準確率
- 分段load data，避免RAM無法一次load完所有data，故改成或者直接減少產生次數並增加製造新data的次數

# Conclusion
訓練到後期
測試資料準確率：
digit1_acc: 0.9998 
digit2_acc: 0.9960 
digit3_acc: 0.9742 
digit4_acc: 0.9932 
digit5_acc: 0.9976 
digit6_acc: 0.9992

驗證資料準確率：
val_digit1_acc: 0.9952 
val_digit2_acc: 0.9896 
val_digit3_acc: 0.8706
val_digit4_acc: 0.9100 
val_digit5_acc: 0.9736 
val_digit6_acc: 0.9916

目前未以官方資料進行測試


# Remarks
此是我第一次上傳code，如有問題(冒犯)歡迎提出。
