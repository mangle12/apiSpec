# 真人API-系統維運狀態
###### tags: `高鐵AI規劃`


:::info 
為了讓datasource 回歸到正常的設計模式，將真人的 datasource 移除
全部透過無狀態的服務做存檔
:::

#### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /chat/agent/agsSystem
  Real 環境 API 地址 | `尚未定義`

#### 資料流向
```flow
st=>start: flow:>
op=>operation: 真人API
e=>end: 真人DB:>

st(right)->op(right)->e(bottom)

```

### Request 欄位
無



### Response 欄位

真人系統打開來看就知這是啥了，先這樣吧 不知如何敘述

```json
{
    "C3": "Y",
    "A1": "Y",
    "C4": "Y",
    "C5": "Y",
    "C6": "Y",
    "C7": "Y",
    "C1": "Y",
    "B1": "Y",
    "C2": "Y"
}
```

