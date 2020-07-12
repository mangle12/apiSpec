# 取得Flow系統參數

###### tags: `高鐵AI規劃`
:::info
從Flow to TPIGetway 取得資料庫資料
:::
==20200103 modi by 子彥 增加讀取共用參數的部分==


#### 規格
通過系統的識別代號對資料庫取得固定的詞彙。來輸入在FLOW內，所有的節點須自定義，沒有一定要怎麼樣寫FLOW的人決定即可。

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | \thsr\public\getconfig
  Real 環境 API 地址 | `尚未定義`

### 資料流向
```flow
st=>start: flow:>
op2=>operation: TPIGetway
e=>end: flow:>

st(right)->op2(right)->e(bottom)

```

### Request 欄位

  欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
  --------- | ------- |-----| --------|--------|--------
  parameter_key | int | - | 200 | Y | LFS 


  

### Request 範例

```
  {
    "parameter_key": "LFS",
  }
```


### Response 欄位

  欄位名稱名稱 | 資料型別| 長度| 說明
  --------- | ------- |-----| --------
  content | array | - | 


### content 欄位  

  欄位名稱名稱 | 資料型別| 必要| 說明
  --------- | ------- |-----| --------
  function_id | filed | Y | 功能代碼
  param | filed | Y | 參數內容


### Response 範例
"function_id": "param" //示意說明..
```
  {
    "content": { 
      "nlu.current":  "http:///123456789"
      "nlu.yesno": "http:///12345678977777777777",
      "intent.lfs": "遺失物",
      "intent.PGSMS": "乘車導引",
      "intent.search": "票價查詢",
      "intent.nlu": "http:///12345678977777777777",
    }
  }
```
