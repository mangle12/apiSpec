# 真人API-取得敏感詞
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
  測試 環境 API 地址 | /chat/agent/findBySensitiveMsg
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
這回應有點狂，寫的人自己想辦法...
```javascript=
[
    "叫你主管出來",
    "客訴",
    "太差勁了"
]
```

