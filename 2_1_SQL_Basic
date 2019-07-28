# 数据分析师需要掌握的SQL基础

Hi，各位同学，我们将会从本期开始数据分析师的“技法修炼”，这些技法包括SQL，Python和统计学，具体的~~学习~~修炼安排如下：
- SQL
  - SQL基础：语法，检索，排序，过滤，创建计算字段和使用别名；
  - SQL进阶：链接表，聚合，分组，条件判断，子查询以及时间序列的处理；
- Python
  - Python基础：语法，数据类型，运算符，控制流，函数，脚本编写及本地环境搭建；
  - Python数据处理：Numpy与Pandas；
  - Python可视化：Matplotlib，Pyecharts；
- 统计学
  - 统计学基础：描述统计学，概率，正态分布，随机抽样，中心极限定律等；
  - 统计学进阶：推论统计学，置信区间，假设检验，线性回归，逻辑回归等。

所有以上的这些技法都只是**工具**，所以要以**会用且熟练**为目的，把学习重点放在应用层面，文章最后也会给出线上练习SQL的网址，多动手便能事半功倍！好啦，那我们就先开始SQL基础的修炼吧！
## 知识清单
### SQL简介

SQL是Structured Query Language的简写，也就是结构化查询语言。它最受欢迎的功能便是对数据库中的数据进行**增删改查**。作为数据分析师，会经常使用SQL语言从数据库中**查询**并提取数据，而**增删改**则一般由数据工程师去操作。

