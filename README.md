# wechat miniProgram Precautions
1、scroll-view元素中fixed元素在滚动时会产生抖动。 
解决方法：将fixed元素与scroll-view元素放置到同一层级

2、switch滑块样式控制。 
/** 滑块选择时背景大小 **/
.wx-switch-input { 
  width: 90rpx !important;
  height: 50rpx !important;
}
/** 滑块大小 **/
.wx-switch-input::before {
  width: 96rpx !important;
  height: 50rpx !important;
}
/** 滑块小圆点大小 **/
.wx-switch-input::after {
  width: 50rpx !important;
  height: 50rpx !important;
}

3、canvas生成图片大小是根据当前canvas大小来设定的，如果canvas的高度是不固定的，最好在一开始就设置好canvas的高度，否则生成的图片可能会被拉伸；

4、控制多行文本超出显示省略号：
/** 块级元素内多个行内元素/多行文本 **/
.line {
 text-overflow:ellipsis;
 overflow:hidden;
 display:-webkit-box; /** 必要 **/
 -webkit-line-clamp:2; /** 这个数字是设置要显示省略号的行数 **/
 -webkit-box-orient:vertical;
}

5、text组件使用三元运算控制style的color字段无效，默认选择false结果。可将色值提前设置为变量引用。

6、IOS在new Date()时，只支持传入[年，月-1，日]格式。在Date.parse()的时候，不支持直接传输日期字符串，需转换为标准UTC格式。

7、小程序使用textarea组件时，回车展示为\r\n，但是在浏览器内有时会展示为\n。

8、小程序使用TS时会报`Cannot find global type 'CallableFunction' `和`Cannot find global type 'NewableFunction' `。解决办法为到`node_modules`路径下的`TypeScript`包的`bin`目录下，`lib.es5.d.ts`文件里面把这两个类型的`Interface`拷贝到，小程序`typing`目录下的`lib.wa.es6.d.ts`里面。

9、IOS不支持`display: flow-root;`可用`overflow: hidden;`产生BFC；

10、IOS上有时网络图片加修饰后图片加载失败，可在图片组件的`binderror`里将图片地址更新一次；

11、在`setData`时，key和value相同时，对value进行任何操作都会导致编译错误。解决方式为value不要和key重名，使用其他名称或者加上`this`的前缀；

12、微信小程序不支持`text-align: justify-all;`属性。文本两端对齐的最好解决办法为：将文本拆分为单独的块，使用flex布局解决；

13、微信小程序单行文本两端对齐支持：`display: inline-block; width: 120rpx; text-align: justify; text-align-last: justify;` 这种写法。

14、微信小程序阻止页面滚动可以监听`catchtouchmove`事件。必须要给一个空方法，不然会报错；

15、自定义组件生命周期触发除了一开始页面载入时，使用`wx:if`控制显示隐藏时也会触发；

16、安卓在后台时，无法调用wx.reLaunch()，只能通过在页面onShow时进行判断跳转；
