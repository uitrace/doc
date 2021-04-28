## 设备连接
+ 工具中手机屏幕显示有较大黑边，不能填满整个区域（如图所示）  
![black_edge](./black_edge.png ':size=240x460')  
请在手机“设置”-“显示”-“屏幕分辨率”中调为“WQHD”

+ MIUI 10+等部分手机无法连接  
请选择WeTest Java连接方式，分辨率设置为较低的数值，如720、640（分辨率较高会导致画面卡顿设置连接失败）

## 设备操作
+ 部分手机无法通过工具操控手机  
设置->开发者选项->打开安全设置（允许通过USB调试修改权限或模拟点击）

## 常见错误
+ （查看->工具日志）cloudscreen run over, return value:255  
请选择WeTest Java连接方式，分辨率设置为较低的数值，如720、640（分辨率较高会导致画面卡顿设置连接失败）  

+ （查看->工具日志）Failed to load dynlib/dll '*.dll'. Most probably this dynlib/dll was not found when the application was frozen.  
打开关于->环境检测，查看各项是否已安装  
尝试以管理员权限运行（部分电脑普通用户权限较低，无法访问所需资源）  

+ （运行输出）设备默认屏幕分辨率被修改，请复查  
部分手机不是默认分辨率，使用adb shell wm size查看 
输出中的Physical size表示设备默认分辨率   
如果输出Override size则表示默认分辨率被修改  
可用adb shell wm size 1440x2960重置（1440x2960为Physical size）

+ 脚本中使用inputChineseText输入中文时无效或出现乱码  
检查WeTest输入法是否安装并启用  
Wetest输入法路径为程序根目录下：/resources/app/uitraverse/etcv/android/driver/libs/ime/WeTestIME.apk

+ 使用ai_monkey后导航栏被隐藏  
执行 adb shell settings put global policy_control null

+ 自动弹出开关控制设置指南
执行 adb shell settings put secure enabled_accessibility_services 0 

+ 执行adb命令出现java.lang.SecurityException: Permission denial
方法一：在开发者选项里，打开“USB调试（安全设置）”选项，允许USB调试修改权限或模拟点击
方法二：在开发者选项里，打开“禁止权限监控”选项。

## 执行
+ 如何用命令行运行脚本
> Windows

    从工具菜单栏 查看-> 工具配置 进入 config目录，上层目录为uitraverse，该目录下有app.exe。在该目录下执行以下命令
``` powershell
# 场景模式
app.exe run_probe -s ${deviceId} -r ${项目路径}
``` 
``` powershell
# 脚本模式
app.exe run_lyra -s ${deviceId} -r ${项目路径}
```

    -s  参数为设备Id，可从adb devices查看，不添加该参数默认使用当前机器第一个设备  
    -r  参数为项目文件夹路径
> Linux

    先使用UI版本导出脚本功能导出可在Linux上执行的脚本
    请自行在你的Linux主机上安装python3.6.8，然后再安装以下依赖库。你可以通过一些环境管理方案来管理你的python环境，例如virtualenv
``` 
环境配置：python3.6.8
依 赖 库：
certifi==2020.4.5.1
chardet==3.0.4
idna==2.8
lxml==4.5.0
msgpack==0.6.1
msgpack-numpy==0.4.4.3
numpy==1.18.2
opencv-python==4.2.0.34
opencv-contrib-python==3.4.2.17
Pillow==7.1.1
pyzmq==18.0.1
requests==2.21.0
requests-toolbelt==0.9.1
urllib3==1.24.3
PCV==1.0
```
```
    运行时先解压从工具中打包出的脚本文件。
    解压后目录为以下结构：
    .
    ├── adaptation
    ├── config
    ├── etcv
    ├── probe
    ├── runner
    ├── script
    ├── statics
    ├── thirdparty
    ├── runTest.sh
    └── endTest.sh
    在该文件夹根目录下运行runTest.sh, 或者执行以下命令。
```
``` bash
# 场景模式
python36 runner/run_probe.pyc -s ${deviceId} -r ./script
``` 
``` bash
# 脚本模式
python36 runner/run_lyra.pyc -s ${deviceId} -r ${项目路径}
``` 

    -s 参数为设备Id，可从adb devices查看，不添加该参数默认使用当前机器第一个设备  
    -r 参数为项目路径, 打包后默认为script