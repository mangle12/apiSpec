# AI FLOW 需調整部分
###### tags:`工作用`


## 改善資料池的部分

下圖所示是開啟DB連線取得共用資訊的部分
![](https://i.imgur.com/t5PyFCv.png)

一直以來沒有說明的是mongoDB的承載量，起先我們理解的東西是systalk的節點下資料就是共用的，是以一個session作為基準點來去讀出寫入

後面再觀察mongodb存檔的邏輯來看，每一次都將這一票的東西寫入，這個session在對話上十組對話他就會產生十組這樣完全不必要的資訊。

請重點高量 增加新的表 來做共用資料池 而不是一再使用nodemessage 來記錄資料，mongodb的增長速度是幾乎用**爆肥**來形容...
![](https://i.imgur.com/0XDbLeu.png)

![](https://i.imgur.com/OzFQWRf.png)
5124862323.0 單位 bytes
512MB?! 我們才幾個人一天能做幾筆?...
這還是我曾經刪除過..沒記錯應該是三月初，並且我有稍微瘦身過..FLOW處存的資料

更不要說ES拉過去也無需要這些資料啊?


## 移除不必要的單元 或是元件化於底層像是 

主要是希望能夠不要是封裝起來的底層可以直接使用而不是每次都需要
msg.xxx = function xxx {
  ???每次執行都來這要一次???
}

![](https://i.imgur.com/Wuoupdx.png)
只有這些會用到其他都沒再用。因為其實seconde也有這個覺得很沒必要

## 轉真人

![](https://i.imgur.com/SFezkUV.png)

以下節點都是轉真人會用到的

轉真人主要的流程是

1. 進線格式
2. 知識隨行
3. 斷線訊號
4. getsession、setsession 也會有用但我不太明白用途
5. 跟發送滿意度的回饋
6. 進線前二次詢問
這些不應該考慮太多可滿足最低需求，並留下擴充模式即可。擴充模式盡量不影響原先定義的架構


## 初始化設定

![](https://i.imgur.com/2YzVUOx.png)

由於上版模式的定義，真正放置給上版人員調整的參數應統一集中於此


## 流程結束的最後處理
![](https://i.imgur.com/CCAp4Wl.png)
1. 由於腳本的設計方式，建議直接將全部的流程fallback轉接回firstbot統一處理
2. 跟second Bot轉真人 是直接透過變數回傳
3. restart 也是 就是重啟狀態初始值得概念
4. 需考慮過如果是 firstbot就被重啟了 但是secondbot 沒初始化狀態導致下次session相同會有異常的問題(賴、FB、AOG 再APP不重啟時session暫時都是一致的) 因此fitstbot 收到 結束需一併刪除到second 
:::success
這邊寫得有點我自己也看不太明白 ， 在電話call一下
:::