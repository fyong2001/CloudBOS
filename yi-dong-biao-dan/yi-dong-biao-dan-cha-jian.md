---
description: 移动表单插件
---

# 移动表单插件

## 【插件基类】

![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551258157b3s08gqn4nu3unttu40gu64rujtjjnd3.png)

##  【插件注册】

![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551258380x355x06p3xzhppzio5pddw5dphy3dpyi.png)

## **【代码示例】**

  
1、字段取值、赋值：

```text
using Kingdee.BOS.Mobile.PlugIn;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace LKD.MobileDemoPlugins
{
    /// <summary>
    /// 移动表单插件
    /// </summary>
    public class MobileFormEdit : AbstractMobilePlugin
    {
        public override void AfterBindData(EventArgs e)
        {
            //单据头字段赋值
            this.View.Model.SetValue("F_LKD_Text","文本字段设置值");

            //单据头字段取值
            string strText = this.View.Model.GetValue("F_LKD_Text").ToString();

            //移动列表字段赋值
            int row = 0; //移动列表行索引，索引号从 0开始
            this.View.Model.SetValue("F_LKD_Text1", "文本字段设置值", row);

            //移动列表字段取值
            string strRowText = this.View.Model.GetValue("F_LKD_Text1", row).ToString();

            //移动列表新增行、并给字段赋值
            for (int i = 0; i < 5; i++)
            {
                this.View.Model.CreateNewEntryRow("F_LKD_MobileListViewEntity");
                int rowCount = this.View.Model.GetEntryRowCount("F_LKD_MobileListViewEntity");
                this.View.Model.SetValue("F_LKD_Text1", "F_LKD_Text1" + rowCount, rowCount);
                this.View.Model.SetValue("F_LKD_Integer", rowCount, rowCount);
            }
        }
    }
}
```

  
2、[控件属性设置代码示例](http://club.kingdee.com/forum.php?mod=viewthread&tid=1237879)

3、[移动列表行格式示例代码](http://club.kingdee.com/forum.php?mod=viewthread&tid=1407890)

4、[底部菜单属性设置代码示例](http://club.kingdee.com/forum.php?mod=viewthread&tid=1186906)

5、[调用移动端特性功能示例代码（定位、扫描等）](http://club.kingdee.com/forum.php?mod=viewthread&tid=1097311)

6、[移动BOS中如何响应点击发短信和打电话](http://club.kingdee.com/forum.php?mod=viewthread&tid=1323498)

7、[移动BOS中如何打开一个网页链接](http://club.kingdee.com/forum.php?mod=viewthread&tid=1095930)

