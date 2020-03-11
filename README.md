# README

### 云直播微信小程序SDK版本
* 日期：2020年03月10日
* 版本：1.4.1

### 版本兼容
* 微信开发工具：建议使用 1.02.1912261 及以上版本
* 调试基础库：建议使用 2.10.3 及以上版本，最低兼容2.0.1
* 微信：建议使用 7.0.11 及以上版本，最低兼容微信客户端6.7.2 及以上版本

### 小程序服务器域名配置
登陆微信公众平台小程序开发平台 - 开发 - 开发设置 - 服务器域名 - 配置服务器信息

request合法域名
```
https://eva.csslcloud.net
https://report.csslcloud.net
https://view.csslcloud.net
https://zeus.csslcloud.net
```

socket合法域名
```
wss://io-cc1.csslcloud.net
wss://io-cc2.csslcloud.net
wss://sio-1.csslcloud.net
wss://sio-2.csslcloud.net
wss://sio-3.csslcloud.net
wss://sio-4.csslcloud.net
wss://sio-7.csslcloud.net
```

downloadFile合法域名
```
https://image.csslcloud.net
```
### ccsdk_demo使用方法
* WXCCLive小程序插件是CC云直播提供的小程序SDK，使用此插件可以快速实现与CC云直播对接。
* ccsdk_demo 是通过WXCCLive插件实现的直播推流、观看直播、观看回放的demo。
* 使用demo需要用户配置 ccsdk_demo/project.config.json appid字段，添加自己的appid。
* 添加配置WXCCLive插件后就可以运行使用ccsdk_demo，并参考demo进行二次开发。

1. 推流sdk插件快速使用详见 doc/云直播微信小程序推流SDK开发指南.html
2. 播放sdk插件快速使用详见 doc/云直播微信小程序播放SDK开发指南.html
3. 回放sdk插件快速使用详见 doc/云直播微信小程序回放SDK开发指南.html

### ccsdk_demo目录结构
* components/（自定组件）
    *     img/（静态资源）
    *     live/（观看直播相关自定义组件）
    *     publisher/（推流相关自定义组件）
    *     replay/（观看回放相关自定组件）
* pages/
    *     index/（入口文件）
    *     live/（观看直播页面）
    *     publisher/（直播推流页面）
    *     replay/（观看回放页面）

### 自定义组件使用说明
* 自定义组件封装在ccsdk_demo/components文件下,用户可以直接复制并使用，components/img有所有的UI资源。
* 微信小程序ccsdk_demo中使用了WXCCLive插件，为了便于全局使用，直接在小程序app.js中引用了插件，并且赋值给globalData。
* 尽量避免修改ccsdk_demo/components自定义组件中的内容，可以适当增加和优化，避免减少。因为WXCCLive插件依赖自定义组件提供的部分事件和数据。
* 如果用户需要的功能自定义组件已经封装，推荐使用封装好的自定义组件，否则可能会导致某些功能异常。

### 事件、方法生命周期和调用触发监听时机
* 方法：ccsdk插件提供的大多数方法除一些配置方法外，需要在登录成功以后才能正常调用，大多数方法调用成功返回true，调用失败返回false。
* 事件：
    * 微信小程序插件1.3.0版本开始，对事件监听进行了优化，只要监听就会得到数据。
    * 无需考虑监听时机和监听位置，登录前监听还是登录后监听，都会接收到返回的事件参数，并且只接收一次事件参数的事件不会重复返回。
    * 一般在登录过程中，返回给相应的监听对应的数据，数据有自己的返回周期，如果错过这个时机，会在监听时，立即返回。
    * WXCCLive插件中，任何事件只能监听一次，如果重复监听，最后一次监听有效。

### 更新记录和升级文档

详见: doc/升级文档 vX.X.X (20XX-XX-XX).html

### Q&A

#### 观看直播视频、回放视频、推流视频出现无法播放黑屏等异常
如果出现视频异常或者黑屏，请参考文档配置或者对照微信小程序demo。检查是否在微信公众平台 - 开发 - 接口设置中开启了实时播放音视频流、实时录制音视频流权限或手机是否开启了视频和音频的权限。

检查手机是否允许了微信小程序视频，音频权限。

微信小程序观看直播、观看回放需要在真机中进行观看，微信小程序开发者工具中黑屏。

#### 微信小程序开发这工具调试
由于微信小程序开发者工具中部分组件在真机中表现不一致，在使用微信小程序开发者工具配置demo时，建议使用真机机型调试。

#### 登录异常
如果出现登录异常或socket连接异常等问题，建议首先排查网络，尝试切换4G或wifi进行调试。

#### Error: 登录用户不是该小程序的开发者
检查微信小程序 ccsdk_demo/project.config.json appid字段值是否改为自己的appid。如："appid": "开发者自己的appid"。

#### 登录微信公众平台添加WXCCLive插件
使用ccsdk_demo必须添加WXCCLive微信小程序插件。
登录微信公众平台 - 设置 - 第三方设置 - 添加插件中搜索 WXCCLive，添加后和客服确认审核即可使用。


