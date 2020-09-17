# 修改 FAQ

### 作業目的

> 修改 FAQ

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | GET                                          |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/edit                               |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 回應

### Request 欄位

| 欄位名稱名稱 | 資料型別 | 長度 | 必須 | 說明                     |
| ------------ | -------- | ---- | ---- | ------------------------ |
| action       | string   | 1    | Y    | 1. 修改 2. 刪除          |
| faqNo        | string   | 40   | Y    | FAQ 代號                 |
| typeNo       | string   | 40   | O    | 類別代號 action = 1 必填 |
| quset        | string   | 20   | O    | 問題 action = 1 必填     |
| ans          | string   | 1    | O    | 答案 action = 1 必填     |
| priority     | string   | 1    | O    | 優先級 action = 1 必填   |

### Request 範例

```json
{
  "action": "1",
  "faqNo": "20200720142103A0003",
  "typeNo": "20200720142103A0003",
  "quset": "pan piano為什麼收看率這麼高",
  "ans": "「Pan Piano」同樣也是鋼琴YouTuber，一開始都是以日常穿著入鏡，從未露臉，不過她的好身材經常受到討論，Pan也開始在彈鋼琴時cosplay動漫角色，多套爆乳裝扮讓粉絲看得目不轉睛，追蹤人數直線上升，目前有65.7萬人訂閱頻道",
  "priority": "11"
}
```

## 回應

> 簡單的回應訊息，來確定是否存檔成功
> 使用通用格式 code 200 msg succese

```json
{
  "state": 200,
  "msg": "succese",
  "error": "",
  "data": {}
}
```
