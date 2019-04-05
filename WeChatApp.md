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
| touchmove | 手指触摸后移动 |
| touchcancel | 手机触摸动作被打断，如来电提醒，弹窗 |
| touchend | 手指触摸动作结束 |
| tap | 手指触摸后马上离开 |
| longtap | 手指触摸后,超过350ms在离开 |
## 基础组件
### 属性类型
| 类型 | 描述 |
|:---|:---|
| Boolean | 布尔 |
| Number | 数字 |
| String | 字符串 |
| Array | 数组 |
| Object | 对象 |
| EventHandler | 事件处理函数名 |
| 自定义 | 任意属性 |
### 共有属性类型
| 属性名 | 类型 | 描述 | 注解 |
|:---|:---|:---|:---|
| `id` | String | 组件的唯一标识 | 保持整个页面唯一 |
| `class` | String | 组件的样式类 | 在相应的wxss中定义的样式类 |
| `style` | String | 组件的内联样式 | 可以动态设置的内联样式 |
| `hidden` | Boolean | 组件是否显示 | 所有组件默认显示 |
| `data-*` | | 自定义属性 | 组件上触发事件时,会发送给事件处理函数 |
| `bind-*` `catch-*` | EventHandler | 组件的事件 | (是否为冒泡事件) |
## 地图 Map
| 属性名 | 类型 | 功能 |
|:---:|:---:|
| longitude | Number | 中心经度 |
| latitude | Number | 中心纬度 |
| scale | Number | 缩放级别,[5,18] (默认16) |
| markers | Array | 标记点 |
| polyline | Array | 路线 |
| circle | Array | 圆 |
| controls | Array | 控件 |
| include-points | Array | 缩放视野以包含所有给定的坐标点 |
| show-location | Boolean | 显示带有方向的当前定位点 |
| bindmarkertap | EventHandle | 点击标记点时触发 |
| bindcallouttap | EventHandle | 点击标记点对应的气泡时触发 |
| bindcontroltap | EventHandle | 点击控件时触发 |
| bindregionchange | EventHandle | 视野发生变化时触发 |
| bindtap | EventHandle | 点击地图时触发 |

## 动画 Animation
| 函数名 | 参数 | 功能 |
|:---:|:---:|:---:|
| export() | None | 导出动画队列 |
| step(object) | `number duration 持续时间` `string timingFunction 动画效果` `number delay 动画延迟时间` | 表示一组动画完成 |
| rotate(number angle) | angle [-180, 180] | 从原点顺时针旋转的角度 |
| scale(number sx, number sy) | sx x(y)轴缩放倍数, sy y轴缩放倍数 | 缩放 |
| skew(number ax, number ay) | ax 对X轴坐标倾斜的角度, ay 对Y轴坐标倾斜的角度 | 对X, Y 轴坐标继续进行倾斜 |
| trainslate(number tx, number ty ) | tx 当仅有该参数时表示在 X 轴偏移 tx(单位px), ty Y 轴平移的距离(单位为px) | 平移变换 |
| opacity(number value) | value 透明度，范围 0-1 | 设置透明度 |
| backgroundColor(string value) | value 颜色值 | 设置背景色 |
| width(number/string value) | 长度值，如果传入 number 则默认使用 px，可传入其他自定义单位的长度值 | 设置宽度 |
| height(number/string value) | | 设置高度 |
| left(number/string value) | | 设置left值 |
| right(number/string value) | | 设置right值 |
| top(number/string value) | | 设置 top 值 |
| bottom(number/string value) | | 设置 bottom 值 | 
