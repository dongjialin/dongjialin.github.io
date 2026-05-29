---
title: in_array优化
date: 2021-03-17 00:00:00
tags: [PHP]
description: 每天一个小技巧
---

in_array这个函数，在数据量大的情况下，效率会变的特别低
例如比较字符型数字的时候，两个字符型数字串先转换为长整型再进行比较，虽然加上第三参数true，转变成严格比较，会快一些，但还远远达不到优化的目的。
举例如下：

```php
//计算时间
function microtime()
{
list($usec, $sec) = explode(' ', microtime());
return ((float)$usec + (float)$sec);
}
//初始化数组(int和str类型)
$int_arr = [];
$str_arr = [];
for ($i = 0; $i < 30000; $i++) {
$int_arr[] = $i;
$str_arr[] = "{$i}";
}
$int_arr1 = array_flip($int_arr);
$str_arr1 = array_flip($str_arr);
//执行
$starttime = microtime();
for ($i = 0; $i < 50000; $i++) {
if (in_array(1000, $int_arr)) {
continue;
}
//  if (isset($int_arr1[18000])) {
//      continue;
//  }
}
$endtime = microtime();
echo '耗时：' . ($endtime - $starttime);
```

所以，我们在数据多的时候，利用array_flip()函数，调换数组的key和value,然后用isset()函数去搜索。速度会得到大幅度的提升。
