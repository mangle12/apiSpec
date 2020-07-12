# 需求引導單查詢＿通知FLOW
###### tags: `高鐵AI規劃`

### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | flow位置
  Real 環境 API 地址 | `尚未定義`

  
### 資料流向
```flow
st=>start: TPIGetway:>
e=>end: flow:>
st(right)->e(bottom)
```

### Response 欄位



  欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
  --------- | ------- |-----| --------|--------|--------
  channel  | String |8| 根據平台而定 ChatWeb、FB 
  source |String | -| 固定傳送 (thsr)
  role |String||固定傳送(thsr)
  fbintent | string | | 掛失 | N | Firstbot意圖
  sbintent | string | | 記名卡 | N | Secondbot意圖
  content | object | max |



### content 欄位
| 欄位名稱 | 資料型別 | 長度 | 範例 | 必須 | 說明 說明[參考高鐵API]()
| ---------- | --------- | ---------- | ----  | -------- | ----- 
serviceNo | String | 12 | | Y | serviceNo 導引單編號
message | String | 255 | | Y | responseMsg 應用系統回傳訊息(未定義)
| serviceNo | String | 12 | e.g. '' | N | 導引單編號（新增固定為空字串） |
| applyDatetime | String | 14 | yyyyMMddHHmmss | N | 申請日期時間（新增固定為空字串） |
| passengerName | String | 10 | e.g. '令狐沖' | Y | 旅客姓名 |
| passengerSex | String | 1 | e.g. 'M' | Y | 旅客性別（'M'/'F'） |
| passengerTel | String | 10 | e.g. '0933654321' | Y | 旅客聯絡電話 |
| emergencyContact | String | 10 | e.g. '任盈盈' | Y | 緊急聯絡人 |
| emergencyTel | String | 10 | e.g. '0915123456' | Y | 緊急聯絡人電話 |
| originStation | String | 2 | e.g. '04' | Y | 起站（請參考代碼表） |
| terminalStation | String | 2 | e.g. '07' | Y | 迄站（請參考代碼表） |
| trainDepartDate | String | 8 | yyyyMMdd | Y | 列車發車日期 |
| stationDepartDateTime | String | 12 | yyyyMMddHHmm | Y | 起站發車時間 |
| stationArrivalDateTime | String | 12 | yyyyMMddHHmm | Y | 迄站到達時間 |
| trainNo | String | 4 | e.g. '0987' | Y | 車次 |
| carNo | String | 2 | e.g. '07' | Y | 車廂（01~12） |
| rowNo | String | 2 | e.g. '14' | Y | 座位排數（01~20） |
| seatNo | String | 1 | e.g. 'E' | Y | 座位號碼（A/B/C/D/E） |
| passengerStatus | String | 1 | e.g. 'E' | Y | "身心狀況：A：視障 B：年長 C：行動不便 D：拐杖/助行器 E：輪椅旅客" |
| passengerNeeds | String | 1 | e.g. 'A' | Y | "乘車需求： A：自備輪椅 B：借用輪椅1台及服務人員推送 C：借用輪椅即可 D：僅需導引" |
| serviceProvider | String | 1 | e.g. 'A' | Y | "服務提供車站： S：起站 E：迄站 A：起迄站皆需要" |
cards| object | - | 卡牌 | Y | 參考[乘車資訊牌卡](./ff5zk72RSEuer268gMy7XA)

### content 範例
```
{
  "channel":"FB",
  "source": "thsr",
  "role": "thsr",
  "fbintent": "掛失",
  "sbintent": "記名卡",
  "content": {
      ........參考上面內容或是其他隻相同的多一個位置叫做
      cards 參考乘車資訊牌卡
  }
}
```



