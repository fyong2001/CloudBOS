# 发短信和打电话

移动BOS中能够点击一个按钮或者图片，给某个人发短信或者打电话了，并且自动填入电话号码呢 在移动BOS中做到这个很简单的，如何响应按钮我们就不罗嗦了，进入正题，在按钮响应事件中，加入以下代码 

1 、首先我们来看看如何打电话 

```text
JSONArray jsonArray = new JSONArray(); jsonArray.Add("13900000000"); //电话号码 
this.View.AddAction(JSAction.SendCall, jsonArray);
```

2 、再来看看如何发短信 

```text
JSONArray jsonArray = new JSONArray(); jsonArray.Add("13900000000"); 
this.View.AddAction(JSAction.SendSMS, jsonArray);
```



