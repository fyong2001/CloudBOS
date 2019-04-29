# 底部菜单插件开发

##  【插件中进行底部菜单的赋值】

        如何在插件中设置底部菜单栏呢，目前移动bos不支持对于某一个菜单项的处理，目前需要对于整个菜单控件进行赋值 场景如下：我们在界面上有个底部菜单，控件的key为FTabMenuField 

        简单说明：因为实在手机上，所以我们的底部菜单定义参考目前通用的做法，支持两级，因为也不建议第一级定义太多，那样会导致无法显示，一般一级三个已经够了，更多的放到二级菜单中去 

### 1、首先定义一个菜单列表，如下 

```text
List _tabMenuList = new List();
```

### 2、带子菜单的，添加一级菜单 

```text
BaseTabMenu tabMenuApproval = new BaseTabMenu();
tabMenuApproval.Id = "FApproval";
tabMenuApproval.Key = "FApproval";
tabMenuApproval.Value = "处理";
tabMenuApproval.Type = "view";//click表示此菜单就是直接点击的，如果是有子菜单的话，此处要设置成为view
_tabMenuList.Add(tabMenuApproval);
tabMenuApproval.sub_button = new List<BaseTabMenu>();
BaseTabMenu subTabMenu = new BaseTabMenu();
subTabMenu.Id = "FSubtest1";
subTabMenu.Key = "FSubtest1";
subTabMenu.Value = "Ftitle";
subTabMenu.Type = "click";
tabMenuApproval.sub_button.Add(subTabMenu);
```

### 3、直接一级菜单就是处理点击的

```text
BaseTabMenu tabMenuApproval = new BaseTabMenu();
tabMenuApproval.Id = "FCancel";
tabMenuApproval.Key = "FCancel";
tabMenuApproval.Value = "撤销";
tabMenuApproval.Type = "click";
_tabMenuList.Add(tabMenuApproval);
```

### 4、最后设置对应控件的菜单值 

```text
string value = BaseMenuManager.ParseToString(_tabMenuList);
this.View.GetControl("FTabMenuField").SetCustomPropertyValue("value", value);
```

##  【底部菜单属性设置代码示例】

### 1、设置底部菜单背景色 

#### 1）移动单据列表底部菜单样式设置插件代码：

```text
JSON.JSONObject style = new JSON.JSONObject();
style["FApproval"] = "background-color:#EF0000;";
this.View.GetControl("FList").SetCustomPropertyValue("bottomMenuStyle", style);
```

#### 2）移动表单底部菜单控件样式设置插件代码：

```text
JSON.JSONObject style = new JSON.JSONObject();
style["FB"] = "background-color:#EF0000;";
style["FB_a"] = "background-color:#00EF00;width:150px;";    //子菜单
this.View.GetControl("FTabMenuField").SetCustomPropertyValue("tabMenuStyle", style);
```

### 2、插件设置列表底部菜单

```text
List<BaseTabMenu> tabMenuList = new List<BaseTabMenu>();
BaseTabMenu tabMenuApproval1 = new BaseTabMenu();
tabMenuApproval1.Id = "FApproval";
tabMenuApproval1.Key = "FApproval";
tabMenuApproval1.Value = "批量审批";
tabMenuApproval1.Type = "click"; //按钮类型,view = 菜单，click = 按钮
string value = BaseMenuManager.ParseToString(tabMenuList);
this.View.GetControl("FList").SetCustomPropertyValue("bottomMenuValue", value);
```

### 3、插件设置底部菜单控件

```text
List<BaseTabMenu> tabMenuList = new List<BaseTabMenu>();
BaseTabMenu tabMenuApproval = new BaseTabMenu();
tabMenuApproval.Id = "FApproval";
tabMenuApproval.Key = "FApproval";
tabMenuApproval.Value = "任务处理";
tabMenuApproval.Type = "view"; //按钮类型,view = 菜单，click = 按钮
tabMenuApproval.sub_button = new List<BaseTabMenu>();   
BaseTabMenu tabMenuForward = new BaseTabMenu();
tabMenuForward.Id = "FForward";
tabMenuForward.Key = "FForward";
tabMenuForward.Value = "转发";
tabMenuForward.Type = "click"; //按钮类型,view = 菜单，click = 按钮
tabMenuApproval.sub_button.Add(tabMenuForward);
tabMenuList.Add(tabMenuApproval);
string value = BaseMenuManager.ParseToString(tabMenuList);
this.View.GetControl("FTabMenuField").SetCustomPropertyValue("value", value); 
```

