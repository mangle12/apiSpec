# 真人API-留言版
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
  測試 環境 API 地址 | /chat/agent/messageBoard
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

欄位名稱 | 資料型別| 長度|Response範例| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
message.Board.Period |string | - | - | Y | 留言板時間
unprocessed.count |string | - | - | Y | 目前留言板未處理數
close.Message.Board |string | - | - | Y | 關閉留言板之未處理留言數最大值

```json
{
    "message.Board.Period": "08:00~22:00",
    "unprocessed.count": "999",
    "close.Message.Board": "50"
}
```

