# 第三方平台集成

1.      适用环境：7.x版本（2018年8月10号以后），6.x版本（2018年4月26号以后）；2.      路径：cloud后台，系统管理---第三方系统登录授权3.      配置：

![](http://clubimg.kingdee.com/club/attachments/forum/201805/02/1525232406tw0j13lhe3hytqwly0flwljy33hblowf.png)  
如图，所示，填写应用id，名称，以及集成用户（即对应的用户名称）；根据上述消息生成授权链接：  
![](http://clubimg.kingdee.com/club/attachments/forum/201808/27/1535362253l33ylc8kmy7cbztclmzlkmbyyde7bb8g.png)  
参考代码如下：



  


```text
namespace Kingdee.BOS.Mobile.FormPlugIns
{
    [Description("第三方授权登录")]
    public class TestLoginBySign : AbstractMobilePlugin
    {
        public override void AfterBindData(EventArgs e)
        {
            base.AfterBindData(e);
        }

        public override void AfterButtonClick(Core.DynamicForm.PlugIn.Args.AfterButtonClickEventArgs e)
        {
            base.AfterButtonClick(e);
            if (e.Key.EqualsIgnoreCase("FButton"))
            {
                string acctID = this.View.Model.GetValue("FAcctID").ToString();
                string username = this.View.Model.GetValue("FUserName").ToString();
                string appId = this.View.Model.GetValue("FAppID").ToString();
                string appSecret = this.View.Model.GetValue("FAppSecret").ToString();
                int lcId = 2052;
                //时间戳
                long timestamp = DateTimeFormatUtils.CurrentTimeMillis() / 1000;
                //签名
                string[] arr = new string[] { acctID, username, appId, appSecret, timestamp.ToString() };
                string sign = Kingdee.BOS.Util.SHA1Util.GetSignature(arr);
                //url
                string url = string.Format("http://localhost/k3cloud/mobile/k3cloudForPhone.html?acctid={0}&username={1}&appid={2}&sign={3}&timestamp={4}&lcid={5}&formid=BOS_MOB_ActivityEdit&formtype=mobileform", acctID, username, appId, sign, timestamp, lcId);
                this.View.GetControl("FUrl").SetValue(url);
                this.View.UpdateView("FUrl");
            }
        }
    }
}

如果是java环境没有获得签名的包；也可以自己够家里：
public class SHA1Util
    {
        /// <summary>
        /// SHA1签名
        /// </summary>
        /// <param name="arr"></param>
        /// <returns></returns>
        public static string GetSignature(string[] arr)
        {
            //1. 将数组进行排序
            //2. 将数组拼接成一个字符串进行sha1加密
            Array.Sort(arr, StringComparer.Ordinal);
            var arrString = string.Join("", arr);
            var sha1 = SHA1.Create();
            var sha1Arr = sha1.ComputeHash(Encoding.UTF8.GetBytes(arrString));
            StringBuilder enText = new StringBuilder();
            foreach (var b in sha1Arr)
            {
                enText.AppendFormat("{0:x2}", b);
            }

            return enText.ToString();
        }
    }
```





