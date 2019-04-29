---
description: 介绍如何开发移动列表过滤表单。
---

# 单据列表过滤

## **【过滤界面设计】**

### 1、新增并设计列表过滤表单

![](http://clubimg.kingdee.com/club/attachments/forum/201903/06/1551854566cxz4boi5ii3kim2n7ioxii74ioz3dma7.png)

### **2、**如何新增设置表单请参考

{% page-ref page="../yi-dong-biao-dan/yi-dong-biao-dan-kai-fa-jiao-cheng.md" %}

## **【过滤界面插件】**

```text
using Kingdee.BOS.Mobile.PlugIn;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Kingdee.BOS.Util;
using Kingdee.BOS.Core.DynamicForm;
using Kingdee.BOS.Orm.DataEntity;

namespace LKD.MobileDemoPlugins
{
    public class POFilterEdit : AbstractMobilePlugin
    {
        //用于向移动单据列表传达过滤条件
        private FilterData _filterData = new FilterData();

        public override void ButtonClick(Kingdee.BOS.Core.DynamicForm.PlugIn.Args.ButtonClickEventArgs e)
        {
            if (e.Key == "FOK")
            {
                if (this.Model.GetValue("FBillNo") != null)
                {
                    _filterData.BillNo = this.Model.GetValue("FBillNo").ToString();
                }
                if (this.Model.GetValue("FDocumentStatus") != null)
                {
                    _filterData.DocumentStatus = this.Model.GetValue("FDocumentStatus").ToString();
                }
                if (this.Model.GetValue("FPurchaseOrgId") != null)
                {
                    _filterData.PurchaseOrgId = Convert.ToInt32(((DynamicObject)this.Model.GetValue("FPurchaseOrgId"))["Id"]);
                }
                if (this.Model.GetValue("FSupplierId") != null)
                {
                    _filterData.SupplierId = Convert.ToInt32(((DynamicObject)this.Model.GetValue("FSupplierId"))["Id"]);
                }

                //把过滤条件返回移动单据列表界面，并关闭当前过滤界面
                FormResult formResult = new FormResult(_filterData);
                this.View.ReturnToParentWindow(formResult);
                this.View.Close();
            }
            else if (e.Key == "FClose")
            {
                this.View.Close();
            }
        }
    }
}
```

## **【单据列表界面设计】**

![](http://clubimg.kingdee.com/club/attachments/forum/201903/06/1551869062c4f44rlirzymf5fyhl05hin7p10q57f5.png)

## **【单据列表插件】**

```text
using Kingdee.BOS.Mobile.PlugIn;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Kingdee.BOS.Util;
using Kingdee.BOS.Mobile;

namespace LKD.MobileDemoPlugins
{
    public class POBillTestList : AbstractMobileListPlugin
    {
        //用于接收从过滤界面返回的过滤条件
        private FilterData _filterData = null;

        public override void PrepareFilterParameter(Kingdee.BOS.Core.List.PlugIn.Args.FilterArgs e)
        {
            if (_filterData != null)
            {
                if (!string.IsNullOrWhiteSpace(_filterData.BillNo))
                {
                    e.AppendQueryFilter(string.Format("FBillNo like '%{0}%'", _filterData.BillNo));
                }
                if (!string.IsNullOrWhiteSpace(_filterData.DocumentStatus))
                {
                    e.AppendQueryFilter(string.Format("FDocumentStatus = '{0}'", _filterData.DocumentStatus));
                }
                if (_filterData.PurchaseOrgId > 0)
                {
                    e.AppendQueryFilter(string.Format("FPurchaseOrgId = {0}", _filterData.PurchaseOrgId));
                }
                if (_filterData.SupplierId > 0)
                {
                    e.AppendQueryFilter(string.Format("FSupplierId = {0}", _filterData.SupplierId));
                }
            }
        }

        public override void ButtonClick(Kingdee.BOS.Core.DynamicForm.PlugIn.Args.ButtonClickEventArgs e)
        {
            if (e.key.EqualsIgnoreCase("FFilter"))
            {
                MobileShowParameter param = new MobileShowParameter();
                param.FormId = "LKD_MOB_POFilter";
                param.OpenStyle.ShowType = Kingdee.BOS.Core.DynamicForm.ShowType.Floating; //浮动弹出窗
                param.SyncCallBackAction = false;

                this.View.ShowForm(param, new Action<Kingdee.BOS.Core.DynamicForm.FormResult>((res) =>
                {
                    if (res.ReturnData == null)
                    {
                        return;
                    }

                    _filterData = res.ReturnData as FilterData; //接收从过滤界面返回的过滤条件

                    this.View.Refresh(); //刷新列表，重新加载数据过滤条件才生效
                }));
            }
        }
    }    
    
```

## **【过滤条件类】**

```text
/// <summary>
    /// 自定义一个过滤条件类，用于单据列表和过滤界面之间传递过滤条件的值
    /// </summary>
    public class FilterData
    {
        public string BillNo { get; set; }

        public string DocumentStatus { get; set; }

        public int PurchaseOrgId { get; set; }

        public int SupplierId { get; set; }

    }
```

## **【其它参考】**

  
    [移动单据列表过滤示例](http://club.kingdee.com/forum.php?mod=viewthread&tid=1344069)  


