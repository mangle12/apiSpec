
# POSTGRES 
###### tags: `SQL`


## 登入
#### (指定的格式： psql -h [主機IP或名稱] -p [port 號] [資料庫名稱] [使用者名稱])
:::info

$psql -h 10.0.31.184 -p 5555 aicsdb postgres
:::
切換資料庫：
:::info
postgres=# \c aicsdb
:::


離開 psql 操作介面：
:::info
postgres=# \q
:::


離開 psql 操作介面：
:::info
postgres=# \q
:::


操作.SQL檔匯入
:::info
psql -d mydb -f D:\sql\data.sql
-d 指定 database，-f 指定檔案
:::



## 資料庫備份

#### 透過pg_dump 匯出整個DB
```sql
pg_dump -U pbd4 PBD4Chatweb > PBD4Chatweb_bak.sql

pro
pg_dump -U aicsuser aicsdb > aicsdb_bak.sql
```
:::info
使用語法的時候需要將$去除
-U {使用者名稱} {資料庫名稱}
    > {輸出路徑} 遠端下SQL的絕對路徑
:::


#### 實用參數
::: info 
-t 選定
-T 排除
##### 必須注意 postgres 的 匯出指令是包含create table 的因此如果是需要表匯入的方式請加帶此參數
-c --if-exists
:::

#### 排除 flow_call_log、sys_log 兩張表
```sql
pg_dump -c --if-exists -T flow_call_log -T sys_log -U pbd4 PBD4Chatweb > PBD4Chatweb_bak.sql
```

#### 僅儲存 config_detail 兩張表
```sql
pg_dump -c --if-exists -t config_detail -U pbd4 PBD4Chatweb > PBD4Chatweb_bak.sql
```

## 資料庫還原
```sql
psql -U postgres -d dbname < filename.sql
```
:::info
dbname 資料庫名稱
#### postgres 很特別會先把你DB給砍了請 "眼睛睜大"看清楚目前登入的帳號是誰

#### -c --if-exists 沒有使用此參數的匯入僅限用於新建DB
:::


## postgres TRANSACTION 模式

#### 不用想太多 下就對了 如果有摸過其他sql 差別不大 多了一個SAVEPOINT的用法 用不到就當沒這回事..

### TransAction 交易模式
> commit 確認交易
> begin transaction 模式的起頭 
```sql
BEGIN;
update config_detail set patam = '0.75' where function_id ='CDS_threshold_nlu_current';
update config_detail set patam = '0.76' where function_id ='CDS_threshold_nlu_current';
update config_detaila set patam = '0.77' where function_id ='CDS_threshold_nlu_current';
COMMIT; 
```

### Rollback 退回
>全部退回，用不到savepoint
```sql
rollback;
```


### savepoint 儲存點
```sql
BEGIN;
UPDATE accounts SET balance = balance - 100.00
    WHERE name = 'Alice';
SAVEPOINT my_savepoint;
UPDATE accounts SET balance = balance + 100.00
    WHERE name = 'Bob';
-- oops ... forget that and use Wally's account
ROLLBACK TO my_savepoint;
UPDATE accounts SET balance = balance + 100.00
    WHERE name = 'Wally';
COMMIT;
```

### 查連線SPID
```sql
select * from pg_stat_activity;
show max_connections;
```

查高鐵信心值用
```
SELECT * FROM config_detail
where function_id like 'threshold_nlu%';
SELECT * FROM config_detail
where function_id like 'secondThreshold%';
```