---
description: 介绍一些常用示例代码
---

# 移动BOS开发技巧

## 如何打开一个设计好的移动表单或者单据

        移动BOS开发技巧 -- 如何打开一个设计好的移动表单或者单据 在K/3 Cloud的移动BOS,我们可以看到在设计器中我们区分为移动表单核移动单据 下面我们就来看一下,我们如何用代码打开他们,我们以一个简单的场景为例: 我们在当前页面的一个按钮点击的时候,打开另外一个页面\(移动表单和移动单据列表\) 以下是打开移动表单的写法，如果要打开移动单据列表，只需要把 MobileShowParameter 换成 MobileListShowParameter即可：

```text
MobileShowParameter param = new MobileShowParameter();                
param.FormId = "你想打开的formid";
//也可以添加自定义的参数                
param.CustomParams.Add("key名", “value”);
//如果需要支持回调参考以下写法
param.SyncCallBackAction = false; 
this.View.ShowForm(param, new Action<FormResult>((res) =>{ 
     this.View.Refresh(); //刷新当前页面 
}));
```

## 如何打开一个网页链接

 1、  移动BOS,在今年的3月份的补丁中增加了对于OpenUrlWindow得支持

```text
JSONArray paras = new JSONArray();
JSONObject jo = new JSONObject();
jo["url"] = "
http://www.kingdee.com"; // 如果是本网站相对路径，就不要加http://
jo["title"] = "金蝶官网";
paras.Add(jo);
this.View.AddAction("openUrlWindow", paras);
```

2 、 我们再深入一点，如果openurlwindow里面我需要用到登陆页面信息，该如何获取呢  
       我们跳转前对于session进行了处理，在服务器端存储了session\["mobilecontext"\]存储了身份信息  
       就和我们日常写插件完全一致的。  
       一般呢，我们是推荐页面直接采用aspx作为载体

## 如何打开链接时传递自定义的参数

        如何在移动BOS中打开链接时传递自定义的参数，大家在云之家中使用移动BOS，如果使用了外部页面和移动页面的混合方式，一般跳转都是采用链接方式，那么如何传递自定义参数呢。看下面的url，这个是我们打开移动表单的url [http://localhost/k3cloud/mobile/k3cloud.html?entryrole=XT&appid=101091440&formId=test\_xiaogy&formType=mobile](http://localhost/k3cloud/mobile/k3cloud.html?entryrole=XT&appid=101091440&formId=test_xiaogy&formType=mobile) 我们的实现思路是：移动bos在url上固定了一个参数，用于自定义数据传输 A 首先如上的链接，我们可以修改为 [http://localhost/k3cloud/mobile/k3cloud.html?entryrole=XT&appid=101091440&formId=test\_xiaogy&formType=mobile&custparam=test](http://localhost/k3cloud/mobile/k3cloud.html?entryrole=XT&appid=101091440&formId=test_xiaogy&formType=mobile&custparam=test) 在参数中增加custparam=test，其中custparam是固定的，不能修改，test就是你爱传什么就传什么了 B 然后你再this.View.OpenParameter.GetCustomParameter\("custparam"\)，就可以获取到cusparam中的值了

## 控件属性设置代码示例

1、可见性设置 this.View.GetControl\("FButton"\).SetCustomPropertyValue\("visible", true\); 

2、锁定性设置 this.View.GetControl\("FDate"\).SetCustomPropertyValue\("disabled", true\); 

3、按钮、标签背景色设置 this.View.GetControl\("FButton"\).SetCustomPropertyValue\("backcolor", "115,208,241"\); 

4、按钮、标签字体颜色设置 this.View.GetControl\("FButton"\).SetCustomPropertyValue\("forecolor", "255,255,255"\); 

5、按钮、标签文本值设置 this.View.GetControl\("FLable"\).SetCustomPropertyValue\("value", "我是标签"\); 6、高度、宽度设置 this.View.GetControl\("FDocEntity"\).SetCustomPropertyValue\("height", 100\); this.View.GetControl\("FDocEntity"\).SetCustomPropertyValue\("width", 320\); 

7、设置页签控件的当前选中页签 this.View.GetControl\("FTab"\).SetCustomPropertyValue\("selectedIndex", 2\); 

8、设置控件背景图片 this.View.GetControl\("FButton"\).SetCustomPropertyValue\("backgroundurl", "img.png"\);

