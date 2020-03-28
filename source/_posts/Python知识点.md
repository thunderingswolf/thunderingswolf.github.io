---
title: Python知识点
date: 2019-09-04 10:20:11
categories:
- 技术
tags:
- 技术
- Python
---



Python知识点

```
1. __init__.py 作用：将文件夹变为一个Python模块,Python 中的每个模块的包中，都有__init__.py 文件。
2. Python入口main函数：
在一个.py文件中，如果不是在定义函数，也就是说不是在def关键字的内嵌结构内，python会默认其余部分函数是main函数，并自动执行。但正规工程中，一般都会将main函数写为：if __name__ == __main__
3. setup.py 作用：发布源码包，相关配置
4. Blinker库：Blinker是一个基于Python的强大的信号库，支持一对一、一对多的订阅发布模式，支持发送任意大小的数据等等，且线程安全。
5. Pycharm下配置Virtualenv：先创建Virtualenv，再为项目分配
6. py.test 使用：pytest是python的一种单元测试框架，与python自带的unittest测试框架类似，但是比unittest框架使用起来更简洁，效率更高。
	pip install -U pytest
	切换测试文件test_sample所在的目录下，运行py.test即可。pytest会在当前的目录下，寻找以test开头的文件（即测试文件），找到测试文件之后，进入到测试文件中寻找test_开头的测试函数并执行。
7. pytest、tox、关系：http://jhshi.me/2016/10/04/python-testing-using-pytest-tox-travis-ci-and-coverall/index.html#.XW8u2HUzZFQ
8. pytest运行执行用例：pytest -v test_pytest_markers.py::TestClass::test_method
9. Flask修改端口配置：pycharm下，通过configuration配置 --host=127.0.0.1 --port=5000 （add option）
10. six python作用:它是一个专门用来兼容 Python 2 和 Python 3 的库
11. pytest.fixture 作用:高级测试环境的准备，灵活可配置 》setup与teardown

```



