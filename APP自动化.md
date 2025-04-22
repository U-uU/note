## APP自动化

使用数据线将手机与电脑相连，使用开发者模式在电脑命令行输入  

    python -m uiautomator2 init

如果需要wifi连接 adb需要tcpip连接模式所以在数据线连接时我们需要设定端口  

    adb tcpip 5566
    adb connect ip:5566

    d = u2.connect("192.168.0.102:5566")

清除应用缓存：`adb shell pm clear com.gaotu100.tutu`  

开启uiautodev：`python -m uiautodev`