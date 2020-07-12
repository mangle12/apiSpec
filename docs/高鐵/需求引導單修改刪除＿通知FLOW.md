# 需求引導單修改刪除＿通知FLOW
###### tags: `高鐵AI規劃`

>從TPIGetway to Flow 需求引導單通知


### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | 請求最初來源是flow回應即可
  Real 環境 API 地址 | `尚未定義`

  
### 資料流向
```flow
st=>start: TPIGetway:>
e=>end: flow:>
st(right)->e(bottom)
```

### Request 欄位

  欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
  --------- | ------- |-----| --------|--------|--------
  channel  | String |8| 根據平台而定 ChatWeb、FB 
  source |String | -| 固定傳送 (thsr)
  role |String||固定傳送(thsr)
  fbintent | string | | 掛失 | N | Firstbot意圖
  sbintent | string | | 記名卡 | N | Secondbot意圖
  content | object | max |


### customerData 欄位
  欄位名稱名稱 | 資料型別| 長度| 必須 | 說明[參考高鐵API]()
  --------- | ------- |-----| --------|--------|--------
serviceNo | String | 12 |  Y | serviceNo 導引單編號
message | String | 255 |  Y | responseMsg 應用系統回傳訊息(未定義)
responseCode | String | 255 |  Y | responseMsg 應用系統回傳Code(未定義)


### Request 範例
```
{
  "channel":"FB",
  "source": "thsr",
  "role": "thsr",
  "fbintent": "掛失",
  "sbintent": "記名卡",
  "content": {
      "serviceNo":"12345",
      "message":"失敗，已結案單號不可變更",
      "responseCode":"03"
  },
}
```