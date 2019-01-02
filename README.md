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
