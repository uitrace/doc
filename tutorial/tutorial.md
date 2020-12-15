## 场景模式
#### 案例下载
项目：[先游](https://gamer.qq.com/)，请先下载安装  
工程：[scene.uitrace.zip](https://raw.githubusercontent.com/uitrace/doc/gh-pages/tutorial/scene.uitrace.zip)

## 代码模式
#### 案例下载
项目：[榫接卯和](https://zhuimeng.qq.com/webplat/info/news_version3/36752/36753/36754/36777/36892/m21258/201809/760840.shtml)，请先下载安装，并提前登陆好微信  
工程：[script.uitrace.zip](https://raw.githubusercontent.com/uitrace/doc/gh-pages/tutorial/script.uitrace.zip)

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