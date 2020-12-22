## 设备连接
+ 工具中手机屏幕显示有较大黑边，不能填满整个区域（如图所示）  
![black_edge](./black_edge.png ':size=240x460')  
请在手机“设置”-“显示”-“屏幕分辨率”中调为“WQHD”

+ MIUI 10+等部分手机无法连接  
请选择WeTest Java连接方式，分辨率设置为较低的数值，如720、640（分辨率较高会导致画面卡顿设置连接失败）。

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
python36 runner/run_probe.pyc -s ${deviceId} -r ./script -w 0 -b 0
``` 
``` bash
# 脚本模式
python36 runner/run_lyra.pyc -s ${deviceId} -r ${项目路径} -w 0 -b 0
``` 

    -s 参数为设备Id，可从adb devices查看，不添加该参数默认使用当前机器第一个设备  
    -r 参数为项目路径, 打包后默认为script