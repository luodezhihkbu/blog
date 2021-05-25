# CSS 知识总结

## 浏览器渲染原理

* 渲染步骤
  1. 根据html构建html树（DOM）;
  2. 根据css构建css树（CSSOM）；
  3. 将两棵树合并成一个渲染树（render tree）；
  4. 布局Layout：根据文档流，盒模型，计算大小和位置；
  5. 绘制Paint：把边框颜色，文字颜色、阴影等画出来；
  6. 合成Compose：根据层叠关系展示画面。
   
* 三种不同的渲染方式：
  
  ![渲染方式](images/render.jpg)

## CSS动画的两种做法

### 1. transform

transform有四个常用的功能：translate，scale，rotate和skew。

1）位移translate

常用的写法有

`translateX(length-percentage)`表示在X轴方向偏移某个长度；

`translateY(length-percentage)`表示在Y轴方向偏移某个长度。

2）缩放scale

常用的写法有

`scaleX(number)`表示按某个角度在X轴方向缩放；

`scaleY(number)`表示按某个角度在Y轴方向缩放。

3）旋转rotate

常用的写法有

`rotate(angle)`表示按某个角度在X轴方向旋转。

4）倾斜skew

常用的写法有

`skewX[angle]`表示按某个角度在X轴方向倾斜；

`skewX[angle]`表示按某个角度在Y轴方向倾斜。

transform可以组合使用，以达到多重效果。

transform一般会和transition搭配使用。transition是用来补充动画的中间帧。

### 2. animation

animation可以在动画里增加中间点。

首先需要用`@keyframes`声明关键帧，常用语法为下图的两种：

![@keyframes语法1](images/animation1.png)
![@keyframes语法2](images/animation2.png)

接着用`animation`添加动画。`animation`的语法为：
animation: 时长|过渡方式|延迟|次数|方向|填充模式|是否暂停|动画名;