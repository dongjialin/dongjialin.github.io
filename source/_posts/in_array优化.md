---
title: in_array优化
date: 2021-03-17 00:00:00
tags: [PHP]
---

in_array这个函数，在数据量大的情况下，效率会变的特别低
例如比较字符型数字的时候，两个字符型数字串先转换为长整型再进行比较，虽然加上第三参数true，转变成严格比较，会快一些，但还远远达不到优化的目的。
举例如下：
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
//计算时间
function microtime()
&#123;
list($usec, $sec) = explode(&#x27; &#x27;, microtime());
return ((float)$usec + (float)$sec);
&#125;
//初始化数组(int和str类型)
$int_arr = [];
$str_arr = [];
for ($i = 0; $i &lt; 30000; $i++) &#123;
$int_arr[] = $i;
$str_arr[] = &quot;&#123;$i&#125;&quot;;
&#125;
$int_arr1 = array_flip($int_arr);
$str_arr1 = array_flip($str_arr);
//执行
$starttime = microtime();
for ($i = 0; $i &lt; 50000; $i++) &#123;
if (in_array(1000, $int_arr)) &#123;
continue;
&#125;
//  if (isset($int_arr1[18000])) &#123;
//      continue;
//  &#125;
&#125;
$endtime = microtime();
echo &#x27;耗时：&#x27; . ($endtime - $starttime);
所以，我们在数据多的时候，利用array_flip()函数，调换数组的key和value,然后用isset()函数去搜索。速度会得到大幅度的提升。