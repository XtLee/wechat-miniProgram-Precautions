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
