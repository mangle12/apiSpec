# 修改 FAQ 類別

### 作業目的

> 修改 FAQ 類別

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | GET                                          |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/edittype                           |
| 通用格式                | 是                                           |

## 回應

### Request 欄位

| 欄位名稱名稱 | 資料型別 | 長度 | 必須 | 說明           |
| ------------ | -------- | ---- | ---- | -------------- |
| type_no      | string   | 40   | Y    | 修改代號       |
| type_name    | string   | 20   | Y    | 預計修改的名稱 |
| type_state   | string   | 1    | Y    | 1.修改 2 刪除  |

### Request 範例

```json
{
  "type_no": "A00001",
  "type_name": "其他問題",
  "type_state": "1"
}
```

## 回應

> 簡單的回應訊息，來確定是否存檔成功
> 使用通用格式 code 0 msg succese
