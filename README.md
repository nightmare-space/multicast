# multicast

适用于 Dart 的局域网组播+广播实现的消息发送与接收。

## 使用的项目
- ADB TOOL
- 无界投屏
- 速享
## 已知问题

在 Android  热点，PC 端连接的情况，PC 端检测 Android 端 UDP 消息会有延迟，具体视局域网而定。
简单说，PC 端监听 Android 比 Android 端监听 PC 端的延迟要高 。

### 相关资料

目前设备的发现是通过**组播**加**广播**实现的。

在尝试了[multicast_dns](https://github.com/flutter/packages/tree/master/packages/multicast_dns)后，并没有调通实例代码。
这是躺坑过程中的资料：[https://github.com/flutter/flutter/issues/16335](https://github.com/flutter/flutter/issues/16335)

Android 默认关闭组播，意味着，局域网其他设备发送的组播消息，Android 设备无法收到，这个问题已经通过内部的 plugin 进行了解决，目前存在的问题是：
在 Android 设备打开热点，PC 端连接的情况，PC 设备收不到来自 Android 设备的组播消息，所以监听 UDP 的代码中，同时支持了组播与广播，发送 UDP 也同时将
消息发送到组播地址与广播地址中。
