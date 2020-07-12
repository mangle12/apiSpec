# template 問題一覽


## 1. 真人滿意的回收
![](https://i.imgur.com/ftVlZcu.png)

真人這邊也有紀錄滿意度分數
似乎也有報表

kibana這邊也需要我們將分數紀錄進去

還請決議使用哪一種。

## 2. 轉真人方式不對

![](https://i.imgur.com/tbjN7td.png)

:::info
藍色線條是AI部門給予的轉真人方式
:::

:::warning
紅色線條是真正的轉真人方式以及真人回收訊息的機制，藍色線條已無法轉真人及接收訊息。
轉真人的response 也不是改變一個狀態即可，需透過call api的方式來呼叫

可參考 [轉真人](./EvqnqJnjTmWzpaO5xTaqoQ)
可參考 [知識隨行](./7YrOfqnuTXabI4KzQ_4nog) 
:::



## 3. kibana的問題
四處在設計紀錄LOG是透過getway的後台 將資料回收之後可立即呈現
kibana在看問題的話須等到ES拋轉後方可得知，時間上略有落差

## 4. 模板更新的紀錄方式
![](https://i.imgur.com/KqjASxQ.png)


> 建議將程式碼包起來，我們在更修的時候可以方便的知道你們這次主要更新了哪些部分
```
// 若總機聽不懂，服務台聽不懂，但有建議 FAQ 或建議的 NLU 意圖
// 20200208 add by 子彥 ↓
if (!faqDecided && !nluReturns && ((msg.isSuggestedFAQ && !!msg.FAQ) || (msg.isSuggestedNLU && !!msg.suggestedNLUIntent))) {
    return MsgUtils.output(msg, 9, numOfOuts);
}
// 20200208 add by 子彥 ↑
```
> 除了可以用日 應該也可以這樣寫
> 如此一來我們可以很清楚的知道你們改了些什麼，在更修上會比較方便，後續當然是可以移除的沒問題，否則目前幾乎是一行一行看，且與現行落差過多，幾乎是得理解過後方可更修

```
// 20200208 add by FlowTemplate_v2.0.5↓
if (!faqDecided && !nluReturns && ((msg.isSuggestedFAQ && !!msg.FAQ) || (msg.isSuggestedNLU && !!msg.suggestedNLUIntent))) {
    return MsgUtils.output(msg, 9, numOfOuts);
}
// 20200208 add by FlowTemplate_v2.0.5 ↑
```



