[toc]

# 基础语法

## 字符串

### 字符串格式化

#### f-string

```python
f"{<var>:<spec>}"
```



[f-string 竟然能有 73 个例子，我要学习下 (qq.com)](https://mp.weixin.qq.com/s/x06toCJRWu87QEsQGEpIDg)

## 模块和包

### 包 

一个包含 `__init__.py `的文件夹就是一个包

### 模块

一个拓展名为 `.py` 的文件就成为一个模块

```Python
import <module_name> [as alias]
from <module_name> import <member> # 导入指定的变量、函数、类 后导入的同名变量、函数或类会覆盖先导入的
```

导入模块时，会按照以下顺序进行查找，`sys.path` 存储了所以查找的目录

1. 当前目录
2. PYTHONPATH 环境变量对应的路径
3. Python 的安装目录

每个模块都有一个记录模块名称的变量 `__name__`，如果一个模块不是因被导入而执行，而是直接被执行的，那么它的 `__name__` 为 `__main__`

`help('modules')` 可以查看当前可使用的模块

# 进阶使用

## 正则表达式

## 爬虫

### request 库

## 图像处理 

### Pillow

[Pillow — Pillow (PIL Fork) 9.1.1 documentation](https://pillow.readthedocs.io/en/stable/index.html)

### OpenCV

[opencv-python · PyPI](https://pypi.org/project/opencv-python/)

[OpenCV: OpenCV modules](https://docs.opencv.org/4.x/)

### OCR-pytesseract

[pytesseract · PyPI](https://pypi.org/project/pytesseract/)

## 辅助工具

### 进度条

tqdm

[tqdm documentation](https://tqdm.github.io/)

https://github.com/tqdm/tqdm

### 命令行参数解析

fire



