# 微信小程序：涂鸦

涂鸦小程序，可以在白板上画画，也可以选择涂鸦照片。可以自由修改画笔宽度、颜色。画画代码位于painting、涂鸦照片代码位于painting2

可以通过搜索 soso涂鸦 或者扫面下面的二维码体验效果。
![soso涂鸦](http://bmob-cdn-20716.b0.upaiyun.com/2019/02/22/09c84a5840cd995880c2505920574554.png)

由于考虑到canvas在小程序中层级最高，因此采用动态调整高度的方法显示底部调整栏。

为了解决涂鸦照片的橡皮擦不会破坏原图，采用先为canvas设置background，在保存时先保存绘制的效果，然后清空canvas先绘制原图，再绘制手绘结果图。（利用canvas输出图片背景可以透明的特性）


### 版本更新
* v1.2.3 采用曲线绘制，解决折线问题

* v1.2.2 新增荧光涂鸦（代码与普通涂鸦为同一页，入口页通过参数 `pageType` 进行区分， 主要实现代码参考小程序api`setShadow`）

* v1.2 新增像素涂鸦（根据原来的普通涂鸦改写而成，将`lineTo`改为`fillRect`）
  于18.2.24提交微信审核

* v1.1 修改图片来源路径，优化无权限提醒


### 兼容性/性能问题：

  ~~1、安卓下涂鸦稍微多一点就会存在卡顿现象，估计是由安卓端使用qq浏览器的x5内核所致，ios上表现正常。~~（1.2.3，采用曲线绘制的方法已解决）

  2、在开发者工具中动态修改画布高度的功能有问题，安卓、ios表现正常。
  
  3、开发者工具中修改完画笔宽度、颜色后会导致之前画的部分缺失，手机端正常。
  
  4、像素涂鸦中过快的移动可能会导致中间部分的涂鸦缺失，目前已上线的其他类似小程序中也存在同样问题 （18.2.24）

### 未来版本预计添加功能

* 新增黑板模式，模仿在黑板上写字
 > 感觉模仿粉笔的效果可能有点麻烦，想办法中

* 可以调整普通涂鸦、荧光涂鸦、像素涂鸦的画板颜色
 > 具体实现打算同图片涂鸦
 
* ~~半透明画笔~~
 > 1、 半透明在自由绘画时效果不好
