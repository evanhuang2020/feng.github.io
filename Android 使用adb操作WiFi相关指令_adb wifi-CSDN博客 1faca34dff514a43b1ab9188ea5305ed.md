# Android 使用adb操作WiFi相关指令_adb wifi-CSDN博客

Created: June 20, 2024 5:18 PM
Tags: Wi-Fi, adb
URL: https://blog.csdn.net/BOJUE01/article/details/136684847

没有系统原生设置应用又需要调试WiFi功能时，可以使用如下指令来验证WiFi相关功能

最常用的就是 svc wifi enable/disable，再使用wpa_supplicant/wpa_cli来验证，但对于AP功能就没办法验证了，其实Android有组很强大的shell指令集，包含各个方便，这里只记录下平时使用的WiFi相关指令

1、查看WiFi所有指令以及参数

```jsx
adb shell cmd wifi -h
```

2、打开关闭WLAN

```jsx
adb shell cmd wifi set-wifi-enabled enabled
```

```jsx
adb shell cmd wifi set-wifi-enabled disabled
```

3、扫描WiFi

```jsx
adb shell cmd wifi start-scan             //扫描
```

```jsx
adb shell cmd wifi list-scan-results    //查看扫描结果
```

4、连接WiFi

```jsx
adb shell cmd wifi connect-network TP-LINK_5G_0FE1 wpa2 12345678
```

<aside>
💡 //TP-LINK_5G_0FE1 连接WiFi名称

</aside>

<aside>
💡 //wpa2 加密方式

</aside>

<aside>
💡 //12345678 密码

</aside>

5、查看WiFi状态

```jsx
adb shell cmd wifi status
```

6、打开关闭热点

```jsx
adb shell cmd wifi start-softap ap_ssidxx wpa2 12345678 -b5
```

<aside>
💡 // ap_ssidxx  热点名称

</aside>

<aside>
💡 // wpa2 加密方式

</aside>

<aside>
💡 //12345678 密码

</aside>

<aside>
💡 //-b5 5G频段

</aside>

```jsx
adb shell cmd wifi stop-softap
```

其他可以指令可以使用adb shell cmd wifi -h查看，如果需要连接WiFi以外的相关指令可以使用adb shell cmd -l(小写L)