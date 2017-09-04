## 0 所需基础知识
- HTML/CSS/JS
- 数据库操作
- jquery

## 1 基本操作
**操作流程:** 新建页面 - 添加布局 - 配置布局 - 在布局中添加组件 - 配置组件
### 1.1 新建页面
 在 URL 中的 `modify/` 后输入页面名即可新建页面
**例子:** 新建 quota_extract, detail_data 两个页面
```
http://10.12.1.228:8043/nmcweb/modify/quota_extract
http://10.12.1.228:8043/nmcweb/modify/detail_data
```
### 1.2 在页面中添加控件
点击 + 后进入开发界面
![](http://upload-images.jianshu.io/upload_images/3022282-b2bb1ecc53668842.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **开发界面: **
![](http://upload-images.jianshu.io/upload_images/3022282-500d9e8a7868a8f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  - **代码区: ** 编写代码
  - **控制区: ** **预览**: 执行代码区中的代码, 在预览去显示结果. **取消**: 直接退出开发界面, 之前的所有操作将清空. **保存**按钮: 根据控件类型, 将控件保存到数据库中. **布局类控件保存在 smc_layout 表中, 其它类型控件保存在 smc_component 表中**
  - **设置区: ** 配置控件名, 控件类型, 选择模版 

- **添加布局:** 布局控件是一个容器, 在里面可以按上述方式继续添加布局, 或者其他类型控件
![](http://upload-images.jianshu.io/upload_images/3022282-4d1df7b92ed4c1db.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/3022282-97df4bab4f23ffe6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2 数据库操作
### 2.1 smc_layout 和 smc_component表
- **smc_layout:** 在开发界面中点击保存后自动向表中插入数据
关键字段说明:
  * layout_id: 布局id, 存储布局控件中的 layout_id 变量的值, 格式为字符串
  * component_id: 存储布局控件中 layout_id + "_" + ids 变量的值, 格式为字符串
  * grid_id: 存储 ids 变量的值
  * init_params: 存储设置区-原始参数类型-初始化参数的值, 格式为 JSON 格式

- **smc_component:** 在开发界面中点击保存后自动向表中插入数据 
关键字段说明:
  * id: 组件 id, 和对应的 smc_layout 表中的 component_id 数据相同
  * name_cn: 存储组件名, 在设置区 - 原始参数类型 - 控件名称中设置
  * content(clob): 存储代码区的代码

- **插入数据例子:**  
**在布局控件的 option 中设置 layout_id 和 ids, ids为组件id**
![](http://upload-images.jianshu.io/upload_images/3022282-b23c3c2d67c601c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**当在布局下的组件中添加内容后, 点击保存, 将向数据库中插入数据**
![smc_layout](http://upload-images.jianshu.io/upload_images/3022282-d747d30a8707ff34.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![component_id](http://upload-images.jianshu.io/upload_images/3022282-83ad4cbebffc9244.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2.3 smc_sql 表
```
smc_sql(ID, NAME, NAME_CN, TYPE, SQL, PARAMS, DBSTR, STATUS, OPER_BY)
```
**插入数据例子:** 
```
insert into smc_sql (ID, NAME, NAME_CN, TYPE, SQL, PARAMS, DBSTR, STATUS, OPER_BY)
values ('hdGPRS01', null, 'GPRS上网结束到入库完毕时间', 
'json', '<CLOB>', '$queryDate$', 'nmcuser@nmcdesign230', '1', 'wangzhou');
```
关键字段说明:
  * id: 该条数据的查询条件
  * sql: SQL语句
  * params: SQL的绑定参数
  * dbstr: 目标数据库, 与项目目录下的 `config/application.properties` 文件中的配置有关
  * status: 数据生效标记, 1为有效, 0为无效

## 3 开发例子: 周报前台页面展示
### 3.1 周一周报内容及对应链接: 
- **capes直采二期省端采集时长:** http://10.12.1.228:8043/nmcweb/modify/capes2_time
- **指标抽取:** http://10.12.1.228:8043/nmcweb/modify/quota_extract
- **数据明细梳理:** http://10.12.1.228:8043/nmcweb/modify/detail_data

### 3.2 capes直采二期省端采集时长周报
- **使用控件类型:** 简单自动布局, HTML, Echart3图表, JavaScript
- **简单自动布局配置:** 
```
layout_id = "capes2_time"
```



### 3.3 指标抽取周报

### 3.4 数据明细梳理周报




## 4 Tips:
1. 后台执行 SQL 语句，SQL 中不能含有分号
