---
title: 二分查找：写对边界的套路
description: 搞清楚左闭右开区间，二分再也不写错
slug: binary-search
date: 2026-10-28
image: cover.jpg
math: true
categories:
    - 算法
tags:
    - 二分
    - C++
---

二分查找思路简单，但边界很容易写错。这篇笔记记录一个固定写法，背下来就不会出错。

## 核心思想

在**有序**数组里找第一个满足条件的位置。每次比较中间元素，排除一半的区间，所以时间复杂度是 $O(\log n)$。

长度为 $n$ 的区间，最多比较的次数是：

$$
\lceil \log_2 (n + 1) \rceil
$$

## 模板：左闭右开 `[l, r)`

找第一个 **大于等于** `x` 的位置（等价于 C++ 的 `lower_bound`）：

```cpp
int lower_bound(const vector<int>& a, int x) {
    int l = 0, r = a.size();      // 区间 [l, r)
    while (l < r) {
        int mid = l + (r - l) / 2; // 防止溢出
        if (a[mid] >= x) r = mid;  // 答案在左半边（含 mid）
        else l = mid + 1;          // 答案在右半边
    }
    return l; // l == r，就是答案
}
```

### 为什么这样写不会错

- 循环条件 `l < r`：区间为空时停止
- `r = mid` 而不是 `mid - 1`：因为右边界本来就是“开”的
- 最后 `l == r`，不需要再判断返回哪个

## 常见变形

| 需求 | 条件 |
| --- | --- |
| 第一个 `>= x` | `a[mid] >= x` |
| 第一个 `> x` | `a[mid] > x` |
| 最后一个 `<= x` | 第一个 `> x` 的位置减 1 |

## 练习题

- LeetCode 704. 二分查找
- LeetCode 35. 搜索插入位置
- LeetCode 34. 在排序数组中查找元素的第一个和最后一个位置
