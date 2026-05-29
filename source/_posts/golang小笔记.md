---
title: golang小笔记
date: 2020-11-07 00:00:00
tags: [Golang]
description: 最近在学习Golang，在此记录一下
---

### 运行用时
```go
start := time.Now()
secs := time.Since(start).Seconds()
```

### 将字符串 "hello" 转换为 "cello"
```go
s := "hello"
c := []byte(s)
c[0] = 'c'
s2 := string(c) // s2 == "cello"
```

### 切片（php中类似索引数组）
当相关数组还没有定义时，我们可以使用 make() 函数来创建一个切片 同时创建好相关数组：var slice1 []type = make([]type, len)。
也可以简写为 slice1 := make([]type, len)，这里 len 是数组的长度并且也是 slice 的初始长度。
所以定义 s2 := make([]int, 10)，那么 cap(s2) == len(s2) == 10。
make 接受 2 个参数：元素的类型以及切片的元素个数。
如果你想创建一个 slice1，它不占用整个数组，而只是占用以 len 为个数个项，那么只要：slice1 := make([]type, len, cap)。
make 的使用方式是：func make([]T, len, cap)，其中 cap 是可选参数。
所以下面两种方法可以生成相同的切片:
```go
make([]int, 50, 100)
new([100]int)[0:50]
```

### map（php中类似关联数组）
map 是 引用类型 的： 内存用 make 方法来分配。
map 的初始化：var map1 = make(map[keytype]valuetype)。
或者简写为：map1 := make(map[keytype]valuetype)。
上面例子中的 mapCreated 就是用这种方式创建的：mapCreated := make(map[string]float32)。
相当于：mapCreated := map[string]float32{}。
mapAssigned 也是 mapList 的引用，对 mapAssigned 的修改也会影响到 mapLit 的值。
不要使用 new，永远用 make 来构造 map
```go
map1 := make(map[string]int)
map1["New Delhi"] = 55
map1["Beijing"] = 20
map1["Washington"] = 25
```

### 转json
```go
json, _ := json.Marshal(array)
```