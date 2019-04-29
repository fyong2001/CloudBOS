---
description: 介绍全新创建一个移动单据，以及如果简单设计界面、编写插件、启动代码调试、及功能发布云之家。
---

# 移动单据设计

## **【新建移动单据】**  

新建移动单据步骤：打开BOSIDE -》 打开子系统 -》 新建移动单据。

![&#x521B;&#x5EFA;&#x79FB;&#x52A8;&#x5355;&#x636E;](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519959551ofpvzy4d4xyda1ecc5zu5cn1dx5u5n1j.png)

![&#x79FB;&#x52A8;&#x5355;&#x636E;&#x8BBE;&#x8BA1;&#x754C;&#x9762;](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519959869qo5axcc500ka6mafq4629m27ztr95xka.png)

## **【选择来源单据】**

选择绑定来源单据，本示例用销售订单。  


![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519960249z60r6f00cbqe0gbzlcz4bpp5a0zk44pv.png)

## **【单据列表】**

### 1、列表布局：

参考下图步骤设置每行格式（**注：增加内边距，整体界面看起来不会那么拥挤。**）

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519961528j71n31oof7629s47ii6c6xs92uqio2c7.png)

### 2、列表行布局

增加两个横向布局的流式布局，再从左边的字段树中把要在列表中展示字段（一般是单据头字段）选中，分别拖拽到列表页签的流式布局中

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519970302gcf0u0f6qyc3mcffqmmamp0hycoqp0to.png)

### 3、如果需要分割线：

可以添加一个高度为“1”、并设置背景色的流式布局作为分割线。

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519970792hkf8bik70d18sfd2tizfwp7k106sf0r0.png)

### 4、底部菜单定义：

选择单据列表（FList） -》定义“底部菜单集合” -》菜单的“点击事件”选择绑定新增操作。

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519971406s3r330z0h14303u33m3v3p5i5u0v38u3.png)

### 5、列表行点击事件绑定：

列表双击事件绑定修改操作（如果不需要编辑详情，则绑定查看操作），运行时点击打开单据详情界面。

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519971710rrmyor272m747u1o561zo17585u7rolm.png)

### 6、实际运行效果

![](http://clubimg.kingdee.com/club/attachments/forum/201803/02/1519972777g9gze1ll1ewol1c8lllgpp1rblpcpzgg.png)

## **【列表过滤】**

{% page-ref page="untitled.md" %}

## **【单据详情】**

### 1、设计表头布局：

添加一个流式布局，设置内边距，再往里添加表头显示字段，**注：表头的字段可以在详情界面编辑修改**。

![&#x8BBE;&#x7F6E;&#x6D41;&#x5F0F;&#x5E03;&#x5C40;&#x5185;&#x8FB9;&#x8DDD;](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520240373t4zl9n8h9hl4n44ck246ypn2v42c9v92.png)



![&#x8BBE;&#x7F6E;&#x5355;&#x636E;&#x5934;&#x5B57;&#x6BB5;](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520240290qtdp522t3wv5vtwtw4nh0l13ppwepz5a.png)



### 2、移动分录：

添加移动代理分录，从左侧的树中选择分录，拖拽到单据页签，调整分录高度，并**设置每页显示行数**。

![&#x6DFB;&#x52A0;&#x79FB;&#x52A8;&#x4EE3;&#x7406;&#x5206;&#x5F55;](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520240783a6ozinb6sb6ouh6o00c0go4nos88sn0u.png)

### 3、分录布局设计：

选择分录要显示的字段，往移动代理分录添加流式布局，调整高宽，设置方向和内边距，在往布局里添加移动代理字段。如下图：

![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520241470pvi08pvs0gx0bpe04ppixi4pbx0ppz94.png)

### 4、设计单据菜单和操作，

先添加底部菜单，再设置菜单集合，后绑定表单操作。

![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520242348wdd9d7989d9h880cncr8yhy78y9hyrh9.png)

![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520242434q9jd32ezgeeyy2oelqqq9qlq1q8qnejq.png)



### 5、实际运行效果

![](http://clubimg.kingdee.com/club/attachments/forum/201803/05/1520243375mmomwfmm30oo7mvvwsvm7awm0wmom7w3.png)

## **【移动分录】**

{% page-ref page="../yi-dong-dan-ju-lie-biao/dan-ju-fen-lu-xiang-qing.md" %}

{% page-ref page="../yi-dong-dan-ju-lie-biao/zi-ding-yi-fen-lu-xiang-qing.md" %}

## **【插件代码】**

{% page-ref page="yi-dong-dan-ju-lie-biao-cha-jian.md" %}

{% page-ref page="yi-dong-dan-ju-cha-jian.md" %}

## **【发布移动主控台】**

  
  
[发布移动主控台](http://club.kingdee.com/forum.php?mod=viewthread&tid=1334748&page=1&extra=#pid3778567)  


## **【调试】**

\*\*\*\*[移动开发如何本地调试](http://club.kingdee.com/forum.php?mod=viewthread&tid=1176706) 

##  **【其他参考】**

  
****1、[移动表单开发](http://club.kingdee.com/forum.php?mod=viewthread&tid=1455980&page=1&extra=#pid4102909)2、[移动平台汇总贴](http://club.kingdee.com/forum.php?mod=viewthread&tid=1062364)3、[零代码移动开发--移动智能录单](http://club.kingdee.com/forum.php?mod=viewthread&tid=1144830)4、[移动单据设计开发（增加手势应用）](http://club.kingdee.com/forum.php?mod=viewthread&tid=1288822)  


