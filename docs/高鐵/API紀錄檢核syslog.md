# API紀錄檢核syslog

###### tags: `AI規劃`

#### 資料流向
```flow
st=>start: flow:>
e=>end: TPIGetway:>
st(right)->e(bottom)

```

### DB 欄位

欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
id | string | - | true | Y | 流水序 (毫無意義)
session_id| string | - | true | Y | session_id
connection_id| string | - | true | N | connection_id（國泰）
method| string | - | true | Y | JAVA檔名
params|stringO | - | true | Y | 傳入值
result| string | - | true | Y | 查詢結果(如有呼叫外部API)
remark| string | - | true | Y | 可備註外部API名稱(如有呼叫外部API)
cost_time| string | - | true | Y | 花費時間成本(毫秒)
create_time| string | - | true | Y | 起始時間
update_time| string | - | true | Y | 更新時間(基本上沒意義，因為都一樣)

### 用途
用來解析API異常緩慢的問題，因此可透過此DB資料搜尋找出特慢的API或是透過 session_id
找到回傳異常的API