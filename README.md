# wechat-qqmusic


项目预览：

   ![演示图片](snap/show.gif)

# 基础知识 #


## 视图 ##

普通视图, 头部的设置
```
<view class="header">
  <image src="../../img/logo.png" />
  <button class="download">下载APP</button>
</view>
```


```
/*通过宽度设置 100% 来铺满整个屏幕*/
.header {
    width: 100%;
    height: 44px;
    background: #31c27c;
    overflow: hidden;
}
```


### 滑块控件 ###

swiper 中滑块视图容器。


其中 wx:for 循环遍历数据


```


  <swiper indicator-dots="true" autoplay="true" interval="2000">
    <block wx:for="{{tuiData.slider}}">
      <swiper-item>
        <image src="{{item.picUrl}}" class="slide-image" />
      </swiper-item>
    </block>
  </swiper>
```


### 视图空间 ###

参考资料：
https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/list.html

```
wx:for
在组件上使用wx:for控制属性绑定一个数组，即可使用数组中各项的数据重复渲染该组件。

默认数组的当前项的下标变量名默认为index，数组当前项的变量名默认为item

<view wx:for="{{array}}">
  {{index}}: {{item.message}}
</view>
```



## 请求数据 ##

```
var that = this;
//推荐的请求
wx.request({
  url: tuiUrl,
  method: 'GET', 
  success: function(res){
    // success
    console.log(res);
    var resData = res.data.data;
    //因为当前的this不是指向的的Page,所以要使用that.
    that.setData({
      tuiData: resData
    });
  }
});

```
