# 真人API-滿意度參數
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
  測試 環境 API 地址 | /chat/agent/satisfaction
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
satisfaction.agent.switch |string | - | - | Y | 真人評分啟用否
satisfaction.ai.switch |string | - | - | Y | 機器人評分啟用否
satisfaction.agent.title |string | - | - | Y | 真人評分台詞
satisfaction.ai.title|string | - | - | Y | 機器人評分台詞

```json
{
    "satisfaction.agent.switch": "true",
    "satisfaction.ai.switch": "true",
    "satisfaction.agent.title": "很高興為您服務！請幫真人客服的表現評個分好嗎？",
    "satisfaction.ai.title": "很高興為您服務！請幫智能客服機器人的表現評個分好嗎？"
}
```

