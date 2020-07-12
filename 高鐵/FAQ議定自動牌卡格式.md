# FAQ議定自動牌卡格式

## 針對 Type 13 組合卡片


欄位名稱 | 資料型別|  說明
--------- | ------- |-----
type | int | 1(文字)、13(牌卡)| 
data | ao | 按鈕 
content | ao | 連續內文
title| string |小標題
image | string | 圖片 - 有http絕對路徑 無http相對路徑(img01.png =>抓相對路徑 https://i.imgur.com/iFBMjF4.jpg 絕對路徑) 

### data 欄位
欄位名稱 | 資料型別|  說明
--------- | ------- |-----
title | string | 按鈕顯示名稱
payload | string | FLOW收到的字串
url | string | 超連結
:::info
有url按鈕就是超連結的版本
:::

### content 欄位
欄位名稱 | 資料型別|  說明
--------- | ------- |-----
mkey | string | 單身名稱
mvalue | string | 單身資料



```json
[
   {
      "type":1,
      "text":"有關「檔案清理」業務，小助手為您推薦幾個熱門問題，或者您也可以直接詢問單一問題，我會竭誠為您解答！"
   },
   {
      "type":16,
      "title":"以下是大家都在問的「檔案清理」問題：",
      "image":"https://i.imgur.com/iFBMjF4.jpg",
      "data":[
         {
            "title":"預覽銷毀目錄時，出現090集合中所需成員不存在。",
            "payload":"預覽銷毀目錄時，出現090集合中所需成員不存在。"
         },
         {
            "title":"預覽銷毀目錄時，出現090集合中所需成員不存在。",
            "payload":"預覽銷毀目錄時，出現090集合中所需成員不存在。"
         }
      ],
      "content":[
         {
            "mkey":"單身名稱",
            "mvalue":"單身資料"
         },
         {
            "mkey":"單身名稱1",
            "mvalue":"單身資料2"
         }
      ]
   }
]
```

