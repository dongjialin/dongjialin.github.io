---
title: golang时间戳转换
date: 2021-11-19 00:00:00
tags: [Golang]
description: golang的时间戳
---

### 例子
```go
package main
import(
"fmt"
"time"
)
func main() {
datetime := "2015-01-01 00:00:00"  //待转化为时间戳的字符串
//日期转化为时间戳
timeLayout := "2006-01-02 15:04:05"  //转化所需模板  
loc, _ := time.LoadLocation("Local")    //获取时区  
tmp, _ := time.ParseInLocation(timeLayout, datetime, loc) 
timestamp := tmp.Unix()    //转化为时间戳 类型是int64
fmt.Println(timestamp) 
//时间戳转化为日期  
datetime = time.Unix(timestamp, 0).Format(timeLayout)
fmt.Println(datetime)    
}
```

### 数据库查出转换
```go
//v.Birthday在数据库中存2021-11-10 查出显示2021-11-10T00:00:00+08:00
//v.CreatedAt在数据库中存2021-11-10 23:32:31.072  查出显示2021-11-10T23:27:35.075+08:00
for k, v := range res {
res[k].Birthday = strings.Split(v.Birthday, "T")[0]
t := v.CreatedAt
t.String()
res[k].Createtime = t.Format("2006-01-02 15:04:05")
}
```