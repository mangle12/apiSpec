# 交易對話意圖紀錄 flow_call_log
###### tags: `AI規劃`


:::info 
搭配xxxxxx軟體為了呈現分析報表而定的資料儲存
主要用途方便客戶調教AI的精準度以及聰明性
:::

#### 規格



#### 資料流向
```flow
st=>start: flow:>
e=>end: TPIGetway:>
st(right)->e(bottom)

```

### Request 欄位


欄位名稱名稱 | 資料型別| 長度|Response範例| 必須 | 說明
--------- | ------- |-----| --------|--------|--------
ip | string | - | true | Y | 來源IP
session_id| string | - | true | Y | session_id（國泰）
connection_id| string | - | true | N | connection_id（國泰）
inputType| string | - | true | Y | def 1 (1 文字 2語音)
msgType| string | - | true | Y | customerMsg 、 等其他..(特殊訊息紀錄)
msgId|string | - | true | Y | 紀錄系統時間(母災為啥)
msg| string | - | true | Y | 當次文字
assignIntent| string | - | true | Y | 有無指定 行為意圖
assignSecondBotIntent| string | - | true | Y | 有無指定 操作意圖
assignParameter| string | - | true | Y | 有無參數 (最新版都是以Parameter為主)
firstNluIntent| string | - | true | Y | 總機意圖
firstNluScore| float | - | true | Y | 總機分數
firstNluSupportIntent| string | - | true | Y | 服務台意圖
firstNluSupportScore| float | - | true | Y | 服務台分數
faqAnswer| string | - | true | Y | FAQ ID
faqScore| float | - | true | Y | FAQ分數
secondNluEntities| string | - | true | Y | Second_實體1
secondNluAdd1Entities| string | - | true | Y | Second_實體2
secondNluAdd2Entities| string | - | true | Y | Second_實體3
flowTime| date | - | true | Y | 系統時間
flowCostTime| integer | - | true | Y | flow成本時間
flowHostName| string | - | true | Y | 串接手機端可做為紀錄用
flowFirstAppId| string | - | true | Y | 串接手機端可做為紀錄用
secondNluIntent| string | - | true | Y | 紀錄SecondBot的意圖
secondNluScore| string | - | true | Y | 紀錄SecondBot的意圖分數
secondNluEntities| string| - | true | Y | 紀錄SecondBot的對話產生實體
secondNluCostTime|string | - | true | Y | 紀錄SecondBot的FLOW成本
custId|string | - | true | Y | 員工編號
custom|string | - | true | Y | FAQ命中結果
botScore|string | - | true | Y | 機器人滿意度
agentScore|string | - | true | Y | 真人滿意度
custCmt |string| - | true | Y | 滿意度備註
memo| string | - | true | Y | 有需要記錄在使用
state| string | - | true | Y | 命中結果文字呈現

### Request範例

```json
{
    ip : "127.0.0.1",
    inputType: "1",
    msgType:"customerMsg",
    msgId:"1578551659857",
    msg:"明晚八點",
    assignIntent:"",
    assignSecondBotIntent:"",
    assignParameter:"",
    firstNluIntent:"乘車資訊",
    firstNluScore:"0.7986872411602549",
    firstNluSupportIntent:"查詢",
    firstNluSupportScore:"0.7986872411602549",
    faqAnswer:"",
    faqScore:"",
    secondNluEntities:"",
    secondNluAdd1Entities:"",
    secondNluAdd2Entities:"",
    secondNluIntent:"",
    secondNluScore:"",
    secondNluEntities:"",
    secondNluCostTime:"",
    flowTime:"",
    flowCostTime:"",
    flowHostName:"",
    flowFirstAppId:"",
    faqId:"",
    faqResult:"",
    botScore:"",
    agentScore:"",
    custCmt:"",
    custId:"",
    memo:"",
    state:""
};
```

### 參考三處模板FirstBot
![](https://i.imgur.com/HkaQVdl.png)



