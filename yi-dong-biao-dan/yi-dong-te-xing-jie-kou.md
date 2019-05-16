---
description: 扫码、地图、短信、电话等移动特性接口
---

# 移动特性接口

## 【二维码、条码扫描】

```text
//点击扫描二维码
public override void AfterButtonClick(AfterButtonClickEventArgs e)
{
    this.View.CodeScan(); //调用二维码、条码扫描
}        
//扫描结果返回，参数e为二维码、条码结果字符串
public override void AfterCodeScan(string e)
{
    this.Model.SetValue("FCode", e);
}
```

## 【移动客户端地图定位】

```text
public override void AfterButtonClick(AfterButtonClickEventArgs e)
{
    this.View.LocateMobileClient(LocationProvider.LBS_PROVIDER, true); //调用定位服务
}
//定位结果返回，参数e为位置信息
public override void AfterMobileClientLocated(MobileClientLocatedEventArgs e)
{
    //PlunInHelper.SaveSignInInfo(this.Context, e.Latitude, e.Longitude, e.Desc);
}
```

## 【发短信和打电话】

### 1 、首先我们来看看如何打电话 

```text
JSONArray jsonArray = new JSONArray(); jsonArray.Add("13900000000"); //电话号码 
this.View.AddAction(JSAction.SendCall, jsonArray);
```

### 2 、再来看看如何发短信 

```text
JSONArray jsonArray = new JSONArray(); jsonArray.Add("13900000000"); 
this.View.AddAction(JSAction.SendSMS, jsonArray);
```

## 4、发起云之家沟通 

```text
//单个用户发起沟通
JSONObject config = new JSONObject();
config.Put("openId", openIds[0]);
this.View.AddAction("chatWithXT", config);
//发起群聊
JSONObject config = new JSONObject();
config.Put("shareType", "1");
config.Put("text", "采购xxxxxx");
config.Put("appId", "10037");
config.Put("appName", "业务审批";
config.Put("ignore", new List<string>());
config.Put("selected", openIds);
this.View.AddAction("shareWithXT", config);
//获取openId接口：
UserXunTongServiceHelper.GetXunTongOpenIds(Context ctx, List<string> userIds);
```

