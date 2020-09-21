# FAQ 類別建立作業

### 作業目的

> FAQ 類別建立作業

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | POST                                         |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/type                               |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 請求

### Request 欄位

| 欄位名稱 | 資料型別 | 長度 | 必須 | 說明                |
| -------- | -------- | ---- | ---- | ------------------- |
| text     | string   | 64   | Y    | form.輸入的類別名稱 |

### Request 範例

```json
{
  "text": "常見問題類"
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