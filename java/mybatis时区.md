# mybatis 时区

在使用mybatis连接mysql数据库查询时间的时候，时区上出了点偏差

通过终端连接数据库，

`select now();` 语句查出来的时间，和我本地时间是一致的。

select 语句查表对应记录查出来的时间是 `2014-10-18 17:40:00` 

但是通过 mybatis 连接数据库查出来的时候却是 `2014-10-18T22:40:00.000+00:00` 这是零时区的时间，换算本地东8区时间为 `2014-10-19 06:40:00 ` 和本地时间差了 13 个小时

将连接数据库的 url 后面添加上一个参数 `serverTimezone=GMT%2B8` 查询出来的时候就是 `2014-10-18T09:40:00.000+00:00` 换算本地时间为 `2014-10-18 17:40:00` 这和直接通过终端查询到的时间就是一致的了

通过终端执行 `show variables like '%time_zone%'` 查询出来的结果是

```
+------------------+--------+
| Variable_name    | Value  |
+------------------+--------+
| system_time_zone | CST    |
| time_zone        | SYSTEM |
+------------------+--------+
```

也不知道对不对，反正数据是对应上了