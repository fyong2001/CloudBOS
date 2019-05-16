# 移动开发如何本地调试

## 【浏览器打开登录】

浏览器（建议用谷歌浏览器：Chrome）地址栏输入（http://localhost/K3Cloud/mobile/index.aspx），打开H5登录界面。

![](https://club.kingdee.com/forum.php?mod=image&aid=256510&size=300x300&key=021a51a894d27a10&nocache=yes&type=fixnone)

## 【打开指定的移动界面】

修改地址栏的FormId、PageId和FormType的参数：  
      FormId=对应移动表单的唯一标识；  
      **PageId=;清空PageId的参数值。**  
      FormType=mobilelist：指打开移动单据列表；  
      Formtype=mobile\|mobileform：指打开移动表单或单据详情。

![](https://club.kingdee.com/forum.php?mod=image&aid=256509&size=300x300&key=68fd20a9a141a6ed&nocache=yes&type=fixnone)

![](https://club.kingdee.com/forum.php?mod=image&aid=256508&size=300x300&key=2eb4c043a7c5b649&nocache=yes&type=fixnone)

## 【到Visual Studio附件进程调试】

![](https://club.kingdee.com/forum.php?mod=image&aid=256507&size=300x300&key=687e2517aec2e821&nocache=yes&type=fixnone)

