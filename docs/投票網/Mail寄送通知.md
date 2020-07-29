# Mail 寄送通知

### 作業目的

> Mail 寄送通知

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | POST                                         |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/schedule/mail                          |
| 通用格式                | 否                                           |

## 請求

### Request 欄位

| 欄位名稱 | 資料型別 | 長度 | 必須 | 說明        |
| -------- | -------- | ---- | ---- | ----------- |
| text     | string   | 500  | Y    | mail 的內容 |
| work_no  | string   | 500  | Y    | 作業代號    |


### 作業代號簡述
| 作業代號 | 作業功能      |
| -------- | ------------- |
| VOTS01   | 活動通知 Mail |
| VOTS02   | 催票通知 Mail |
| VOTS03   | 活動結束 Mail |
| VOTS04   | 聯繫我們      |
| VOTS05   | 保留 1        |
| VOTS06   | 保留 2        |


### Request 範例

```json
{
  "text": "你低头 眉间落下场雪 我抚平情愫万千 帘外响起 霜将琴声冷却 刹那间 过往事皆湮灭 江南又梦烟雨 长河流入故里",
  "work_no": "VOTS01"
}
```

## 回應

> 簡單的回應訊息，來確定是否存檔成功
> 使用通用格式 code 0 msg succese

### Response 範例

```json
{
  "code": "0",
  "msg": "succese",
  "error": ""
}
```
