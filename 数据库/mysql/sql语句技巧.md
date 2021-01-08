#### 大表一般用distinct效率不高，大数据量的时候都禁止用distinct，建议用group by解决重复问题。

#### 由于COUNT()函数不可用于WHERE语句中，故使用HAVING语句来限定t>15的条件