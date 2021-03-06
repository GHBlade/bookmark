# 命名规则

####基本准则
![简单约定的命名方式](../img/android_name_1.jpg)
* **\<WHAT\>：**表示代表是什么资源，通常是一个标准的View类或者能代表View的类
* **\<WHERE\>：**表示属于app什么地方，在多个页面使用的资源用all，其他则对应页面名称自定义部分
* **\<DESCRIPTION\>：**区分同一界面的不同元素
* **\<SIZE\>：**描述大小的文字（可选）<br>
![命名示例](../img/android_name_2.png)

####Layout命名规则
![Layout命名规范](../img/android_name_3.png)<br>
其中<WHAT>可以是以下名称之一:<br>
* activity:activity的布局
* fragment:fragment的布局
* view:一个自定义view所要inflated的布局
* item:recyler或者gridview中使用的布局
* layout:include标签中用来重用的布局

**示例**

* activity_main: MainActivity的布局
* fragment_articledetail:  ArticleDetailFragment的布局
* view_menu: 被自定义view：MenuView所inflate的布局
* item_article: ArticleRecyclerView中的item
* layout_actionbar_backbutton:带有返回按钮的actionbar的布局

####String命名规则
![String的命名规范](../img/android_name_4.png)
当整个app都要使用这个string时：
![全局string](../img/android_name_5.png)

**示例**
* articledetail_title: ArticleDetailFragment的标题
* all_done: 通用的 "done" 字符

####Drawable命名规则
![Drawable的命名规范](../img/android_name_6.png)
当整个app都要使用这个drawable时：
![全局drawable](../img/android_name_7.png)
可以选择性的添加\<SIZE\>元素

**示例**
* articledetail_placeholder: placeholder in ArticleDetailFragment
* all_infoicon_24dp: 24dp version of generic info icon

####ID
![ID的命名规范](../img/android_name_8.png)

**示例**
* tablayout_main -> MainActivity中的TabLayout
* imageview_menu_profile -> 自定义MenuView中的profile image

(当然这里的imageview可以缩写为iv，textview可以缩写为tv等等)

####Dimension

app应该只定义一套数量有限的常用dimension，这个特性使得dimension一般都默认用all

常用：
![常用](../img/android_name_9.png)

偶尔：
![偶尔](../img/android_name_10.png)

通常除文字单位用sp以外,其余使用dp
