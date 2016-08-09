---
title: '[c++] map vs unordered_map'
date: 2016-08-08 22:30:18
categories: Programming
tags: c++
---
****
### Difference between map and unordered_map

#### 1.去官网上查implemention的解释。

- map : Maps are typically implemented as **binary search**.
- unordered_map: unordered_map implement the direct access operator which allows for **direct access** of the mapped value using its key value as argument. (**Hashing**)

So, map will have the feathers of binary search, and unordered_map will match Hashing.

|                       | map            | unordered_map  |
| :-------------        | :------------- | :------------- |
|element ordering       | strict weak    | n/a            |
|common implementation  | binary tree    | hash table     |
|Insertion Time         |  log(n)        | O(1) no collisions|
|Search Time            | log(n)         | O(1)           |
|need hash function     | no             | yes            |
<br/>

#### 2. 什么时候该用哪一种map？

由于两种map的原理不同，所以用法的选择大概可以参照binary tree vs hash table。

我大概总结几条：

1. unordered_map have a big array and then additional memory for each array. So if you need to be memory-aware, use map.

2. If you need pure lookup-retrieval ,use unordered_map.

(剩下的点，将会在将来结合工作经验进来补充)

****  
