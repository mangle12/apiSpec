# MongoDB指令
###### tags: `教育訓練文件`


### 查詢資料庫清單
:::success
show dbs
:::

### GOTO 資料庫
:::success
use 資料庫
:::

### nodemessages 查詢
:::success
```
db.getCollection('nodemessages').find({
    'info.appId': 'f0e50683b41ad638c2c8.312b4362139c',
    'type': 'output',
}).sort({ 'registered_at': -1 }).limit(50);
```
:::	

### 重啟mongoImport 
:::success
docker run --name systalk-mongoImport_tmp --rm \
-e "MONGO_HOSTS=mongodb://chatflex:chatflex123@10.0.31.184:23001" \
-e "ELASTICSEARCH_HOSTS=https://10.0.31.184:9200/" \
-e "FLOW_DB_NAME=systalk-flow" \
-e "FLOW_INDEX_PREFIX=flow" \
-e "IMPORT_APP_ID=[Firstbot AppID]" \
-e "IMPORT_DATE=2020-03-02" \
systalk/report-mongo-importer:1.1.6-systalk
:::

### mongodb

查詢不相等 
:::success
db.user.find( { age: {$ne:18} }
:::


### find運算元

:::success
條件|	操作符號|
-|-
AND|	$and，另一種方法也可以直接在query中下{"key1","value1","key2":"value2"}
OR|	$or
NOT|	$not
NOR|	$nor
大於|	$gt
大於等於|	$gte
小於|	$lt
小於等於|	$lte
包含|	$in
不包含|	$nin
:::

條件寫法 參考
https://ithelp.ithome.com.tw/articles/10185439


```
進階查詢

```


