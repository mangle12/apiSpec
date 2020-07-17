# LFS訂單失敗紀錄檔

###### tags: `高鐵AI規劃`

:::info 
從 TPIGetway 發起外部API存檔失敗後要做紀錄，特定的幾隻作業需要有
存檔位置:真人客服的service下的postgreSQL
作業清單如下
  * [遺失物單據建立](./gvchtLqxQRyyICgOCTuXRw) (看需求只有這隻)
  * [需求引導單建立＿新增單據](./c3tTMmKWQZOO2ypMQuoGvA)(預留接口)
  * [需求引導單修改刪除＿修改單據](./9sUpbDMeSS-b8FTjWdRqcA) (預留接口)

:::

#### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /thsr/txlog/savelog_lfs
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
psgName |String | 16 | 張三豐 | N | 旅客完整姓名
psgTel |String | 16 | 0225112233 | N | 旅客市話號碼
pickupStationId |String | 2 | 08 |Y |  方便領取的車站 (請參考代碼表)
psgAddr |String | 200 | 台北市某道觀 |N |  地址
psgSex |String | 1 | M | N |  性別 ('M':男; 'F':女)
lostSite |String | 1 | S | Y | 遺失地點 ('S':車站; 'T':列車)
lostStationId |String | 2 | 08 | Y | "遺失發生的車站 (請參考代碼表)(若 lostSite=='S' 則為必填)"
lostTrainNo |String | 8 | 649 | N | 遺失列車車次 (若 lostSite=='T' 則為選填)
lostSeatNo |String | 8 | 14E | N | 遺失座位號碼 (若 lostSite=='T' 則為選填)
lostLocation |String | 32 | 第二月台 | Y | 遺失位置 **
lostDate |String | 8 | 20191025 | Y | 遺失日期 (yyyyMMdd)
lostTime |String | 4 | 1325 | Y | 遺失時間 (HHmm)
lostObjectName |String | 96 | 黑色隨身聽一台 | Y | 遺失物內容


### 表名稱 thsrc_lost_order_record
#### 資料庫欄位對應

表欄位名稱 | 表說明 | Response 
--------- | ------- | ----|
seqno  | 流水號 | 自動建立不用管
applicant_name | 旅客姓名 | psgName
applicant_phone | 旅客連絡電話 | psgTel
applicant_gender | 旅客性別 | psgSex
applicant_attr | 旅客地址 | psgAddr
pickup_station | 方便領取車站 | pickupStationId
lost_site | 遺失地點 | lostSite
lost_station | 遺失發生車站 | lostStationId
lost_train_no | 遺失列車車次 | lostTrainNo
lost_seat_no | 遺失座位號碼 | lostSeatNo
lost_location | 遺失位置 | lostLocation
lost_date | 遺失日期 | lostDate
lost_time | 遺失時間 | lostTime
lost_property | 遺失物內容 | lostObjectName
lost_order_status | 處理狀況 | N(尚未報失)
create_user | 建立人員ID | "flow auto"
create_time | 建立時間 | 系統時間
update_user | 異動人員ID | 
update_time | 異動時間 | 




