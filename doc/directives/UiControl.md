# UiControl

## Table of Contents



## 总体逻辑

客户端在每个请求中上报当前界面的上下文，包括***可能需要语音控制的所有元素***，服务端如果识别出语音请求和里面的某一项匹配，就返回Click指令，包含对应项目的url字段


## 上报UiControl状态

在[请求](../api/request.md)中的device_status字段

```javascript
"device_status":{
    "UiControl":{
        "items":[
              {"label":"下一个","url:"xxapp://next"},
              {"label":"暂停”,url:"xxapp://pause"},
              {"label":”停止”,url:"xxapp://stop"},
        ],
    },
},
```

## UiControl.Click指令

在[响应](../api/response.md)中的directives字段中的一项

```javascript
{
       "header": {
            "namespace":  "UiControl",
            "name":  "Click",
            "message_id": "message_id-1344"
        },
        "payload": {
            "url":"xxapp://next"
        }
}
```

## UiControl.Clicked 事件

用户执行Click指令之后，需要上传Clicked Event

在[请求](../api/request.md)中的device_event字段

```javascript
{
    "device_event":{
        "header": {
            "namespace":  "UiControl",
            "name":  "Clicked",
            "message_id": "message_id-1344"
        },
        "payload": {
            "url":"xxapp://next"
        }
    }
}
```
