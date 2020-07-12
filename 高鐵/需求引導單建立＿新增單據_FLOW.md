# 需求引導單建立＿新增單據_FLOW

###### tags: `高鐵AI規劃`

>從flow > TPIGetway 建立引導單..

### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /thsr/guide/createOrder
  Real 環境 API 地址 | `尚未定義`

### 資料流向
```flow
st=>start: flow:>
e=>end: TPIGetway:>

st(right)->e(bottom)

```

### Request 欄位

欄位名稱 | 資料型別| 長度| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
account | string | 20 | Y| 手機驗證後會有的資料
token | string | 20 |Y| 手機驗證後會有的資料
authPhone | string | 20 |Y| 手機驗證後會有的資料
forceCreate |  string | 1 |Y |手機驗證後會有的資料
channel | string | 8|  Y |根據平台而定 ChatWeb、FB
fbintent | string | | N | Firstbot意圖
sbintent | string | | N | Secondbot意圖
serviceNo | string | 12 | N | 導引單編號（新增固定為空字串）
applyDatetime | string | 14 | N | 申請日期時間（新增固定為空字串）
passengerName | string | 10 | Y | 旅客姓名
passengerSex | string | 1 | Y | 旅客性別（'M'/'F'）
passengerTel | string | 10 | Y | 旅客聯絡電話
emergencyContact | string | 10 | Y | 緊急聯絡人
emergencyTel | string | 10 | Y | 緊急聯絡人電話
originStation | string | 2 | Y | 起站（請參考代碼表）
terminalStation | string | 2 | Y | 迄站（請參考代碼表）
trainDepartDate | string | 8 | Y |  列車發車日期yyyyMMdd
stationDepartDateTime | string | 12 | Y | 起站發車時間yyyyMMddHHmm
stationArrivalDateTime | string | 12 | Y | 迄站到達時間yyyyMMddHHmm
trainNo | string | 4 | Y | 車次
carNo | string | 2 | Y | 車廂（01~12）
rowNo | string | 2 | Y | 座位排數（01~20）
seatNo | string | 1 | Y | 座位號碼（A/B/C/D/E）
passengerStatus | string | 1 | Y | 身心狀況：A：視障 B：年長 C：行動不便 D：拐杖/助行器 E：輪椅旅客 
passengerNeeds | string | 1 | Y | 乘車需求：A：自備輪椅 B：借用輪椅1台及服務人員推送 C：借用輪椅即可 D：僅需導引
  serviceProvider| string | 1 | Y | 服務提供車站：S：起站 E：迄站 A：起迄站皆需要

### Request 範例
```
 {   
     "account":"AICS12345678",			
     "token":"a1b2c3d4e5f6",			
     "authPhone":"0933654321",			
     "forceCreate":"",	
     "channel":"",
     "fbintent":"",
     "sbintent":"",
     "serviceNo":"" ,
     "applyDatetime":"" ,
     "passengerName":"顧傾城" ,
     "passengerSex":"M" ,
     "passengerTel":"3345678" ,
     "emergencyContact":"顧OO" ,
     "emergencyTel":"2345678" ,
     "originStation":"01" ,
     "terminalStation":"04" ,
     "trainDepartDate":"20190101",
     "stationDepartDateTime":"201901011401",
     "stationArrivalDateTime":"201901011401",
     "trainNo":"666"  ,
     "carNo":"12",
     "rowNo":"13",
     "seatNo":"B",
     "passengerStatus":"A",
     "passengerNeeds":"B",
     "serviceProvider":"A"
  }
```


