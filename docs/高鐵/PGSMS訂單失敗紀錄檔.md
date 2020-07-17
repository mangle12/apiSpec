# PGSMS訂單失敗紀錄檔

###### tags: `高鐵AI規劃`

:::info 
從 TPIGetway 發起外部API存檔失敗後要做紀錄，特定的幾隻作業需要有
存檔位置:真人客服的service下的postgreSQL
:::

#### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /thsr/txlog/savelog_pgsms
  Real 環境 API 地址 | `尚未定義`

#### 資料流向
```flow
st=>start: TPIGetway:>

e=>end: 真人DB:>

st(right)->e(bottom)

```

#### Request 欄位

欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
fbintent | string | | 掛失 | N | Firstbot意圖
sbintent | string | | 記名卡 | N | Secondbot意圖
channel |	String | 8| FB ||根據平台而定 ChatWeb、FB
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



### 表名稱 thsrc_guide_services_record
#### 資料庫欄位對應

表欄位名稱 | 表說明 | Response 
--------- | ------- | ----|
seqno | 流水號 | 
passenger_name | 旅客姓名 | passengerName
passenger_sex | 旅客性別（M:男,F:女）| passengerSex
passenger_tel | 旅客聯絡電話 | passengerTel
emergency_contact | 緊急聯絡人| emergencyContact
emergency_tel | 緊急聯絡人電話 | emergencyTel
origin_station | 起站 | originStation
terminal_station | 迄站 | terminalStation
train_depart_date | 列車發車日期 | trainDepartDate
station_depart_date_time | 起站發車時間 | stationDepartDateTime
station_arrival_date_time | 迄站到達時間 |stationArrivalDateTime
train_no | 車次 | trainNo
car_no | 車廂（01~12） | carNo
row_no | 座位排數（01~20） | rowNo
seat_no | 座位號碼（A/B/C/D/E） |seatNo
passenger_status | 身心狀況(A:視障,B:年長,C:行動不便,D:拐杖/助行器,E:輪椅旅客) | 存中文字給他 passengerStatus
passenger_needs | 乘車需求(A:自備輪椅，導引人員一名,B:借用輪椅一台，導引人員一名,C:借用輪椅一台，不需導引人員,D:僅需導引人員一名)  | 存中文字給他 passengerNeeds
service_provider | 服務提供車站(S:起站,E:迄站,A:起迄站皆需要) | 存中文字給他 serviceProvider
guide_services_status | 處理狀況(N:待處理,Y:已處理)| N
create_user | 異動人員ID 
create_time | 異動時間 
update_user |  
update_time |  





