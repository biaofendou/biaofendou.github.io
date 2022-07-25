title: APP操作的adb命令
tags:
- adb
- Appium
- 测试

categories:
- 测试

description: <center><h3>adb命令主要用于控制安卓端设备</h3></center>

photo: https://biaofendou.github.io/images/photos/Cg-4V1S_EOWIMyUCAAhG5zFfIHUAATsVQNFKM0ACEb_770.jpg

---
<!--more-->

# APP操作的adb命令

### 1.启动App命令

- adb shell am start -W -n package/activity

>  获取包名和activity名
>
> adb logcat | grep START

- 返回参数ThisTime就是APP启动时间

### 2.APP关闭命令

* adb shell am force-stop package/activity

### 3.APP后台关闭方式

- adb shell input keyevent 3