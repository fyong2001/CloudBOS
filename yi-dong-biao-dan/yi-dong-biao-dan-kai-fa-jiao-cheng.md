---
description: 本教程介绍全新创建一个移动表单，以及如果简单设计界面、编写插件、启动代码调试、及功能发布云之家。
---

# 移动表单开发教程

## **【简介】**  

本教程介绍全新创建一个移动表单，以及如果简单设计界面、编写插件、启动代码调试、及功能发布云之家。  
**阅读本教程前，您需要了解的知识：**  移动的基础知识、 BOS表单设计、 BOS插件开发

## **【新建移动表单】**  

新建移动表单步骤：打开BOSIDE -》 打开子系统 -》 新建移动表单。![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551252053i68486ojboe5c5o4584xbkc0z0b7k56l.png)![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551252138ijhjdt070c0t6phj3p6h87hd08kizc60.png)  


\*\*\*\*

## **【界面设计】**

\*\*\*\*

### 1、流式布局

添加一个流式布局，然后往布局里添加字段或控件，支持横向、纵向两种布局方向（注：增加内边距，整体界面看起来不会那么拥挤。）  
![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551254060n07k8w0o56pxyjn8jyxoz19pxp0b85p0.png)  


### 2、移动列表：

  
![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551256512u44p9ws8e8swepmlm4wc113lpzpw93s3.png)  
  


### 3、附件：

  
      [移动附件\_上传篇-6.0版本以上](http://club.kingdee.com/forum.php?mod=viewthread&tid=1147545)  
      [移动附件\_下载篇-6.0版本以上](http://club.kingdee.com/forum.php?mod=viewthread&tid=1147567)  
  


### 4、底部菜单：

**注：移动表单不支持绑定操作，要开发插件实现。**  
![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551257088dmt7n4mnun7e6a68xsa8w7zewwnz2m2n.png)  
  
  


## **【插件开发】**

### 1、移动表单插件基类

### ![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551258157b3s08gqn4nu3unttu40gu64rujtjjnd3.png)  2、插件注册 ![](http://clubimg.kingdee.com/club/attachments/forum/201902/27/1551258380x355x06p3xzhppzio5pddw5dphy3dpyi.png) 

## **【代码示例】**

  
1、字段取值、赋值：using Kingdee.BOS.Mobile.PlugIn;using System;using System.Collections.Generic;using System.Linq;using System.Text;using System.Threading.Tasks;  
namespace LKD.MobileDemoPlugins{    /// &lt;summary&gt;    /// 移动表单插件    /// &lt;/summary&gt;    public class MobileFormEdit : AbstractMobilePlugin    {        public override void AfterBindData\(EventArgs e\)        {            //单据头字段赋值            this.View.Model.SetValue\("F\_LKD\_Text","文本字段设置值"\);  
            //单据头字段取值            string strText = this.View.Model.GetValue\("F\_LKD\_Text"\).ToString\(\);  
            //移动列表字段赋值            int row = 0; //移动列表行索引，索引号从 0开始            this.View.Model.SetValue\("F\_LKD\_Text1", "文本字段设置值", row\);  
            //移动列表字段取值            string strRowText = this.View.Model.GetValue\("F\_LKD\_Text1", row\).ToString\(\);  
            //移动列表新增行、并给字段赋值            for \(int i = 0; i &lt; 5; i++\)            {                this.View.Model.CreateNewEntryRow\("F\_LKD\_MobileListViewEntity"\);                int rowCount = this.View.Model.GetEntryRowCount\("F\_LKD\_MobileListViewEntity"\);                this.View.Model.SetValue\("F\_LKD\_Text1", "F\_LKD\_Text1" + rowCount, rowCount\);                this.View.Model.SetValue\("F\_LKD\_Integer", rowCount, rowCount\);            }        }    }}  
2、[控件属性设置代码示例](http://club.kingdee.com/forum.php?mod=viewthread&tid=1237879)3、[移动列表行格式示例代码](http://club.kingdee.com/forum.php?mod=viewthread&tid=1407890)4、[底部菜单属性设置代码示例](http://club.kingdee.com/forum.php?mod=viewthread&tid=1186906)5、[调用移动端特性功能示例代码（定位、扫描等）](http://club.kingdee.com/forum.php?mod=viewthread&tid=1097311)6、[移动BOS中如何响应点击发短信和打电话](http://club.kingdee.com/forum.php?mod=viewthread&tid=1323498)7、[移动BOS中如何打开一个网页链接](http://club.kingdee.com/forum.php?mod=viewthread&tid=1095930)  


## **【开发调试】** 

 ****[移动开发如何本地调试](http://club.kingdee.com/forum.php?mod=viewthread&tid=1176706)

##  【其他参考】

1、[移动单据开发](http://club.kingdee.com/forum.php?mod=viewthread&tid=1270539&page=1#pid3548934)

2、[移动平台汇总贴](http://club.kingdee.com/forum.php?mod=viewthread&tid=1062364)

3、[零代码移动开发--移动智能录单](http://club.kingdee.com/forum.php?mod=viewthread&tid=1144830)

4、[移动单据设计开发（增加手势应用）](http://club.kingdee.com/forum.php?mod=viewthread&tid=1288822)

