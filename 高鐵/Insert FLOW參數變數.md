# Insert FLOW參數變數

###### tags: `高鐵AI規劃`
:::info
從Flow to TPIGetway 回寫資料庫資料 
TABLE config_detail

:::
==20200318 modi by 子彥 增加寫入共用參數的部分==


#### 規格

  項目 | 說明
  ---- | ---
  Method | POST
  Required Request Header |  Content-Type:application/json; charset=UTF-8
  測試 環境 API 地址 | /thsr/public/insertPublic
  Real 環境 API 地址 | `尚未定義`

### 資料流向
```flow
st=>start: flow:>
op2=>operation: TPIGetway
e=>end: DB:>

st(right)->op2(right)->e(bottom)

```

### 規則
#### 先查詢後寫入
:::info
查詢SQL
select * from config_detail 
where parameter_key = req{'parameter_key'} and
      function_id   = req{'function_id'} 
:::

#### 找到update SQL
:::info

update config_detail set  param = req{'param'} 
where parameter_key = req{'parameter_key'} and
      function_id   = req{'function_id'} 
:::

#### 沒找到Insert SQL
:::info
**這個我不確定postgres是不是這樣寫，應該是吧 TSQL都差不多...**
INSERT INTO config_detail ("parameter_key", "function_id", 'param','description')
VALUES ("req{'parameter_key'}", "req{'function_id'}", req{'param'}, req{'description'});
:::


### Request 欄位

  欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
  --------- | ------- |-----| --------|--------|--------
  data | oa | - |  |Y | 物件陣列 [key:value,key:value,]
  
 ### Request 欄位 
  欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
  --------- | ------- |-----| --------|--------|--------
  parameter_key |string | 11 | first | Y | BOT識別
  function_id | string | 50 | 可變量 |Y | 
  param | string | 255 | ---- | Y | 
  description | string | 255 | ---- | N | 

### Request 範例

```
  {
    "data":[
        {
             parameter_key:'first',
             function_id:'FAQTest',
             param:'test',
             description:'test'
        },
        {
             parameter_key:'first',
             function_id:'FAQTest11',
             param:'FAQTest11',
             remark:'FAQTest11'
        },
        {
            .....
        }
        
    ]
  }
```


### Response 欄位
:::success
  回應原型就好
  code 0
  msg xxxxx 
  ```
    {
        code:0
        msg:'xxxxxxxxxxxxxx'
    }
  ```
:::
```
