# FAQ議定格式

###### tags: `高鐵AI規劃`
:::info
FAQ特別處理轉換控制
:::



### 規格

目前僅處理 
* type 1  [文字]
* type 13 [牌卡]
* type 5  [圖]


### 文字處理
```json
[{
	type:1,
	text:"你好啊?我是FAQ哦"
}]
```


### 圖片處理
:::info
out 
* true = 使用外部連結
* false = 使用靜態資源

使用靜態資源檔的時候無須夾帶路徑直接給檔名 例如 hello.jpg
:::
```json
[{
	type:5,
	out: true,
	url:"路徑"
}]
```

### 牌卡處理
:::info
out

* true = 使用外部連結
* false = 使用靜態資源
:::

```json
[{
    type:13,
    data:[
        {
            title:"第一牌卡_第一顆按鈕",
            payload:"第一牌卡_第一顆按鈕",
        },
        {
            title:"第一牌卡_第二顆按鈕",
            payload:"第一牌卡_第二顆按鈕",
        },
        {
            title:"第一牌卡_第三顆按鈕",
            payload:"第一牌卡_第三顆按鈕",
        },
    ]
},{
    type:13,
    data:[
        {
            title:"第二牌卡_第一顆按鈕",
            payload:"第二牌卡_第一顆按鈕",
        },
        {
            title:"第二牌卡_第二顆按鈕",
            payload:"第二牌卡_第二顆按鈕",
        },
        {
            title:"第二牌卡_第三顆按鈕",
            payload:"第二牌卡_第三顆按鈕",
        },
    ]
}
]
```