# mongodb 瘦身
###### tags:`工作用`

### nodemessages 查詢
:::success
mongodb 查詢語法
```
db.getCollection('nodemessages').find({
    'info.appId': 'FLOW的appid',
    'type': 'output',
}).sort({ 'registered_at': -1 }).limit(50);
```
:::	


在mongodb下查詢後 會得到這張圖

![](https://i.imgur.com/HD4Inb7.png)


紅框這些的都是垃圾需刪除
刪除後結果應該會如下圖所示..


![](https://i.imgur.com/gVPuYV2.png)


否則光內部的資料成長速度就頗驚人

![](https://i.imgur.com/M62qw3j.png)


主要是AI那邊在nodemessage的使用方式與我們預想中的不同。因此目前須改善FLOW三處位置

### 1. 首先結尾段要刪除這些資料。
![](https://i.imgur.com/ejMUuVb.png)


### 2. 將原先寫在回應段的程式碼
移動到下述的位置
![](https://i.imgur.com/IT6TTAb.png)


### 3. 將原先開DB那段稍作改善，每次都開
DB IO負載高 總比資料庫炸掉好....
![](https://i.imgur.com/SbvLdms.png)

