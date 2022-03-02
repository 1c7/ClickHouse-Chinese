# ClickHouse 学习资料(文章/视频)
本库开始于2022年3月2号。

## ClickHouse 是什么？
1. ClickHouse 是一个数据库。它有 `create database`, `create table`, 自己的数据类型。等等。
2. 本库创建者的具体用例: PostgreSQL 依然是业务的主数据库, 数据同步到 ClickHouse，数据可视化用 Superset。

## 这是什么？
这里是一个资料列表，存放所有高质量的 ClickHouse 学习资料，包括文章，视频。 

## 为什么做这个表？
网上 ClickHouse 的学习资料并没有想象的那么多。  
我在学习过程中看到高质量资料就收集到这里，帮助其他想学 ClickHouse 的人。   

## 列表
* [(英文) Altinity Quickstart for ClickHouse | Build Your First App | ClickHouse Training](https://www.youtube.com/watch?v=phTu24qCIw0&t=1198s)  
点评：五星推荐。非常适合新手观看。    
2022年1月出的视频，59分钟50秒。     
内容是对 ClickHouse 做入门介绍。     
* 会教你怎么安装 ClickHouse
* 如何从命令行链接上 ClickHouse (使用 `clickhouse-client`)
* 介绍 ClickHouse 内置的 Web UI `localhost:8123`  
* Database 和 Table 的概念
* 一些方便的命令
  * `show databases` 列出 ClickHouse 里的所有数据库。
  * `select currentDatabase()` 输出当前数据库。
  * `show tables` 显示某个数据库里的所有表。
  * `describe table [表名]` 输出某张表的结构。
* 使用 `use [数据库名]` 来切换不同的数据库。  
* ClickHouse 中的特殊数据库
  * default: 每次登陆后的默认数据库。
  * system: 系统表，metadata 存这里。
* (18:24) 如何用 `CREATE TABLE` 创建表格并且指定数据类型，指定 Engine Type。等等。  
* (21:40) 各种插入数据的方法 (Use input formats to load raw data)
```
cat sdata.csv | clickhouse-client \
--database=sense \ 
--query='INSERT INTO sdata FORMAT CSVWithNames'
```
* (26:44) 如何更新或删除行。  
  * 更新和删除的成本很高。并且是异步操作。
  * 教你怎么判断异步操作到底完成没有。
* (28:00) 当运行 INSERT 的时候发生了什么。  
* (29分钟) Why MergeTree? 
* 33分钟：一个 SQL 示例，查询2017年里，哪位用户取消的行程最多。 
* 36分钟：ClickHouse 有很棒的 date-time support。
  * Date, DateTime, DateTime64 类型。
  * toYear(), toMonth(), toWeek(), toDayOfWeek, toDay(), to Hour()...
  * toYYYYMM(), toYYYYMMDD(), toYYYYMMDDhhmmsss()  
* 37分钟: ClickHouse 有很多 aggregates
  * 除了支持标准 SQL 里的 count(), avg(), sum(), min(), max()
  * 还有:
    * any()
    * anyLast()
    * avgWeighted()
    * uniq()
    * uniqExact()
    * quantile()
    * ...
* 38分钟: Group By 语法。  
* 40分钟: JOIN 语法。(LEFT JOIN)  
* 41分钟: JOIN 详解
  * `LEFT [OUTER] JOIN`
  * `FULL [OUTER] JOIN`
  * `RIGHT [OUTER] JOIN`
  * `[INNER] JOIN`
  * `CROSS JOIN`
* 42分钟: ClickHouse 是如何处理 Join 查询的？  
* 45分钟: ClickHouse 性能指南。
  * Add more CPU
  * Limit columns and rows in queries
* 48分钟: Understanding what's going on in MergeTree。  
* 52分钟：压缩。
* 55分钟：和 ClickHouse 搭配使用的各种软件
  * Client Libraries
  * Rendering
    * Apache Superset

* [(书籍) ClickHouse原理解析与应用实践](https://book.douban.com/subject/35091211/)  
这本书我粗略翻了一下，270页。似乎是市面上唯一一本中文书。    
点评：非常适合新手观看。前面介绍了一下 ClickHouse 的历史，名字的由来，发展历程。  
介绍了基本用法。  
后面关于 MergeTree 的部分看不懂。  
这本书可以买了之后备在手边，等需要的时候再翻。因为后半部分的内容没法马上用上，很复杂很多细节，也不可能全部记住。     


