## APP自动化

使用数据线将手机与电脑相连，使用开发者模式在电脑命令行输入  

    python -m uiautomator2 init

如果需要wifi连接 adb需要tcpip连接模式所以在数据线连接时我们需要设定端口  

    adb tcpip 5566
    adb connect ip:5566

    d = u2.connect("192.168.0.102:5566")

清除应用缓存：`adb shell pm clear com.gaotu100.tutu`  

### app可视化工具，快速编写AppUI自动化脚本
开启uiautodev：`python -m uiautodev`

查看手机已安装的包： `adb shell pm list packages`  

### monkey指令
1. -p参数：表示指定测试的程序（空格后面跟安装包名字，拿刚才的第三方安装包一个个试）

2. -v参数：表示查看monkey执行过程的信息（日志级别）（-v 越多越详细，最多三个）

3. 数字100:表示测试事件数为100

指定一个包 `adb shell monkey -p com.tencent.news -v -v -v 100` （此时指定软件会被打开并开始乱点乱按）  
指定多个包 `adb shell monkey -p com.tencent.news -p com.pdfreader -p com.widgets -v 1000`  
不指定包 `adb shell monkey -v 1000`  

保存日志到指定目录：

`adb shell monkey -p com.tencent.news -v -v -v 100 > d:\xxx.txt`  