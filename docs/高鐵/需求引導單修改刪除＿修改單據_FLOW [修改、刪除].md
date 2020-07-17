# 需求引導單修改刪除＿修改單據_FLOW [修改、刪除]
###### tags: `高鐵AI規劃`

>從Flow to TPIGetway 調出 1(修改班次資料修改) 2.(導引需求修改) 3. (身心狀態修改)4
>訂單 修改刪除

```flow
st=>start: flow:>
e=>end: TPIGetway:>

st(right)->e(bottom)

```

### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /thsr/guide/editOrder
  Real 環境 API 地址 | `尚未定義`

### Request 欄位

欄位名稱 | 資料型別| 長度| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
state | String | 1 | Y | PGSMSEditNum(修改班次資料修改) PGSMSEditNeedinfo(導引需求修改) PGSMSEditNeedState (身心狀態修改) PGSMSDelete(刪除)
account | string | 20 | Y| 手機驗證後會有的資料
token | string | 20 |Y| 手機驗證後會有的資料
authPhone | string | 20 |Y| 手機驗證後會有的資料
forceCreate |  string | 1 |Y |手機驗證後會有的資料
channel | string | 8|  Y |根據平台而定 ChatWeb、FB
fbintent | string | | N | Firstbot意圖
sbintent | string | | N | Secondbot意圖
serviceNo | string | 12 | Y | 導引單編號（修改為必填）
applyDatetime | string | 14 | Y | 申請日期時間（）
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
    "state":"PGSMSEditNum",
    "account": "AICS12345678",			
    "token": "a1b2c3d4e5f6",			
    "authPhone": "0933654321",			
    "forceCreate": "",	
    "channel":"",
    "fbintent":"",
    "sbintent":"",
    "serviceNo" :"" ,
    "applyDatetime" :"" ,
    "passengerName" :"顧傾城" ,
    "passengerSex" :"M" ,
    "passengerTel" :"3345678" ,
    "emergencyContact" :"顧OO" ,
    "emergencyTel" :"2345678" ,
    "originStation" :"01" ,
    "terminalStation" :"04" ,
    "trainDepartDate":"20190101",
    "stationDepartDateTime":"201901011401",
    "stationArrivalDateTime":"201901011401",
    "trainNo":"666"  ,
    "carNo":"12",
    "rowNo":"13",
    "seatNo":"B",
    "passengerStatus":"A",
    "passengerNeeds":"B"    
  }
```