> 🙋‍♂️你可能听说过 NoSQL，它表示 Not only SQL（不仅仅是 SQL），与NoSQL的数据库进行交互时，你编写的代码会与本课程中所学的SQL有所不同。最常用的 NoSQL 语言之一是 [MongoDB](https://www.mongodb.com/)，可以自行了解一下～

### 书写规则及注释
就像我们刚开始学写字一样，在学习编写代码之前，我们也要先了解这门语言规范的书写规则和注释方法。
> 这部分虽然比较简单，但非常重要，有时候这不仅关系到你的饭碗，甚至还会危及到你的性命🥶，不信你可以看这篇假新闻：[因代码规范问题,美国一码农枪杀了4个同事](https://yq.aliyun.com/articles/644710?utm_content=m_1000016926)


#### SQL书写规则

- SQL语句不区分大小写，因此SELECT与select甚至是SeLect的效果是相同的，但是要对命令和变量进行区分，所以默认**命令需要大写，其他内容如变量等则需要小写**；
- 表和变量名中不要出现空格，可使用下划线`_`替代;
- 查询语句中，使用单一空格隔开命令和变量;
- 为提高代码的可移植性，请在查询语句结尾添加一个分号`；`。


#### SQL中的注释
代码是给电脑看的，而注释则是给人看的，是对你写这行代码的思路解释，方便自己做debug或者给同事交接。
- 单行注释
使用两个连字符`-`，添加注释。
```SQL
SELECT col_name -- 这是一条注释
FROM table_name;
```

- 多行注释

多行注释以`/*`起始，以`*/`结尾。
```sql
/*SELECT col_name 
FROM table_name;*/
SELECT col_2 
FROM table_name;
```
### 检索数据
检索数据主要用的语句为：SELECT和FROM，意为从（FROM）xxx表中选择（SELECT）xxx变量，下面看示例。
- 检索单列

从table_name表中检索col_name列。
```sql
SELECT col_name
FROM table_name;
```
- 检索多列

从table_name表中检索col_1,col_2和col_3列。
```sql
SELECT col_1,col_2,col_3
FROM table_name;
```
- 检索所有列

使用通配符`*`，返回table_name表中的所有列；
```sql
SELECT *
FROM table_name;
```

- 检索某列中不同的值

检索col_1中具有唯一性的行，即唯一值。
```sql
SELECT DISTINCT col_1
FROM table_name;
```

- 限制检索的结果

使用LIMIT语句可以限制返回的行数。
```sql
SELECT col_1
FROM table_name
LIMIT 10;
```
返回前10行（即第0-第9行）。

也可以添加OFFSET语句，设置返回数据的起始行：
```sql
SELECT col_1
FROM table_name
LIMIT 10 OFFSET 5;
```
从第五行之后，返回十行数据（即第5-第14行）。

### 排序检索数据
排序需要使用的子句是：**ORDER BY**。
- 其可以根据指定的单列或多列对结果进行排序；
- 默认按照升序进行排序（从小到大，从a到z），使用**DESC**关键字可以改为降序；
- 在使用**ORDER BY**时，请确保它是SELECT语句中的最后一条子句。

下面请看示例：
- 按列排序
```sql
SELECT col_name
FROM table_name
ORDER BY col_name;
```
返回的数据会按照col_name列进行升序排序，这里col_name可以是单列也可以是多列，当然也可以使用非检索的列进行排序。

- 降序排序
```sql
SELECT col_1,col_2
FROM table_name
ORDER BY col_2 DESC,col_3;
```
返回的数据会按照col_2列降序，col_3列升序对col_1和col_2两列进行排序。
> 这里可以看出，**DESC**关键字的用法：只对跟在语句前面的变量有效。所以，想要对多列进行降序排序时，需要对每一列都指定DESC关键字。

### 过滤数据
我们使用**WHERE**子句来根据某个条件对筛选的数据进行过滤。
- WHERE子句应该写在表名（即FROM子句）之后，在ORDER BY子句之前；
- 使用的基本方式为：`WHERE 列名+运算符+值`;
- 过滤条件是区分大小写的。

使用示例：
在表table_1列col_1中筛选出满足条件`col_1 运算符 value`的值。
```sql
SELECT col_1
FROM table_1
WHERE col_1 运算符 value;
```
- 运算符

| 运算符 |	描述 |
| --- | --- | 
| = |	等于 |
|<> |	不等于|
|> |	大于|
|< |	小于|
|>= |	大于等于|
|<= |	小于等于|
|BETWEEN…AND… |	在指定的两值之间|
|IS NULL |	为NULL值|
|AND |	逻辑运算符：与|
|OR |	逻辑运算符：或|
|IN |	条件范围筛选|
|NOT |	逻辑运算符：非|

> ⚠️ SQL的版本不同，可能导致某些运算符不同（如不等于可以用！=表示），具体要查阅数据库文档。

> 在同时输入AND和OR时，SQL会优先处理AND语句，所以为了建议大家在进行多条件筛选时，请用小括号将每个条件单独扩起来，这样既方便阅读代码，又不容易出问题。

- 用通配符进行过滤（LIKE）

通配符用来匹配值的一部分，跟在LIKE关键字后面进行数据过滤。
|通配符 |	描述|
| --- | --- | 
|% |	表示任何字符出现任意次数|
|_ 	|表示任何字符出现一次|
|[] |	指定一个字符集，它必须匹配该位置的一个字符|
|^ |	在[]中使用，表示否定|

示例：
```sql
SELECT col_1
FROM table_1
WHERE col_1 LIKE '_[^JM]%'
ORDER BY col_1;
```
如上筛选出的是，第二个字符为非J且非M的数据。
### 创建计算字段

其实就是在检索数据的同时进行计算，并使用关键字**AS**将结果保存为某一列。

- 数值类型的计算
```sql
SELECT prod_id,quantity,item_price,quantity*item_price AS expanded_price
FROM orderitems
WHERE order_num = 200008;
```
输出：
```
prod_id         quantity       item_price      expanded_price
--------------------------------------------------------------
RGAN01			5				4.9900			24.9500
BR03			5				11.9900			59.9500
```
这里实现的就是使用`quantity*item_price`创建一个名为`expanded_price`的计算字段，也就是一个新列。

同样适用于计算的操作符有+（加），-（减）和/（除）。

- 字符类型的拼接
```sql
SELECT RTRIM(col_name) + '('+RTRIM(col_country)+')' AS col_title
FROM table_name
ORDER BY col_name;
```
输出：
```
col_title
------------------------
Bear Emporium(USA)
Bears R Us(USA)
Jouets et ours(France)
```
这里实现的就是将col_name列与col_country列进行了拼接，新列的名字叫做col_title。

> RTRIM()函数是去掉右边的所有空格，LTRIM()是去掉左边的所有空格，TRIM()是去掉两边的所有空格。

### 使用别名

在上一节中我们使用**AS**来为变量设置别名，你可能也见过如下所示的语句：
```sql
SELECT col1 + col2 AS total, col3
```
当然没有 AS 的语句也可以实现使用别名：
```sql
FROM tablename t1
```
以及
```sql
SELECT col1 + col2 total, col3
```
将col1+col2的结果设置名为total的列。

### 代码总结
|语句 |	使用方法 |	其他详细信息|
| --- | --- | --- |
|SELECT |	SELECT Col1, Col2, … |	选择要筛选的列|
|FROM |	FROM Table |	提供列所在的表格|
|LIMIT |	LIMIT 10 |	限制返回的行数|
|ORDER BY |	ORDER BY Col |	根据列Col对查询的结果排序（顺序），可与 DESC 一起使用实现逆序。|
|WHERE |	WHERE Col > 5 |	用于过滤结果的一个条件语句|
|LIKE |	WHERE Col LIKE ‘%me%’ |	仅提取出列文本中包含 ‘me’ 的行|
|IN |	WHERE Col IN (‘Y’, ‘N’) |	仅过滤行对应的列为 ‘Y’ 或 ‘N’的数据|
|NOT |	WHERE Col NOT IN (‘Y’, “N’) |	NOT表示非，与上行结果刚好互补。|
|AND |	WHERE (Col1 > 5) AND (Col2 < 3) | AND表示与，过滤两个或多个条件均为真的数据|
|OR 	|WHERE Col1 > 5 OR Col2 < 3 |	OR表示或，过滤至少某一条件为真的行|
|BETWEEN |	WHERE Col BETWEEN 3 AND 5 |	与AND连用，比用运算符简单一些|

## 相关资源
- 面试前刷题：[SQL zoo](https://sqlzoo.net/)
- 关系数据库MySQL：
   - [21分钟 MySQL 入门教程](https://www.cnblogs.com/mr-wid/archive/2013/05/09/3068229.html)
   - [MySQL索引背后的数据结构及算法原理](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)
- 非关系数据库MongoDB：[The Little MongoDB Book](https://github.com/justinyhuang/the-little-mongodb-book-cn/blob/master/mongodb.md)
- [非关系型数据库和关系型数据库区别，优势比较](https://www.zhihu.com/question/24225007)
