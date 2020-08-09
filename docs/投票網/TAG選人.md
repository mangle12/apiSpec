# TAG 選人

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | GET                                          |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/staffs/list                            |
| 通用格式                | 是                                           |
| authorization           | Bearer { token }                             |

## 回應

### Response 欄位

| 欄位名稱 | 資料型別      | 長度 | 必須 | 說明 |
| -------- | ------------- | ---- | ---- | ---- |
| data     | array[object] | -    | Y    |  直接回傳全公司資料    |

> 系統不停止運行前，都會存在全域變數內部不在呼叫

### data 欄位

| 欄位名稱 | 資料型別 | 長度 | 必須 | 說明 |
| -------- | -------- | ---- | ---- | ---- |
| no       | string   | 12   | Y    |      |
| name     | string   | 20   | Y    |      |
| ename    | string   | 20   | Y    |      |

### Response 範例

```json
{
  "data": [
    {
      "no": "A00001",
      "name": "姚勝富",
      "ename": "BEN"
    },
    {
      "no": "A00002",
      "name": "葉怡蘭",
      "ename": "Yilan Yeh"
    },
    {
      "no": "A00003",
      "name": "蔡敏欣",
      "ename": "Mandy Tsai"
    }
  ]
}
```
