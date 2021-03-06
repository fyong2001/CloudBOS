# Android App标签打印

 移动应用使用的方便性，  
越来越多的功能都希望移动客户端能够支持使用，  
移动端的硬件集成需求在逐步变的迫切，  
如已经实现的移动端蓝牙打印机的类似超时小票打印，  
还有一些新的需求，RFID卡的打卡集成处理（如在移动端链接打卡设备进行刷卡，就可以进行身份的确认单据的提交审批等）  
本帖子把移动端的新支持的功能斑马打印机标签打印做下分享。  
  
移动端的版本：Android客户端  
对应的补丁版本：7.0最新补丁，支持套打设置标签打印。  
6.0发布的最新补丁，支持持套打设置标签打印及直接斑马打印机指令打印。  
  
**Android客户端打印机链接设置（界面可能会有些出入，以实际的产品界面为准）**  
打印设置：  
![](http://clubimg.kingdee.com/club/attachments/forum/201709/25/1506308861jrrqbpjgpo0r90sedh5rqdsr69btieer.png)  
打开打印设置后，  
继续点开【标签打印设置】界面，如下  
  
分别支持“USB”“网络”“蓝牙”打印设置。  
链接方式：一般实际使用比较多，使用Android平板USB链接方式链接打印设备。  
USB打印设置：  
![](http://clubimg.kingdee.com/club/attachments/forum/201710/10/1507603431kt7vivi7t9mvz99jutuzm44g66cocoj4.png)  
设备ID：当通过USB方式链接好打印机，会识别出供选择的斑马打印机设备，也就是在设备ID中进行选择打印链接设备。  
字体库名称：一般打印机默认的字体库是不支持打印中文的，如需要打印中文可以选择打印机支持的中文字体库。  
分辨率：选择打印的分辨率。  
保存：保存数据。  
打印测试：相关信息设置好，成功保存之后，可以进行打印测试了。  
  
  
网络打印设置：  
![](http://clubimg.kingdee.com/club/attachments/forum/201710/10/1507603567or2f99w7kkwr91mbzk2w257w9z522272.png)  
IP地址：打印机所在IP地址Prot端口：打印机链接的端口号  
  
蓝牙打印设置：  
![](http://clubimg.kingdee.com/club/attachments/forum/201710/10/1507606024hq1j0umm30euhbnuube2o7qejh7kxjne.png)  
蓝牙设备：选择链接的蓝牙设备  
  
  
**服务端开发配置**  
  
配置：设置单据套打模板  
单据或基础资料 按斑马打印机纸张尺寸设置套打模板。  
  
开发：通过打印指令  
移动表单插件，可通过如下代码进行调用斑马打印机进行打印，  
  


1. //formId 业务对象Id pkValue 数据行主键 noteTemlatedId套打模板 
2. this.View.MobileNotePrint\(formId, pkValue, noteTemlatedId\); 
3. 
_复制代码_  
  
另：也提供了移动表单插件，直接调用斑马打印机指令代码。  
  
此做法一般是已有打印指令，每次打印前修改指令中的部分数据进行打印。  
比如条码指令，每次打印前修改条码指令的文字描述部分，以便每次打印出需要的不同条码。  


1. //直接打印指令 
2. this.View.MobileNotePrint\(command\);

_复制代码_  
**设置步骤：**  
如配置一个【物料】基础资料的 标签打印  
1、保证第一部分的斑马打印机设置能够链接成功。  
2、设置物料的套打打印模板。  
3、设置一张物料对应移动单据。  
4、在界面上的菜单关联打印控制代码。  
5、进行实际的打印。

