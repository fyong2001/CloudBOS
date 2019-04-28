---
description: 本教程介绍全新创建一个移动单据，以及如果简单设计界面、编写插件、启动代码调试、及功能发布云之家。
---

# 移动单据开发教程

## **【简介】**  

本教程介绍全新创建一个移动单据，以及如果简单设计界面、编写插件、启动代码调试、及功能发布云之家。  
**阅读本教程前，您需要了解的知识：**  移动的基础知识  BOS单据设计  BOS插件开发

##  **【新建移动单据】**  

新建移动单据步骤：打开BOSIDE -》 打开子系统 -》 新建移动单据。![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519959551ofpvzy4d4xyda1ecc5zu5cn1dx5u5n1j.png)![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519959869qo5axcc500ka6mafq4629m27ztr95xka.png)  


## **【选择来源单据】**

选择绑定来源单据，本示例用销售订单。

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519960249z60r6f00cbqe0gbzlcz4bpp5a0zk44pv.png)  


## **【单据列表】**

1、列表布局：参考下图步骤设置每行格式（**注：增加内边距，整体界面看起来不会那么拥挤。**）![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519961528j71n31oof7629s47ii6c6xs92uqio2c7.png)  
  
2、增加两个横向布局的流式布局，再从左边的字段树中把要在列表中展示字段（一般是单据头字段）选中，分别拖拽到列表页签的流式布局中  
![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519970302gcf0u0f6qyc3mcffqmmamp0hycoqp0to.png)  
  
3、如果需要分割线，可以添加一个高度为“1”、并设置背景色的流式布局作为分割线。![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519970792hkf8bik70d18sfd2tizfwp7k106sf0r0.png)  
4、底部菜单定义：选择单据列表（FList） -》定义“底部菜单集合” -》菜单的“点击事件”选择绑定新增操作。![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519971406s3r330z0h14303u33m3v3p5i5u0v38u3.png)  
  
5、列表行点击事件绑定：列表双击事件绑定修改操作（如果不需要编辑详情，则绑定查看操作），运行时点击打开单据详情界面。![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519971710rrmyor272m747u1o561zo17585u7rolm.png)  
6、实际运行效果![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519972777g9gze1ll1ewol1c8lllgpp1rblpcpzgg.png)  


## **【列表过滤】**[移动单据列表过滤示例](http://club.kingdee.com/forum.php?mod=viewthread&tid=1344069)

## **【单据详情】**

1、设计表头布局：添加一个流式布局，设置内边距，再往里添加表头显示字段，**注：表头的字段可以在详情界面编辑修改**。![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520240373t4zl9n8h9hl4n44ck246ypn2v42c9v92.png)![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520240290qtdp522t3wv5vtwtw4nh0l13ppwepz5a.png)  
2、添加移动代理分录，从左侧的树中选择分录，拖拽到单据页签，调整分录高度，并**设置每页显示行数**。![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520240783a6ozinb6sb6ouh6o00c0go4nos88sn0u.png)3、分录布局设计，选择分录要显示的字段，往移动代理分录添加流式布局，调整高宽，设置方向和内边距，在往布局里添加移动代理字段。如下图：![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520241470pvi08pvs0gx0bpe04ppixi4pbx0ppz94.png)  
4、设计单据菜单和操作，先添加底部菜单，再设置菜单集合，后绑定表单操作。![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520242348wdd9d7989d9h880cncr8yhy78y9hyrh9.png)![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520242434q9jd32ezgeeyy2oelqqq9qlq1q8qnejq.png)  
  
  
5、实际运行效果![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520243375mmomwfmm30oo7mvvwsvm7awm0wmom7w3.png)  
  


## **【移动分录新增、修改、删除】**

定义菜单移动分录操作菜单，并绑定操作。选中移动代理分录，属性栏中设置手势管理，弹出手势管理框，定义菜单并绑定操作，**注：分录行的编辑修改建议通过弹出分录编辑界面的形式实现**。  
1、新增分录按钮定义，新增分录操作绑定：![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520243242q3r7y40p7r43z0c0063x444i8p0bpcsz.png)2、修改、删除分录手势菜单定义和修改、删除分录操作绑定：![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520243001mh87we9h7pewyl7b7r8pb2x7xx9w7z1c.png)  
3、运行效果![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520243473zbtiw7ihcdccj74y5mym5tt6zzw7yi7i.png)

* **点击新增分录或修改菜单弹出分录编辑界面** 

![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520243547ybbob3bxjmduouuiiuomnsxucysytby0.png)\*\*\*\*

## **【移动单据分录字段设置】**

注：如果没有设置，则弹出的分录编辑框的字段和移动分录选择的字段一致  
1、菜单路径  
![](http://clubimg.kingdee.com/club/attachments/forum/201710/26/1508983630phiggxzugrr8ou8b0vzb0okfuz29u0nf.png)  
2、设置界面  
![](http://clubimg.kingdee.com/club/attachments/forum/201710/26/1508983758htdtssz3sz4hj2hw3uvh92s22jd93atw.png)  
3、运行效果  
![](http://clubimg.kingdee.com/club/attachments/forum/201710/26/1508983976sj49y9l1u9cuhjaz9kc1yujn9ynkjr49.png)  


## **【插件代码】**

1、插件项目要引用的组件

![](http://clubimg.kingdee.com/club/attachments/forum/201804/11/1523412510rg0eza2e7fs7ewhl2krklaskw14w14ee.png)



2、移动单据详情插件，移动单据插件要继承基类 AbstractMobileBillPlugin，移动单据插件的事件和PC端单据插件的事件基本一致  注：通过下图所示的代码获取和给来源单据的字段赋值

![](http://clubimg.kingdee.com/club/attachments/forum/201804/11/1523413332i2btzj8tvwxvb44d4qty4qyqsbgjb48v.png)

3、移动单据列表插件，移动单据列表插件要继承基类 AbstractMobileListPlugin

![](http://clubimg.kingdee.com/club/attachments/forum/201804/11/1523413688lcqu7w8ww0zhzme7cnuciwwqe7mn7q7u.png)

## **【绑定插件】**

  
插件注册和PC端的一样，如下图：

![](http://clubimg.kingdee.com/club/attachments/forum/201804/11/1523414378ohcba6aaaabsrb968ab9chhhafbfshza.png)

## **【发布移动主控台】**

  
  
[发布移动主控台](http://club.kingdee.com/forum.php?mod=viewthread&tid=1334748&page=1&extra=#pid3778567)  


## **【调试】**

\*\*\*\*[移动开发如何本地调试](http://club.kingdee.com/forum.php?mod=viewthread&tid=1176706) 

##  **【其他参考】**

  
****1、[移动表单开发](http://club.kingdee.com/forum.php?mod=viewthread&tid=1455980&page=1&extra=#pid4102909)2、[移动平台汇总贴](http://club.kingdee.com/forum.php?mod=viewthread&tid=1062364)3、[零代码移动开发--移动智能录单](http://club.kingdee.com/forum.php?mod=viewthread&tid=1144830)4、[移动单据设计开发（增加手势应用）](http://club.kingdee.com/forum.php?mod=viewthread&tid=1288822)  


