# 取得 FAQ 問答

### 作業目的

> 取得 FAQ 問答

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | GET                                          |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/QA                                 |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 回應

### Response 欄位

| 欄位名稱名稱 | 資料型別    | 長度 | 必須 | 說明         |
| ------------ | ----------- | ---- | ---- | ------------ |
| data         | Arrayobject | -    | Y    | 回傳全部類別 |

#### data 欄位

| 欄位名稱名稱 | 資料型別 | 長度 | 必須 | 說明     |
| ------------ | -------- | ---- | ---- | -------- |
| createDate   | string   | 8    | Y    | 建立時間 |
| typeNo       | string   | 40   | Y    | 類別代號 |
| typeName     | string   | 20   | Y    | 類別名稱 |
| faqNo        | string   | 40   | Y    | 項目代號 |
| quest        | string   | 60   | Y    | 問題     |
| ans          | string   | 1000 | Y    | 答案     |
| priority     | string   | 2    | Y    | 優先級   |

### Response 範例

```json
{
  "state": 200,
  "msg": "succese",
  "error": "",
  "data": [
    {
      "createDate": "20200720",
      "typeNo": "202007200003",
      "typeName": "其他問題",
      "faqNo": "2020072000030001",
      "faqQuest": "pan piano為什麼收看率這麼高",
      "faqAns": "「Pan Piano」同樣也是鋼琴YouTuber，一開始都是以日常穿著入鏡，從未露臉，不過她的好身材經常受到討論，Pan也開始在彈鋼琴時cosplay動漫角色，多套爆乳裝扮讓粉絲看得目不轉睛，追蹤人數直線上升，目前有65.7萬人訂閱頻道",
      "priority": "1"
    },
    {
      "createDate": "20200720",
      "typeNo": "202007200004",
      "typeName": "常見問題",
      "faqNo": "2020072000040002",
      "faqQuest": "永遠是深夜多好",
      "faqAns": "「這歌聲不得了！」今年六月，一名神秘創作者ACAね（讀音：AKANE）率領樂團「永遠是深夜有多好｡」以一首《咬住秒針》如閃耀的彗星般現身Youtube，無懈可擊的創作實力與驚人的嗓音，讓極品下流少女。主唱川谷繪音、超人氣Vocaloid 製作人Neru 都忍不住稱讚，並在網路上掀起熱烈討論，ACAね到底是誰? 影像不到二十天便突破百萬閱覽。首張專輯【正確的假裝起床】本週正式上架，六首精彩作品構築「永遠是深夜有多好｡」壓倒性的作品世界觀，超級新人降臨，請大家千萬不能錯過！",
      "priority": "1"
    }
  ]
}
```
