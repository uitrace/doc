## 场景模式
#### 案例下载
项目：[先游](https://gamer.qq.com/)，请先下载安装  
工程：[scene.uitrace.zip](https://raw.githubusercontent.com/uitrace/doc/gh-pages/tutorial/scene.uitrace.zip)

## 代码模式
#### 案例下载
项目：[榫接卯和](https://zhuimeng.qq.com/webplat/info/news_version3/36752/36753/36754/36777/36892/m21258/201809/760840.shtml)，请先下载安装，并提前登陆好微信  
工程：[script.uitrace.zip](https://raw.githubusercontent.com/uitrace/doc/gh-pages/tutorial/script.uitrace.zip)

## 常用API
#### 点击元素
+ <a target="_blank">click(locator, xOffset=0, yOffset=0, by=0, **kwargs)</a>
+ <a target="_blank">doubleClick(locator, xOffset=0, yOffset=0, by=0, **kwargs)</a>
+ <a target="_blank">longClick(locator, longClickTime=1, xOffset=0, yOffset=0, by=0, **kwargs)</a>
+ <a target="_blank">click_text(text_str, pic=None, xOffset=0, yOffset=0, **kwargs)</a>
+ <a target="_blank">clickUiObject(locator)</a>
+ <a target="_blank">clickVanish(locator, timeOut=0, xOffset=0, yOffset=0, by=0, raiseException=0, **kwargs)</a>

``` python
# 常用点击示例

# 点击图片 
click(locator='****.jpg', xOffset=0, yOffset=0, by=DriverType.CV, timeOut=20)
# 点击控件
click(locator='/text="同意并使用" && type="android.widget.TextView"', xOffset=0, yOffset=0, by=DriverType.UIAUTOMATOR, timeOut=20)
clickUiObject('/text="同意并使用" && type="android.widget.TextView"')
# 点击文字
click(locator='同意并使用', xOffset=0, yOffset=0, by=DriverType.OCR, timeOut=20)
click_text('同意并使用')
```

#### 查找元素
+ <a target="_blank">find(locator, by=0, **kwargs)</a>
+ <a target="_blank">find_text(text_str, pic=None, **kwargs)</a>
+ <a target="_blank">ai_find(img_name, pos=None, offset=[0, 0], time_out=0, similarity=0.7, ratio_lv=21, pos_weight=0.05)</a>
+ <a target="_blank">super_find(uia = "", img_name = "", pos = None, uia_timeout = 20, img_timeout = 10, similarity = 0.7, ratio_lv = 21, pos_weight = 0.05)</a>

``` python
# 常用查找元素示例

# 点击图片 
result_pos = find(locator='****.jpg', xOffset=0, yOffset=0, by=DriverType.CV, timeOut=20)
if result_pos is not None:
    print(result_pos)
result, pos = ai_find('****.jpg', pos=None, offset=[0, 0], time_out=0, similarity=0.7, ratio_lv=21, pos_weight=0.05)
if result:
    print(pos)
# 查找控件
result_pos = find(locator='/text="同意并使用" && type="android.widget.TextView"', xOffset=0, yOffset=0, by=DriverType.UIAUTOMATOR, timeOut=20)
if result_pos is not None:
    print(result_pos)
# 查找文字
result_pos = find(locator='同意并使用', xOffset=0, yOffset=0, by=DriverType.OCR, timeOut=20)
if result_pos is not None:
    print(result_pos)
result_pos = find_text('同意并使用')
if result_pos is not None:
    print(result_pos)

# 综合查找(优先基于控件定位，找不到则基于图像及坐标（坐标不为空时）或仅基于图像（坐标为空时）定位)
result, result_type = super_find(uia = '/text="同意并使用" && type="android.widget.TextView"', img_name = '****.jpg', pos = (0.1, 0.5), uia_timeout = 20, img_timeout = 10, similarity = 0.7, ratio_lv = 21, pos_weight = 0.05)
if result is not None:
    print(result)
    print(result_type)
```

#### 滑动元素
+ <a target="_blank">slide(locatorFrom, locatorTo, by=0, **kwargs)</a>
+ <a target="_blank">slideOffset(locator, xOffset=0, yOffset=0, by=0, **kwargs)</a>
+ <a target="_blank">swipe(locator, referencePicture='', **kwargs)</a>

``` python
# 常用滑动屏幕示例

# 根据坐标滑动 
slide((0.244, 0.348), (0.662, 0.362))
# 根据图像滑动
slideOffset('****.jpg', xOffset=-0.005, yOffset=0.159, by=DriverType.CV)
# 根据控件滑动
slideOffset('/text="同意并使用" && type="android.widget.TextView"', xOffset=-0.005, yOffset=0.159, by=DriverType.UIAUTOMATOR)
# 根据文字滑动
slideOffset('同意并使用', xOffset=-0.005, yOffset=0.159, by=DriverType.OCR)
```

#### 等待元素
+ <a target="_blank">wait(locator, timeOut=0, by=0, **kwargs)</a>
+ <a target="_blank">waitVanish(locator, timeOut=0, by=0, **kwargs)</a>

``` python
# 等待元素示例

# 在指定的时间等待图像出现 
wait('****.jpg', timeOut=20, by=DriverType.CV)
# 在指定的时间等待控件出现 
wait('/text="同意并使用" && type="android.widget.TextView"', timeOut=20, by=DriverType.UIAUTOMATOR)
# 在指定的时间等待文字出现 
wait('同意并使用', timeOut=20, by=DriverType.OCR)

# 在指定的时间等待元素消失 
waitVanish('****.jpg', timeOut=20, by=DriverType.CV)
# 在指定的时间等待控件出现 
waitVanish('/text="同意并使用" && type="android.widget.TextView"', timeOut=20, by=DriverType.UIAUTOMATOR)
# 在指定的时间等待文字出现 
waitVanish('同意并使用', timeOut=20, by=DriverType.OCR)
```


#### 智能Monkey
+ <a target="_blank">ai_monkey(pkg=None, explore_type=0, timeout=-1, pre_exec=None, web_check=True, keyboard_check=True, restart_interval=900, other_data=[], qq_data=[], wechat_data=[])</a>
+ <a target="_blank">stop_monkey(ai_key)</a>

#### 账号相关
+ <a target="_blank">qqLogin(acc='', pwd='', **kwargs)</a>
+ <a target="_blank">wechatLogin(acc='', pwd='', **kwargs)</a>
+ <a target="_blank">playWithQQFriends(locator=None, acc='', pwd='', timeOut=240, **kwargs)</a>
+ <a target="_blank">playWithWeChatFriends(locator=None, acc='', pwd='', timeOut=180, **kwargs)</a>

#### 设备相关
+ getDevice()
+ getImage(subRect=None, quality=None)
+ getText(locator, referencePicture='', by=1, **kwargs)
+ getUiObjectTree()
+ ratio_transfer(pt)
+ win_transfer(pt)(pt)
+ screencap(subRect=None, quality=None)
+ script_dir()
+ setDevice(dev)
+ shell(cmd)
+ shell_noshow(cmd)

## 平台使用
#### 终端云测
请使用工具中导出-终端云测，直接导出脚本并上传到平台使用。  
![logo](./package.jpg ':size=122x175')   
+ 功能测试  
强烈建议使用**代码模式**开发脚本：由于终端云测功能测试需要以pytest、unittest形式解析并执行用例，目前UITrace仅代码模式支持在工程内以pytest、unittest形式编写脚本。  
编写示例：

```
    工程目录如下，重点关注test_simple.py及script.py：
    .
    ├── log
    ├── monitor
    ├── pic
    ├── trace
    ├── userlib
    │   └── test_simple.py
    ├── script.py
    ├── script.ini
    └── data.json
```

```python
# -*- coding: UTF-8 -*-
# script.py

import pytest

# pytest原生main运行
pytest.main([os.path.join(os.path.dirname(__file__), "userlib", "test_simple.py")])
pytest.main([os.path.join(os.path.dirname(__file__), "userlib", "test_simple.py::test_2")])

# API运行，本地执行时会运行传入的用例，在终端云测的功能测试运行时，会执行功能测试中选择的用例
print('pytest用例: 运行test_simple.py中所有用例')
pytest_main([os.path.join(os.path.dirname(__file__), "userlib", "test_simple.py")])
print('pytest用例: 运行test_simple.py中的用例test_2')
pytest_main([os.path.join(os.path.dirname(__file__), "userlib", "test_simple.py::test_2")])
```

```python
# -*- coding: UTF-8 -*-
# test_simple.py

import pytest

try:
    from runner.extapi import *
except:
    print("cannot import module runner")

@pytest.fixture(scope='function')
def test_1():
    print("test_1")

def test_2():
    print("test_2")
```

+ 兼容适配
场景模式、代码模式皆支持，正常导出提交即可。

#### [旧版云测](https://wetest.qq.com/console/cloud?menu=autotest)
请使用工具中导出-旧版云测，直接导出脚本并上传到平台使用（平台选择上传脚本-UI自动化）。

#### 通用平台
私有版本，请使用工具中导出-通用平台，直接导出脚本并上传到平台使用。