# FAQ 問答建立作業

### 作業目的

> FAQ 問答建立作業

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | POST                                         |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/QA                                 |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 請求

### Request 欄位

| 欄位名稱 | 資料型別 | 長度 | 必須 | 說明              |
| -------- | -------- | ---- | ---- | ----------------- |
| typeNo   | string   | 40   | Y    | form.FAQ 分類代號 |
| quest    | string   | 60   | Y    | form.輸入的問題   |
| ans      | string   | 1000 | O    | form.輸入的答案   |
| priority | string   | 2    | Y    | form.優先級       |

### Request 範例

```json
{
  "typeNo": "202007220003",
  "quest": "pan piano 是誰",
  "ans": "「Pan Piano」同樣也是鋼琴YouTuber，一開始都是以日常穿著入鏡，從未露臉，不過她的好身材經常受到討論，Pan也開始在彈鋼琴時cosplay動漫角色，多套爆乳裝扮讓粉絲看得目不轉睛，追蹤人數直線上升，目前有65.7萬人訂閱頻道",
  "priority": "1"
}
```

## 回應

> 簡單的回應訊息，來確定是否存檔成功
> 使用通用格式 code 0 msg succese

### Response 範例

```json
{
  "state": 200,
  "msg": "succese",
  "error": "",
  "data": {}
}
```
