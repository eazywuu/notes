## 集

###  1. concat - 连接字符串

```sql
concat(str1,str2,…)
返回结果为连接参数产生的字符串。如有任何一个参数为NULL ，则返回值为 NULL。

contcat_ws(separator,str1,str2,...)
代表 CONCAT With Separator ，是CONCAT()的特殊形式。第一个参数是其它参数的分隔符。分隔符的位置放在要连接的两个字符串之间。分隔符可以是一个字符串，也可以是其它参数。
注意：
如果分隔符为 NULL，则结果为 NULL。函数会忽略任何分隔符参数后的 NULL 值
和MySQL中concat函数不同的是, concat_ws函数在执行的时候,不会因为NULL值而返回NULL
```

###  2. replace - 替换字符串

```sql
REPLACE(str,old_string,new_string)
REPLACE()函数有三个参数，它将string中的old_string替换为new_string字符串

# 有一个也叫作REPLACE的语句用于插入或更新数据。所以不要将REPLACE语句与这里的REPLACE字符串函数混淆。
```

### 3. mid - 获取中间字符串

```sql
MID(str,pos,len)
str是字符串，pos是起始子字符串的位置，len是一个可选参数，它决定从起始位置返回的字符数

MID(str,pos) === MID(str FROM pos) ``(from是标准sql)``

MID(str,pos,len) === MID(str FROM pos FOR len) ``(from是标准sql)``
```

### 4. like - 模糊查询

```sql
like [binary] concat(name,'%')

%通配符：它能代表任何长度的字符串，字符串的长度可以为 0

_通配符：只能代表单个字符，字符的长度不能为 0

[]通配符：匹配[ ]中的任意一个字符(若要比较的字符是连续的，则可以用连字符“-”表达 )

[^]通配符：不匹配[]中的任意一个字符

区分大小写：可以加入 ``BINARY ``关键字

转义字符:如果查询的字符里面有%等字符，可以使用\转义

查询以“#”结尾的学生姓名 
WHERE NAME LIKE '%\#'

/** 注意事项：

不要过度使用通配符，如果其它操作符能达到相同的目的，应该使用其它操作符。因为MySQL 对通配符的处理一般会比其他操作符花费更长的时间。

在确定使用通配符后，除非绝对有必要，否则不要把它们用在字符串的开始处。把通配符置于搜索模式的开始处，搜索起来是最慢的。

仔细注意通配符的位置。如果放错地方，可能不会返回想要的数据。
/
```



### 5. round - 取小数，可以为负数

```sql
ROUND(x,d) ，x指要处理的数，d是指保留几位小数

这里有个值得注意的地方是，d可以是负数，这时是指定小数点左边的d位整数位为0,同时小数位均为0

ROUND(x) ,其实就是round(x,0),也就是默认d为0
```

```sql
# 例：显示万亿国家的人均国内生产总值，四舍五入到千位
select name,round(avg(gdp/population),-3) avg
from world
where gdp > 1000000000000
```



### 6. case - 条件判断语句，可嵌套

```sql
CASE
     WHEN condition1
     THEN value1
     WHEN condition2
     THEN 
         CASE
              WHEN condition3
              THEN value2
              ELSE value3
         End
     ELSE def_value
END
```

### 7. regexp(正则表达式) - 模糊查询

```markdown
LIKE 匹配整个列，如果被匹配的文本在列值中出现，LIKE 将不会找到它，相应的行也不会被返回（除非使用通配符）。

REGEXP 在列值内进行匹配，如果被匹配的文本在列值中出现，REGEXP 将会找到它，相应的行将被返回，并且 REGEXP 能匹配整个列值（与 LIKE 相同的作用）
```

### 8. group by 和 having - 分组查询和组内条件

```sql
group by使用场景
例1：select sum(money) from human
此时只select一个聚合函数字段，不需要使用group by

例2：select name，sum(money) from human
此时包括原始字段和聚合函数字段，需要使用分组，且只能使用原始字段分组
```

```sql
having使用场景：
分组后使用having，只对组内进行筛选，可以使用聚合函数
```

```sql
# 例：列出有至少100百萬(1億)(100,000,000)人口的洲份
select continent
from world
group by continent
having sum(population) > 100000000
```

### 9. join - 连接

```sql
inner join：2表值都存在
outer join：附表中值可能存在null的情况。

A inner join B：取交集

outer join:
A left join B：取A全部，B没有对应的值，则为null
A right join B：取B全部，A没有对应的值，则为null
A full outer join B：取并集，彼此没有对应的值为null
A natural join B：取并集，没有对应的值丢弃

上述4种的对应条件，在on后填写
```

### 0.0 聚合函数

> 聚合函数结果作为筛选条件时，不能用where，而是用having语法.

```sql
sum()
avg()
count()
max()
min()
```



## 杂项

``` sql
instr()

find_in_set()
```

