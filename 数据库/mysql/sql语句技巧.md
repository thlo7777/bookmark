#### 1. 大表一般用distinct效率不高，大数据量的时候都禁止用distinct，建议用group by解决重复问题。

#### 2. 由于COUNT()函数不可用于WHERE语句中，故使用HAVING语句来限定t>15的条件

#### 3. MySQL官方文档有说明，in关键字适合确定数量的情况，一般效率较低，不推荐使用。能用in关键字的语句都可以转化为使用join的语句，推荐使用join关键字。

#### 4. 使用not in 如果子查询中返回的任意一条记录包含空值，则查询不返回任何记录，而且not in 会对内外表进行全表扫描，没有用到索引。而not exists子查询仍然会用到索引，所以无论那个表大，not exists都会比not in 快。 另外，如果子查询表大适合用exists，表小适合用in

#### [GROUP BY语句与HAVING语句的使用](https://www.cnblogs.com/geogre123/p/11177204.html)
```
使用group by子句时，select子句中只能有聚合键、聚合函数、常数。

```

#### Group by 查询时的ONLY_FULL_GROUP_BY错误解决
```
错误显示：
[42000][1055] Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'r.emp_no' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by


sql_mode 配置解析
ONLY_FULL_GROUP_BY

对于GROUP BY聚合操作，如果在SELECT中的列，没有在GROUP BY中出现，那么这个SQL是不合法的，因为列不在GROUP BY从句中。简而言之，就是SELECT后面接的列必须被GROUP BY后面接的列所包含。如：
select a,b from table group by a,b,c; (正确)
select a,b,c from table group by a,b; (错误)
这个配置会使得GROUP BY语句环境变得十分狭窄，所以一般都不加这个配置

解决，通过配置my.cnf

```

####  HAVING子句必须位于任何GROUP BY子句之后和任何ORDER BY子句之前。
```
Having子句一般应用在最后，恰好在结果集被返回给MySQL客户端前，且没有进行优化。（而LIMIT应用在HAVING后）

SQL标准要求：HAVING必须引用在GROUP BY列表中或者聚合函数使用的列。然而，MySQL对此进行了扩展，
它允许HAVING引用Select子句列表中的列，还有外部子查询的列。

切记不要在该使用WHERE的地方使用HAVING。HAVING是和GROUP BY搭配的。

HAVING子句可以引用聚合函数，而WHERE不能。

SELECT user, MAX(salary) FROM users
  GROUP BY user HAVING MAX(salary) > 10;

```

#### [MySQL SELECT语法](https://www.cnblogs.com/bigbigbigo/tag/MySQL/)