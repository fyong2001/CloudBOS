---
description: 自定义分录详情
---

# 自定义分录详情

       由于标准的分录详情界面是所有移动单据公用的界面，对于没有特殊需求的移动单据是适用。但也存在有些特殊的移动单据，需要做个性化二开，这时如果去扩展修改标准的分录详情界面，那其他所有的移动单据都会受影响，所以7.3的PT134511\[7.3.1260.6\]补丁开始，支持自定义移动分录详情。开发请参考以下说明做二次开发。  
  


#### **【新建移动分录详情表单】**

  
如下图所示新建移动表单，**表单继承自“MOB\_EntryDetailBase”基类表单**  
![](https://vip.kingdee.com/download?fileName=0100b6f4e300f30140bf83a115a509bdb461.png)  
  


#### **【编写移动表单插件】**

  
插件必须继承**基类插件“EntryDetailBaseEdit”**，如下图示例代码：

```text
using Kingdee.BOS.Core.DynamicForm.PlugIn.Args;
using Kingdee.BOS.Core.List;
using Kingdee.BOS.Mobile.FormPlugIns.EntryDetails;
using Kingdee.BOS.Orm.DataEntity;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace LKD.MobileDemoPlugins
{
    /// <summary>
    /// 采购订单移动分录编辑界面插件
    /// </summary>
    public class SOEntryDetailTestEdit : EntryDetailBaseEdit
    {
        /// <summary>
        /// 填充分录编辑界面：处理移动分录编辑界面打开时，移动分录的数据填充到移动分录编辑界面对应字段
        /// </summary>
        protected override void FillEntryDetail()
        {
            base.FillEntryDetail();

            //物料赋值，FMaterialId 来源单据物料字段的唯一标识，F_LKD_MaterialId分录编辑界面物料字段的唯一标识
            var material = this.GetSourceFieldValue("FMaterialId") as DynamicObject;
            if (material != null)
            {
                var materialId = material["Id"];
                this.Model.SetItemValueByID("F_LKD_MaterialId", materialId, -1);
            }

            //单位赋值，FUnitID 来源单据单位字段的唯一标识，F_LKD_UnitID分录编辑界面单位字段的唯一标识
            var unit = this.GetSourceFieldValue("FUnitID") as DynamicObject;
            if (unit != null)
            {
                var unitlId = unit["Id"];
                this.Model.SetItemValueByID("F_LKD_UnitID", unitlId, -1);
            }

            //数量赋值,FQty 来源单据数量字段的唯一标识，F_LKD_Qty分录编辑界面数量字段的唯一标识
            var qty = this.GetSourceFieldValue("FQty");
            this.Model.SetValue("F_LKD_Qty", qty);

            //单价赋值,FTaxPrice 来源单据单价字段的唯一标识，F_LKD_TaxPrice分录编辑界面单价字段的唯一标识
            var taxPrice = this.GetSourceFieldValue("FTaxPrice");
            this.Model.SetValue("F_LKD_TaxPrice", taxPrice);
        }

        /// <summary>
        /// 返回移动分录：处理移动分录编辑界面点击确定时，移动分录编辑界面回填移动分录
        /// </summary>
        protected override void ReturnToProxyEntry()
        {
            base.ReturnToProxyEntry();

            //物料赋值，FMaterialId 来源单据物料字段的唯一标识，F_LKD_MaterialId分录编辑界面物料字段的唯一标识
            var material = this.Model.GetValue("F_LKD_MaterialId") as DynamicObject;
            if (material != null)
            {
                var materialId = material["Id"];
                this.SetSourceItemValueByID("FMaterialId", materialId);
            }

            //物料赋值，FUnitID 来源单据单位字段的唯一标识，F_LKD_UnitID分录编辑界面单位字段的唯一标识
            var unit = this.Model.GetValue("F_LKD_UnitID") as DynamicObject;
            if (unit != null)
            {
                var unitlId = unit["Id"];
                this.SetSourceItemValueByID("FUnitID", unitlId);
            }

            //数量赋值,FQty 来源单据数量字段的唯一标识，F_LKD_Qty分录编辑界面数量字段的唯一标识
            var qty = this.Model.GetValue("F_LKD_Qty");
            this.SetSourceFieldValue("FQty", qty);

            //单价赋值,FTaxPrice 来源单据单价字段的唯一标识，F_LKD_TaxPrice分录编辑界面单价字段的唯一标识
            var taxPrice = this.Model.GetValue("F_LKD_TaxPrice");
            this.SetSourceFieldValue("FTaxPrice", taxPrice);
        }        


        public override void BeforeF7Select(BeforeF7SelectEventArgs e)
        {
            if (e.FieldKey == "F_LKD_MaterialId") //分录编辑界面的物料字段
            {
                //获取来源单据对应基础资料的使用组织
                var orgId = this.GetSourceFieldUserOrgId("FMaterialId");
                if (orgId > 0)
                {
                    //设置基础资料使用组织内码
                    ((ListShowParameter)e.DynamicFormShowParameter).UseOrgId = orgId;
                }
            }

        }

    }

}
```

#### **【注册插件】**

注册上一步编写好的插件  
![](https://vip.kingdee.com/download?fileName=01008892589168274243babeb74826429273.png)  
  
  


#### **【设置自定义分录详情】**

  
如下图所示，选择分录详情表单（**选中“移动分录”，在属性栏中找到“分录详情”，点开属性编辑框，选中前面设计好的分录详情表单。**）  
![](https://vip.kingdee.com/download?fileName=0100fd137bbc69f2488385ad2636f7c47047.png)  
  
  


#### **【运行时效果】**

![](https://vip.kingdee.com/download?fileName=0100901b354593784e0abc3eef6420fe86ab.png)

