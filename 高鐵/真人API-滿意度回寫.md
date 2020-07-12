# 真人API-滿意度回寫
###### tags: `高鐵AI規劃`


:::info 
為了讓datasource 回歸到正常的設計模式，將真人的 datasource 移除
全部透過無狀態的服務做存檔
:::

#### 規格

  項目 | 說明
  ---- | ---
  Method | GET
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /chat/agent/saveOcsScoreDetail
  Real 環境 API 地址 | `尚未定義`

#### 資料流向
```flow
st=>start: flow:>
op=>operation: 真人API
e=>end: 真人DB:>

st(right)->op(right)->e(bottom)

```
### Request 欄位

欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
sessionId| string | |  | N | sessionId 
rankBot| string | |  | N | 機器人分數
rankAgent| string | |  | N | 真人分數
sensitive| string | |  | N | 有無觸發敏感詞 

```json
{
    "sessionId":"3333333333333",
    "rankBot":5,
    "rankAgent":3,
    "sensitive":"Y"
}
```

### Response 欄位

回應字串文字

