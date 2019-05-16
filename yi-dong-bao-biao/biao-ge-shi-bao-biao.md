# 表格式报表

 **总体介绍**  
**跟随着移动端的特性，移动报表同样主打精简、一目了然，所以不宜在移动端展示过多的数据。**  
目前移动报表包含了以下几个部分特性：  
**1. 支持数据源配置。**  
**2. 支持对数据进行过滤。**  
**3. 支持插件干预。**  
  
**逐步构建一张简单的移动SQL报表**  
1. 登陆BOS IDE\(K3 Cloud 集成开发平台\)  
2. 打开或新建一个子系统  
3. 新建移动表单  
![&#x65B0;&#x5EFA;&#x79FB;&#x52A8;&#x8868;&#x5355;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201611/24/135447xtb3y0kbn0tnpe3t.jpg)   
4. 添加过滤面板  
![&#x6DFB;&#x52A0;&#x8FC7;&#x6EE4;&#x9762;&#x677F;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201611/24/135446qmh1rvemak5qla4a.jpg)   
5. 添加表格字段  
![&#x6DFB;&#x52A0;&#x8868;&#x683C;&#x5B57;&#x6BB5;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201611/24/135446scoz7og4zgtyb0l0.jpg)   
6. 设置SQL语句及关键字，**注意选择正确的SQL脚本类型**，推荐使用**KSQL**  
图中练习测试的SQL语句：

1. Select T.Fuserid,T.Fname,T.Fdescription From T\_SEC\_USER T 
2. Where T.FName like '%\#FName\#%'

_复制代码_![&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x6E90;&#x548C;&#x5173;&#x952E;&#x5B57;&#x7EF4;&#x62A4;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/133304u0y3j400wwx3fngg.jpg)   
7. 数据列格式化  
![&#x6570;&#x636E;&#x683C;&#x5F0F;&#x5316;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/133304m59hndfemu975nuy.jpg)   
8. 设置汇总字段 （在页脚显示指定列的汇总合并）  
![&#x8BBE;&#x7F6E;&#x6C47;&#x603B;&#x5B57;&#x6BB5;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/133304ungm7zcggfgkmmgc.jpg)   
9. 设置合并字段 （如果该字段存在相邻单元格内容相同则自动合并上下单元格）  
![&#x8BBE;&#x7F6E;&#x5408;&#x5E76;&#x5B57;&#x6BB5;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/133304fcilqdpz5lq6lt5s.jpg)   
10. 完成后会自动生成过滤控件，我们可以进行布局调整  
![&#x8C03;&#x6574;&#x8FC7;&#x6EE4;&#x9762;&#x677F;&#x5E03;&#x5C40;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201611/24/135447vhyxu77y7nno2gnq.jpg)   
至此，一张简单的移动SQL报表已完成，你可以进行发布然后运行查看效果。  
  
**【扩展】构建一张简单的移动业务对象报表**  
1. 登陆BOS IDE\(K3 Cloud 集成开发平台\)  
2. 打开或新建一个子系统  
3. 新建移动表单  
4. 添加表格字段（**注意：业务对象报表暂不支持过滤条件**）  
5. 选择业务对象（选择后会在左侧树控件解析业务对象的具体字段列表，所以可能会有短暂的卡顿）  
![&#x4E1A;&#x52A1;&#x5BF9;&#x8C61;&#x914D;&#x7F6E;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/110718fbiaq2j2ypv8zcpl.jpg)   
6. 设置排序字段  
![&#x8BBE;&#x7F6E;&#x6392;&#x5E8F;&#x5B57;&#x6BB5;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/110718bbvvx9g06a9h4zp0.jpg)   
7. 设置固定过滤条件  
![&#x8BBE;&#x7F6E;&#x56FA;&#x5B9A;&#x8FC7;&#x6EE4;&#x6761;&#x4EF6;.jpg](https://clubimg.kingdee.com/club/attachments/forum/201711/23/110718jptyo73ddd3oxdol.jpg)   
至此，一张简单的移动业务对象报表已完成，你可以进行发布然后运行查看效果。  
  
**参考文档链接**  
★[【分享】移动文档下载中心](http://3g.k3cloud.kingdee.com/m/doc_dowload.htm)  
★[【分享】移动开发如何本地调试](http://club.kingdee.com/forum.php?mod=viewthread&tid=1176706)  
★[【分享】移动报表系列-总览](http://club.kingdee.com/forum.php?mod=viewthread&tid=1283914&extra=)  
★[【分享】移动报表系列-进阶篇](http://club.kingdee.com/forum.php?mod=viewthread&tid=1284130&page=1&extra=#pid3598757)

