# 学习笔记

###分辨率与适配
* 屏幕尺寸：设备的物理屏幕尺寸，指屏幕的对角线的长度，单位是英寸，1 inch = 2.54 cm。比如某某手机为“5寸大屏手机”，就是指对角线的尺寸，5寸×2.54厘米/寸=12.7厘米
* 屏幕分辨率：也叫显示分辨率，是屏幕图像的精密度，是指屏幕或者显示器所能显示的像素点有多少。一般以横向像素×纵向像素表示分辨率，如1200×1920表示此屏幕在宽度方向有1200个像素，在高度方向有1920个像素
* 屏幕密度：屏幕密度是指每英寸上的像素点数，单位是dpi(dot per inch)或者ppi(pixels per inch)。顾名思义，就是每英寸的像素点数，数值越高当然显示越细腻。屏幕密度与屏幕尺寸和屏幕分辨率有关。例如在屏幕尺寸一定的条件下，屏幕分辨率越高屏幕密度越大，反之越小。同理在屏幕分辨率一定的条件下，屏幕尺寸越小屏幕密度越大，反之越小

* 一般的开发的话，都会做三套配图，对应着drawable-hdpi、drawable-xhdpi、drawable-xxhdpi三个文件夹，做一套也是可以的，放在drawable-xxdpi文件夹中



* 在布局文件中，如果只是为了占位，可以用 Space 来取代 View，可以跳过绘制的过程
* ContextThemeWrapper 方便在运行过程中更改主题
* getWindow().setLayout(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT);设置全屏方法一定要在setContentView之后
* viewpager 的 setCurrentItem 一定要在 setAdapter 方法之后调用才会有效果
* TextUtils 是一个非常好用的工具类，把 List 转成字符串，逗号分隔，逗号分隔的 String 字符串，切割成 List ，分别可以用 TextUtils 的 join 和 split 方法。如果要对 List 去重，则可以用 Collection 的 frequency 方法


* [命名规范](./name.md)