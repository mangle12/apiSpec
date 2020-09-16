# ERP 驗證

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | GET                                          |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/login                                  |
| 通用格式                | 否                                           |

## 請求

### Request 欄位

| 欄位名稱 | 資料型別 | 長度 | 必須 | 說明               |
| -------- | -------- | ---- | ---- | ------------------ |
| token     | string   | -    | Y    | ERP 發行的環境變數 |
| staffsNo | string   | 12   | Y    | 員工編號           |

### Request 範例

```json
{
  "token": "42e29e35-b835-4a95-afaf-d4733bbedd7f",
  "staffsNo": "A00001"
}
```

## 回應

### Response 欄位

| 欄位名稱名稱 | 資料型別 | 長度 | 必須 | 說明     |
| ------------ | -------- | ---- | ---- | -------- |
| url          | string   | -    | Y    | 用戶編號 |

### Request 範例

```json
{
  "url": "https://www.tpisoftware.com/home?staffsNo=A00001&token=42e29e35-b835-4a95-afaf-d4733bbedd7f"
}
```
