# 搜索优化


### [时间序列数据库的秘密 (2)——索引](https://www.infoq.cn/article/database-timestamp-02/?utm_source=infoq&utm_medium=related_content_link&utm_campaign=relatedContent_articles_clk)
```
Elasticsearch 是通过 Lucene 的倒排索引技术实现比关系型数据库更快的过滤。特别是它对多条件的过滤支持非常好，比如年龄在 18 和 30 之间，性别为女性这样的组合查询。倒排索引很多地方都有介绍，
但是其比关系型数据库的 b-tree 索引快在哪里？到底为什么快呢？

笼统的来说，b-tree 索引是为写入优化的索引结构。当我们不需要支持快速的更新的时候，可以用预先排序等方式换取更小的存储空间，更快的检索速度等好处，其代价就是更新慢。要进一步深入的化，
还是要看一下 Lucene 的倒排索引是怎么构成的。
```