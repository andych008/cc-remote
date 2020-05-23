## cc-remote
cc-remote来源于[CC](https://github.com/luckybilly/CC)，实现了远程组件(跨app组件)的管理。

组件化框架如果要支持跨进程调用，就会涉及跨app组件的管理，主要是查找。怎么根据组件名定位到组件所在的进程（一般都是组件所在app的包名），是cc-remote要解决的问题。

### 原理
- cc-remote主要做了两件事：
1. 主动扫描设备上已安装的其它组件。
2. 被动监听其它组件的安装、卸载等。
最终cc-remote维护一个map，key为包名，value为该包名下的组件名列表。


- 我们约定组件app的特征就是包含一个Activity，其`<intent-filter>`下`action`为`"action.com.billy.cc.connection"`

