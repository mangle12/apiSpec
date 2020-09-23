# 取得 FAQ 類別

### 作業目的

> FAQ 取得 FAQ 類別

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | POST                                          |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/faq/type                               |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 回應

### Response 欄位

| 欄位名稱名稱 | 資料型別    | 長度 | 必須 | 說明         |
| ------------ | ----------- | ---- | ---- | ------------ |
| data         | Arrayobject | -    | Y    | 回傳全部類別 |

#### data 欄位

| 欄位名稱名稱 | 資料型別 | 長度 | 必須 | 說明          |
| ------------ | -------- | ---- | ---- | ------------- |
| typeNo        | string   | 40   | Y    | FAQ type ID   |
| typeName      | string   | 20   | Y    | FAQ type name |

### Response 範例

```json
{
  "state": 200,
  "msg": "succese",
  "error": "",
  "data": [
    {
      "typeNo": "01",
      "typeName": "問題分類1"
    },
    {
      "typeNo": "02",
      "typeName": "問題分類2"
    }
  ]
}
```
