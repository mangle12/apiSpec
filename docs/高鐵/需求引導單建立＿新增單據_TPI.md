# 需求引導單建立＿新增單據_TPI

###### tags: `高鐵AI規劃`

>從TPIGetway> 高鐵 新增導引單請求

### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /api/pgsms/v1/POST/createGs
  Real 環境 API 地址 | `尚未定義`

### 資料流向
```flow
st=>start: TPIGetway:>
e=>end: 高鐵:>

st(right)->e(bottom)

```

### request 欄位說明

| 欄位名稱 | 資料型別 | 長度 | 範例 | 必須 | 說明 |
| ---------- | --------- | ---------- | ----  | -------- | ----- 
| header | object | - | 參考說明 | Y | 參考說明 [header說明](##header說明)
| account | String | 20 | e.g. 'AICS12345678' | Y | 系統帳號(由PGSMS與AICS事前議定) |
| token | String | 20 | e.g. 'a1b2c3d4e5f6' | Y | 令牌(由PGSMS與AICS事前議定) |
| authPhone | String | 10 | e.g. '0933654321' | Y | 驗證電話 |
| forceCreate | String | 1 | e.g. '' | N | 是否強制建單(''/'Y'/'N') |
| data | object | - | | Y | 導引單物件 |


### header 說明
| 欄位名稱 | 資料型別 | 長度 | 範例 | 必須 | 說明 |
| ---------- | --------- | ---------- | ----  | -------- | ----------- |
| serviceToken | String | 36 | e.g. '2885f056-875f-42a3-ac55-66d037c1b469' | Y | Service Token (驗證用) |
| clientIp | String | 16 | e.g. '123.123.123.123' | Y | Client IP |
| timestamp | String | 14 | yyyyMMddHHmmssSSS | Y | 發送時間 (查核/追踪用; 精確至毫秒) |
| requestToken | String | 64 | e.g. '28288065-891f-4cdc-8bb0-

### data 說明
| 欄位名稱 | 資料型別 | 長度 | 範例 | 必須 | 說明 |
| ---------- | --------- | ---------- | ----  | -------- | ----- 
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

### Request 範例
```
{			
  "AICS": {			
    "header": {			
      serviceToken: "2885f056-875f-42a3-ac55-66d037c1b469",		
      clientIp: "123.123.123.123",			
      timestamp: "20190731112526543",			
      requestToken: "28288065-891f-4cdc-8bb0-3c27cba7c9ad"		
    },		
    parameter: {			
      account: "AICS12345678",			
      token: "a1b2c3d4e5f6",			
      authPhone: "0933654321",			
      forceCreate: "",	
      data:  {			
        serviceNo: "",			
        applyDatetime: "",			
        passengerName: "令狐沖",			
        passengerSex: "M",			
        passengerTel: "0933654321",			
        emergencyContact: "任盈盈",			
        emergencyTel: "0915123456",			
        originStation: "04",			
        terminalStation: "07",			
        trainDepartDate: "20191223",			
        stationDepartDateTime: "201912240025",			
        stationArrivalDateTime: "201912240045",			
        trainNo: "0987",			
        carNo: "07",			
        rowNo: "14",			
        seatNo: "E",			
        passengerStatus: "E",			
        passengerNeeds: "A",			
        serviceProvider: "A"			
      }			
    }			
  }			
} 
```