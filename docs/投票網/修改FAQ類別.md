# 修改 FAQ 類別

### 作業目的

> 修改 FAQ 類別

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | POST                                         |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/edittype                           |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 回應

### Request 欄位

| 欄位名稱名稱 | 資料型別 | 長度 | 必須 | 說明           |
| ------------ | -------- | ---- | ---- | -------------- |
| action       | string   | 1    | Y    | 1.修改 2 刪除  |
| typeNo       | string   | 40   | Y    | 修改代號       |
| typeName     | string   | 20   | O    | 預計修改的名稱 |

### Request 範例

```json
{
  "action": "1",
  "typeNo": "A00001",
  "typeName": "其他問題"
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
