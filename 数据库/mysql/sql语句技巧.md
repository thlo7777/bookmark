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

在my.cnf添加如下配置  remove ONLY_FULL_GROUP_BY
[mysqld]
sql_mode='ONLY_FULL_GROUP_BY,NO_AUTO_VALUE_ON_ZERO,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE, ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION,PIPES_AS_CONCAT,ANSI_QUOTES'
```

####  HAVING子句必须位于任何GROUP BY子句之后和任何ORDER BY子句之前。
```
where和having的不同之处在于，where是查找之前的限定，而having是查找之后。

Having子句一般应用在最后，恰好在结果集被返回给MySQL客户端前，且没有进行优化。（而LIMIT应用在HAVING后）

SQL标准要求：HAVING必须引用在GROUP BY列表中或者聚合函数使用的列。然而，MySQL对此进行了扩展，
它允许HAVING引用Select子句列表中的列，还有外部子查询的列。

切记不要在该使用WHERE的地方使用HAVING。HAVING是和GROUP BY搭配的。

HAVING子句可以引用聚合函数，而WHERE不能。

SELECT user, MAX(salary) FROM users
  GROUP BY user HAVING MAX(salary) > 10;

```

#### [MySQL SELECT语法](https://www.cnblogs.com/bigbigbigo/tag/MySQL/)
---
#### DISTINCT 
```
DISTINCT 必须放在第一个参数。
DISTINCT 表示对后面的所有参数的拼接取 不重复的记录，相当于 把 SELECT 表达式的项 拼接起来选唯一值。
解决方法：使得DISTINCT 只对其中某一项生效

```
---
#### Having与Where的区别

> where 子句的作用是在***对查询结果进行分组前***，将不符合where条件的行去掉，即在***分组之前过滤数据***，where条件中***不能包含聚组函数***，使用where条件过滤出特定的行。<br/> having 子句的作用是筛选满足条件的组，即在***分组之后过滤数据***，条件中***经常包含聚组函数***，使用having 条件过滤出特定的组，也可以使用多个分组标准进行分组。

---
#### 使用Group By子句的时候，一定要记住下面的一些规则：
> （1）不能Group By非标量基元类型的列，如不能Group By text，image或bit类型的列<br/>（2）Select指定的每一列都应该出现在Group By子句中，除非对这一列使用了聚合函数；<br/>（3）不能Group By在表中不存在的列；<br/>（4）进行分组前可以使用Where子句消除不满足条件的行；<br/>（5）使用Group By子句返回的组没有特定的顺序，可以使用Order By子句指定次序。<br/>

>  **1.在使用 GROUP BY 子句时，Select列表中的所有列必须是聚合列（SUM,MIN/MAX,AVG等）或是GROUP BY 子句中包括的列。** 同样，如果在SELECT 列表中使用聚合列，SELECT列表必须只包括聚合列，否则必须有一个GROUP BY 子句。 <br/>
**2.聚合函数。** 聚合函数用于GROUP BY 字句，***用于聚合分组的数据***。聚合函数在和GROUP BY子句一起使用时显示出其强大的功能。但聚合函数的使用不限于分组查询；如果查询语句中使用了聚合函数，***而没使用GROUP BY子句，则聚合函数是用于聚合整个结果集（匹配WHERE子句的所有行）***。当不使用GROUP BY 子句时，在SELECT列表中某些聚合函数只能与其他的聚合函数一起使用，即聚合函数必须使用GROUP BY 子句才能在SELECT列表中与列明配对。例如，不使用GROUP BY子句，SELECT列表中AVG只能和SUM对应，但不能对应特定列。

### [sql 学习之 group by 及 聚合函数](https://www.cnblogs.com/caishuhua226/p/4583129.html)
>   **5. 除了Count(*)函数外，所有的聚合函数都忽略NULL值。** 要考虑到这一点对聚合结果的重要影响。许多用户在求平均值时，把数值类型字段中的NULL值看作0，但实际上NULL值与0并不等同，并不能这样使用。如果对有NULL值的列执行AVG函数或其他聚合函数，NULL值将不会计入聚合值中，除非使用如COALESCE()或ISNULL()等函数，将NULL值转换成非NULL值。 Count函数可与GROUP BY 字句联合使用。<br/>  **6.使用Having子句给分组设置条件 如果要将查询条件放到分组之后，则可以使用Having子句。** Having 子句仅用于带有GROUP BY 子句的查询语句中。WHERE子句应用于每一行（在变成一组的某一部分之前），而HAVING子句应用于分组的聚合值。 <br/> **7.Distinct和All 可以在任意聚合函数中使用Distinct谓词，即使聚合函数中使用Distinct谓词没有实际意义。** 例如，在AVG函数中使用Distinct没有任何意义。 很少在查询语句中使用All谓词，毫无疑问，All与Distinct谓词含义相反。Distinct谓词用于过滤掉重复的行，而All指包括所有的行。All是任意Select语句的默认值，但有Union的Select语句除外。

> Group By语句从英文的字面意义上理解就是“根据(by)一定的规则进行分组(Group)”。 作用：通过一定的规则将一个数据集划分成若干个小的区域，然后针对若干个小区域进行数据处理。 <br/>
>> 注意：
>> * group by 是先排序后分组！
>> * 当group by 与聚合函数配合使用时，功能为分组后计算
>> * 当group by 与 having配合使用时，功能为分组后过滤，获得满足条件的分组的返回结果。
>> * having与where区别：where过滤行，having过滤组

### SQL 子查询
```
子查询用于为主查询返回其所需数据，或者对检索数据进行进一步的限制。
子查询可以在 SELECT、INSERT、UPDATE 和 DELETE 语句中，同 =、<、>、>=、<=、IN、BETWEEN 等运算符一起使用。
```