![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30

Starter Files + Completed solutions for the JavaScript 30 Day Challenge.

Grab the course at [https://JavaScript30.com](https://JavaScript30.com)

## 指針css設定

* 指針由圓中心旋轉 
- transform: rotate(90deg)
- transform-origin: 50%（預設:圖形中央為中心點旋轉）- where to do the rotation
	(set 100% - 旋轉點在最右邊)
- transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1) - 指針顫動效果

## js
* const now = new Date() 
JavaScript 沒有日期資料型態，但是它有提供 Date() 物件，使用內件的日期物件與方法、可以取得與操作日期時間。日期物件有多種的方法來設定及取得。使用時有可能會因為瀏覽器或作業系統之不同，而顯示出不同的結果。
因為它不是瀏覽器必然存在的物件，所以用 new 來產生它。
不使用 new 不會產生物件實體；參數會被忽略一律傳回目前時間的字串。

* 取得秒，分，時
- const now.getSeconds()
- const now.getMinutes()
- const now.getHours()

* setInterval(func, delay[, param1, param2, ...])
固定延遲了某段時間之後，才去執行對應的程式碼，然後「不斷循環」
參考：[https://kuro.tw/posts/2019/02/23/談談-JavaScript-的-setTimeout-與-setInterval](https://kuro.tw/posts/2019/02/23/談談-JavaScript-的-setTimeout-與-setInterval)


* 補充：DateObj.setDate(dayValue)
dayValue：傳入值，是一個1~31的整數，若是傳入的值超出當月份的正常範圍，setDate()方法也會依據超出的數值進行計算。
	- setDate(0)會讓日期變成前一個月的最後一天，
	- setDate(-1)會讓日期變成前一個月的倒數第二天。
	- 若當月有31天，那setDate(32)會讓日期變成下個月的第一天。




