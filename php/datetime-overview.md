# 日期时间操作一箩筐

## 格式化日期时间

> [date](https://www.php.net/manual/zh/function.date.php) : 格式化日期时间

- 说明

返回给定时间戳格式化后所产生的日期时间字符串,如果没有给出时间戳则默认使用本地当前时间.

- 备注

|格式|说明|返回值示例|
|-|-|-|
|`Y`|`4` 位数字完整表示的年份|`2019`|
|`y`|`2` 位数字表示的年份|`19`|
|`M`|三个字母缩写表示的月份|`Jan 到 Dec`|
|`m`|数字表示的月份,有前导零|`01 到 12`|
|`D`|星期中的第几天,文本表示,`3`个字母|`Mon 到 Sun`|
|`d`|月份中的第几天,有前导零的 `2` 位数字|`01 到 31`|
|`H`|小时,`24` 小时格式,有前导零|`00 到 23`|
|`h`|小时,`12` 小时格式,有前导零|`01 到 12`|
|`I`|是否为夏令时|如果是夏令时为`1` ,否则为 `0`|
|`i`|有前导零的分钟数|`00 到 59`|
|`S`|每月天数后面的英文后缀,`2` 个字符|`st,nd,rd` 或者 `th` ,可以和 `j` 一起用|
|`s`|秒数,有前导零 |`00 到 59`|

- 示例

```php
<?php
// 设置当前时区为上海时区
date_default_timezone_set("Asia/Shanghai");

// 获取当前时区 : Asia/Shanghai
echo "当前时区 : ".date_default_timezone_get()."<br/>";

// `Y年m月d日 H时i分s秒` 格式化当前时间 : 2019年05月30日 22时32分46秒
echo "当前时间 : ".date("Y年m月d日 H时i分s秒")."<br/>";

// `Y-m-d H:i:s` 格式化当前时间 : 2019-05-30 22:32:46
echo "当前时间 : ".date("Y-m-d H:i:s")."<br/>";

// `w` 星期中的第几天,数字表示: 0（表示星期天）到 6（表示星期六）
switch (date("w")) {
    case '0':
        $dayStr = "日";
        break;
    case '1':
        $dayStr = "一";
        break;
    case '2':
        $dayStr = "二";
        break;
    case '3':
        $dayStr = "三";
        break;
    case '4':
        $dayStr = "四";
        break;
    case '5':
        $dayStr = "五";
        break;
    case '6':
        $dayStr = "六";
        break;
    default:
        $dayStr = "未知";
        break;
} 
// 2019年05月30日 星期四
echo "当前时间 : ".date("Y年m月d日")." 星期".$dayStr."<br/>";

echo "<hr/>";

// `z` 年份中的第几天 : 今天是全年的第149天
echo "今天是全年的第".date("z")."天<br/>";

// `W` ISO-8601 格式年份中的第几周,每周从星期一开始 : 本周是全年的第22周
echo "本周是全年的第".date("W")."周<br/>";

// `t` 指定的月份有几天 : 本月共有31天
echo "本月共有".date("t")."天<br/>";

?>
```

## 当前 Unix 时间戳

> [time](https://www.php.net/manual/zh/function.time.php) : 返回当前的 Unix 时间戳

- 说明

返回自从 `Unix` 纪元(格林威治时间 `1970年1月1日 00:00:00`)到当前时间的**秒数**.

- 示例

```php
<?php
// 设置当前时区为上海时区
date_default_timezone_set("Asia/Shanghai");

// 获取当前时区
echo "当前时区 : ".date_default_timezone_get()."<br/>";

// 一周前的日期时间: 7 days; 24 hours; 60 mins; 60 secs
$preWeek = time() - (7 * 24 * 60 * 60);
echo "现在是".date("Y-m-d H:i:s").",上周是".date("Y-m-d H:i:s",$preWeek)."<br/>";

// 一周后的日期时间: 7 days; 24 hours; 60 mins; 60 secs
$nextWeek = time() + (7 * 24 * 60 * 60);
echo "现在是".date("Y-m-d H:i:s").",下周是".date("Y-m-d H:i:s",$nextWeek)."<br/>";

?>
```

> [microtime](https://www.php.net/manual/zh/function.microtime.php) : 返回当前 Unix 时间戳和微秒数

- 说明

当前 Unix 时间戳以及微秒数,本函数仅在支持 `gettimeofday()`` 系统调用的操作系统下可用.

- 示例

```php
<?php
// 设置当前时区为上海时区
date_default_timezone_set("Asia/Shanghai");

// 获取当前时区
echo "当前时区 : ".date_default_timezone_get()."<br/>";

// 当前时间戳
echo "当前时间戳: ".time()." <--> ".microtime()." <--> ".microtime(TRUE)."<br/>";
?>
```
