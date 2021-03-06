---
title: "状压dp"
linkTitle: "状压dp"
type: blog
weight: 6
date: 2021-10-17
description: >
  压缩！压缩！（为啥不用bitset咧？）
---

# 状压dp

又是二进制的东西……~~烦躁~~

这东西只是一个辅助，用来优化暴力或dp空间的。

## 用武之地

当状态维数 $n$ 很多但每一维状态数 $k$ 都很少(一般是 $2$)的时候，我们可以用一个 $n$ 位 $k$ 进制整数来表示这维状态。

下面，我们单表状态数为 $2$ 的情况。

在学习状压dp之前，我们应该清楚所有的dp是解决**多**阶段**决策最**优化问题的一种思想方法。请注意**多阶段**这三个字，如何定义状态是动态规划最重要的一步。状态的定义也就决定了阶段的划分。

动态规划多阶段一个**重要**的特性就是**无后效性**(值对于某个给定的阶段状态，它以前各阶段的状态无法直接影响它未来的发展，而只能通过当前的这个状态。换句话说影响当前阶段状态只可能是前一阶段的状态，而不能是后续的状态)

那么可以看出如何**定义状态**是至关重要的，因为状态决定了阶段的划分，阶段的划分保证了无后效性。

因此，我们为了保证无后效性，通常要在转移的时候带上足够的数据(很可能是一个数组)，这时的空间开销就会很大，因此我们把原数组中的每一位表示为某一个数字的某一位，这样只需要携带 $O(1)$ 的空间转移了。

## 例子

我们回想[01背包](./背包问题.md)，如果我们要让你记录一下具体是怎么装的如何？当时，我们给出了反向迭代推导的方法。

但是，我们也可以在每次dp决策的时候就记录一下，并带着选择的方式转移，这样我们就不用回溯了(典型的牺牲空间换取时间的办法)。

我们开了一个数组，`bool ji[n][k][n]`(虽然可以一维优化)，但是我十分不爽，这搞的空间过大了！

所以，我们想起了状压dp，因此，我们现在要降成二维`int ji[n][k]`，$ji[i][j]$ 表示对应dp表第 $i$ 行第 $j$ 列的选择方式：第 $1$ 个物品对应 $ji[i][j]$ 第一位的 $0/1$，第 $2$ 个对应第二位的 $0/1\space\dots\dots$

然后，我们把这个二进制数存在一个`int`里不就可了嘛，这样你就塞下了 $32$ 位的状态，真香。

## 从 $O(n!)$ 到 $O(2^n)$

状压dp是最接近暴力的一种dp，因为它可以完整地记录每一种状态。

但它又比 $O(n!)$ 的纯暴力搜索要优一些，因为它舍弃了状态的更新顺序的记录。

所以很多情况下，状压dp就是将 $O(n!)$ 的暴力优化到的另一个 $O(2^n)$ 暴力的过程。

## 子集枚举

## 合理运用小范围数据

状压dp中 $2^n$ 的复杂度使得题目中的某些数据范围也会很小（一般在 $25$ 以下）。当遇到 $\le{25}$ 数据范围时一定要敏感。