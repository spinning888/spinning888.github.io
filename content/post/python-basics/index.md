---
title: Python 学习笔记：列表推导式与字典
description: 几个让代码更简洁的 Python 写法
slug: python-basics
date: 2026-10-25
categories:
    - 编程语言
tags:
    - Python
---

## 列表推导式

把“循环 + append”写成一行：

```python
# 普通写法
squares = []
for i in range(10):
    squares.append(i * i)

# 列表推导式
squares = [i * i for i in range(10)]

# 带条件：只要偶数
evens = [i for i in range(10) if i % 2 == 0]
```

## 字典的常用操作

```python
scores = {"小明": 90, "小红": 95}

# 取值时给默认值，避免 KeyError
print(scores.get("小刚", 0))  # 0

# 遍历键和值
for name, score in scores.items():
    print(f"{name}: {score}")

# 字典推导式
passed = {k: v for k, v in scores.items() if v >= 60}
```

## 统计次数：Counter

```python
from collections import Counter

words = "the cat and the dog and the bird".split()
cnt = Counter(words)
print(cnt.most_common(2))  # [('the', 3), ('and', 2)]
```

## 小结

- 简单的循环构造列表，优先用推导式
- 取字典值用 `.get()` 更安全
- 计数用 `Counter`，不用自己写字典累加
