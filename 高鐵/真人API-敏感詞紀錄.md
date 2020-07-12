# 真人API-敏感詞紀錄
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
  測試 環境 API 地址 | /chat/agent/checkSensitiveSentenceMsg
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
chatID| string | |  | N | sessionId 
chatMessage| string | |  | N | 對話 

```json
{
    chatID:"1ue81u918j2",
    chatMessage:"你他媽我敏感慈?"
}
```




### Response 欄位

steve 說射後不理




