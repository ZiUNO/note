# WeChatApp
## App(object) 注册一个小程序程序
### object 参数
| 属性 | 类型 | 功能 | 描述 |
|:---:|:---|:---|:---|
| onLaunch | function | 生命周期函数 | 监听小程序初始化 |
| onShow | function | 生命周期函数 | 监听小程序显示 |
| onHide | function | 生命周期函数 | 监听小程序的隐藏 |
| onError | function | 错误监听函数 | |
| onPageNotFound | function | 页面不存在监听函数 | |
| 自定义 |  |  | 自定义函数或数据 |
###### 示例代码:
```
App({
  onLaunch: function(options){

  },
  onShow: function(options){

  },
  onHide: function(){

  },
  onError: function(msg){
    console.log(msg)
  },
  globalData: '...'
  })
```
#### onLaunch, onShow 参数
| 字段 | 类型 | 功能 |
|:---|:---|:---|
| path | String | 打开小程序路径 |
| query | Object | 打开小程序的query |
| scene | Number | 打开小程序的场景值 |
| shareTicket | String |  |
| referrerInfo | Object | 当场景为由另一小程序打开时返回此字段 |
| referrerInfo.appId | String | 小程序AppId |
| referrerInfo.extraData | Object | 来源小程序传过来的数据 |
### getApp()
## Page(object) 注册一个页面
### object 参数
| 属性 | 类型 | 功能 | 描述 |
|:---|:---|:---|:---|
| data | object |  | 页面的初始数据(json) |
| onLoad | function | 生命周期函数 | 监听页面加载 |
| onReady | function | (同上) | 监听页面初次渲染成功 |
| onShow | function | (同上) | 监听页面显示 |
| onHide | function | (同上) | 监听页面隐藏 |
| onUnload | function | (同上) | 监听页面卸载 |
| onPullDownRefresh | function | 页面相关事件处理函数 | 监听用户下拉动作 |
| onReachBottom | function | 页面上拉触底事件的处理函数 |  |
| onShareAppMessage | function |  | 用户点击右上角转发 |
| onPageScroll | function | 页面滚动触发事件的处理函数 | 参数object:scrollTop:Number 页面在垂直方向已滚动的距离(px) |
| 自定义 | | | 自定义函数或数据 |
###### 示例代码
```
<view>{{text}}</view>
<button bindtap="eventHandler">press button</button>
```
```
Page({
  data:{
    text: '',
    form: 'json'
  },
  onLoad: function(options){

  },
  onReady: function(){

  },
  onShow: function(){

  },
  onHide: function(){

  },
  onUnload: function(){

  },
  onPullDownRefresh: function(){

  },
  onReachBottom: function(){

  },
  onShareAppMessage: function(){

  },
  onPageScroll: function(){

  },
  eventHandler: function(){
    this.setData({
      text: ''
      })
  },
  customData:{
    hi: 'ziuno'
  }
  })
```
## 事件
| 分类 | 功能 |
|:---|:---|
| 冒泡事件 | 当一个组件上的事件被触发后，该事件会向父节点传递 |
| 非冒泡事件 | 当一个组件上的事件被触发后，该事件不会向父节点传递 |
#### 冒泡事件
| 开头 | 功能 |
|:---:|:---:|
| bind | 不会阻止冒泡事件向上冒泡 |
| catch | 阻止冒泡事件向上冒泡 |

| 类型 | 触发条件 |
|:---:|:---:|
| touchstart | 手指触摸动作开始 |
| touchmove | 收纸触摸后移动 |
| touchcancel | 手机触摸动作被打断，如来电提醒，弹窗 |
| touchend | 手指触摸动作结束 |
| tap | 手指触摸后马上离开 |
| longtap | 手指触摸后,超过350ms在离开 |
