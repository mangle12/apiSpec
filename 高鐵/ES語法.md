# ES語法
###### tags: `教育訓練文件`



ES 調整對話
```
curl -XPUT "http://10.0.31.184:9200/.flow-report/stats/f0e50683b41ad638c2c8.312b4362139c" -H 'Content-Type: application/json' -d'{
    "fields": [
        {
            "id": "appId",
            "display_name": "App ID",
            "es_path": "appId_str",
            "type": "string",
            "is_filter": false,
            "is_display_field": false
        },
        {
            "id": "startTime",
            "display_name": "start time",
            "es_path": "started_at_str",
            "type": "date",
            "is_filter": true,
            "is_display_field": true
        },
        {
            "id": "time",
            "display_name": "End Time",
            "es_path": "finished_at_str",
            "type": "date",
            "is_filter": false,
            "is_display_field": true
        },
        {
            "id": "sessionId",
            "display_name": "Session ID",
            "es_path": "id_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": false
        },        
        {
            "id": "messages",
            "display_name": "summary",
            "es_path": "messages_nested_list.info_dict.payload_str",
            "type": "string",
            "is_filter": false,
            "is_display_field": false,
            "customRenderUrl" : "http://10.0.31.185:8080/ChatWeb/chatLogByReport"
        },        
        {
            "id": "chatLog",
            "display_name": "message",
            "es_path": "messages_nested_list.info_dict.payload_dict.msg_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": false
        },
        {
            "id": "agentId",
            "display_name": "agent id",
            "es_path": "info_dict.stateVariables_dict.agent_id_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": true
        },
        {
            "id": "channel",
            "display_name": "channel",
            "es_path": "info_dict.stateVariables_dict.channel_str",
            "type": "string",
            "is_filter": false,
            "is_display_field": false
        },
        {
            "id": "botScore",
            "display_name": "bot score",
            "es_path": "info_dict.stateVariables_dict.rank_score_bot_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": true
        },
        {
            "id": "agentScore",
            "display_name": "agent score",
            "es_path": "info_dict.stateVariables_dict.rank_score_agent_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": true
        },
        {
            "id": "customerComment",
            "display_name": "customer comment",
            "es_path": "info_dict.stateVariables_dict.customer_comment_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": true
        },
        {
            "id": "agentComment",
            "display_name": "agent comment",
            "es_path": "info_dict.stateVariables_dict.agent_comment_str",
            "type": "string",
            "is_filter": true,
            "is_display_field": true
        }
    ],
    "message_render_mode": "server"
}'


```