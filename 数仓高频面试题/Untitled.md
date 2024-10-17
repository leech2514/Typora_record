给定一个表temp,字段是 user_id,clo1,col2....col12 12各字段代表12个月电费，求最终结果展现:user_id,month,money

表temp，字段：first_ca,second_ca,mon

``` sql
select
	first_ca,second_ca
	,mon
from temp
group by first_ca,second_ca
grouping sets(first_ca,second_ca)

```

