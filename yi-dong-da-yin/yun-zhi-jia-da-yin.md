# 云之家打印

1.      准备工作：确保打印机支持蓝牙，确保您的手机或其他智能设备蓝牙功能已开启；

2.      适用环境：7.3及以上版本,云之家10.0.0及以上版本；

3.      元素据及操作步骤示例： 

        ![](http://clubimg.kingdee.com/club/attachments/forum/201810/29/1540781862oiva2f9h79xovvb2w2v7xtxih29vvxtv.png)

4.      插件示例类：  
         ![](http://clubimg.kingdee.com/club/attachments/forum/201810/29/1540781894hze5lomwlhozklri6bobrox54ewwohoo.png)      ![](http://clubimg.kingdee.com/club/attachments/forum/201810/29/1540781907y6j6tb94i2ivx4iv8v72qimx9sbb2mrv.png)         ![](http://clubimg.kingdee.com/club/attachments/forum/201810/29/1540781955z23l6v29uoh1zktk9k9lkppol6zvnvb3.png)         ![](http://clubimg.kingdee.com/club/attachments/forum/201810/29/1540781982f0eswsmo03gmee3aj7gr39ezg67emmem.png)  
5.代码示例：

```text
[Description("云之家蓝牙打印测试")]
    public class TestPrint : AbstractMobilePlugin
    {
        public override voidAfterButtonClick(Core.DynamicForm.PlugIn.Args.AfterButtonClickEventArgs e)
        {
            base.AfterButtonClick(e);
            if (e.Key.EqualsIgnoreCase("FButtonGetDevices"))
            {
                JSONObject json = new JSONObject();
                this.View.AddAction("getDevices", json);
            }
            else if (e.Key.EqualsIgnoreCase("FButtonPrint"))
            {
                StringBuilder sb = new StringBuilder();
                sb.Append("<C><F>都市大厨房<BR></F></C>");
                sb.Append("名称　　　　　 单价 数量 金额<BR>");
                sb.Append("--------------------------------<BR>");
                sb.Append("饭　　　　　　 1.0    1  1.0<BR>");
                sb.Append("炒饭　　　　　 10.0   10 10.0<BR>");
                sb.Append("蛋炒饭　　　　 10.0   10 100.0<BR>");
                sb.Append("鸡蛋炒饭　　　 100.0  1  100.0<BR>");
                sb.Append("番茄蛋炒饭　　 1000.0 1   100.0<BR>");
                sb.Append("西红柿蛋炒饭　 1000.0 1   100.0<BR>");
                sb.Append("西红柿鸡蛋炒饭 100.0  10 100.0<BR>");
                sb.Append("备注：加辣<BR>");
                sb.Append("--------------------------------<BR>");
                sb.Append("<R>合计：xx.0元<BR></R>");
                sb.Append("送货地点：深圳市南山区xx路xx号<BR>");
                sb.Append("<B>联系电话：13812345678<BR></B>");
                sb.Append("订餐时间：2016-08-0808:08:08<BR>");
                sb.Append("<QR>http://www.yunzhijia.com</QR>");
                JSONObject json = new JSONObject();
                string deviceId = this.View.Model.GetValue("Fcombo").ToString();
               json.Put("deviceId", deviceId);
               json.Put("content", sb.ToString());
                this.View.AddAction("btPrint", json);
            }
        }

        /// <summary>
        /// 获取设备列表后回调事件，用以设置下拉列表；
        /// </summary>
        /// <param name="e"></param>
        public override void AfterGetDevices(JSONArray e)
        {
            // 组装状态下拉框列表
            ComboFieldEditor combo = this.View.GetControl<ComboFieldEditor>("FCombo");
            List<EnumItem> enumList = new List<EnumItem>();
            foreach (Dictionary<string, object> dict in e)
            {
                if (!dict.ContainsKey("name")) continue;
                EnumItem item = new EnumItem()
                {
                   EnumId = dict["deviceId"].ToString(),
                   Value = dict["deviceId"].ToString(),
                   Caption = new LocaleValue(dict["name"].ToString())
                };
               enumList.Add(item);
            }
            combo.SetComboItems(enumList);
            if (enumList.Count > 0)
            {
                this.View.Model.SetValue("FCombo", enumList[0].Value);
            }
            this.View.UpdateView("FCombo");
        }
}
```

6.打印效果：

![](http://clubimg.kingdee.com/club/attachments/forum/201810/29/1540782092vw3ce2vd963x963xz9t5ezr95e9rz6xl.png)

