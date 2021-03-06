---
title: "欧拉回路"
linkTitle: "欧拉回路"
type: blog
weight: 8
date: 2021-10-18
description: >
  兜兜转转总是你……
---

# 欧拉回路

## 前置知识

图 $G$ 中恰好经过所有边一次(不可重复经过)的通路称作欧拉通路，恰好经过所有边一次的回路称作欧拉回路。

具有欧拉回路的图称为欧拉图，具有欧拉通路但不具有欧拉回路的图称为半欧拉图。

**存在欧拉通路的充要条件：**

- **无向图：** 各点连通，没有或仅有两个奇度结点。(偶度保证一入一出，两个奇度可以作为起止节点)
- **有向图：** 各点连通，有一个点出度 = 入度 +1，有一个点入度 = 出度 +1，其余点入度 = 出度。(入度出度相同保证一入一出，其余两点为起止节点)

**存在欧拉回路的充要条件：**

- **无向图：**各点连通，所有点为偶度。(存在奇度节点即存在起止点，当起止点相同时，$奇数+奇数=偶数$，因此所有节点均为偶度)

- **有向图：**各点连通，所有点入度 = 出度。(当其起止点为同一个是，那个点 入度 +1 = 出度 +1，因此所有点入度 = 出度)

## DFS求解

利用欧拉定理判断出一个图存在欧拉回路或欧拉通路后，选择一个正确的起始顶点，用DFS算法遍历所有的边(每一条边只遍历一次)，遇到走不通就回退。在搜索前进方向上将遍历过的边按顺序记录下来，这组边的排列就组成了一条欧拉通路或回路。

## Fleury(佛罗莱)算法

~~以后有时间再说~~
