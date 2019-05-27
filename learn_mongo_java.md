## Learn about Mongo. :smile:

- ## [Introduction](#1)
  - ### [Rich data types](#1_1)
  - ### [Easily Extendable](#1_2)
  - ### [Rich functionalities](#1_3)
  - ### [Without sacrificing speed](#1_4)
  - ### [Simple management](#1_5)
  - ### [Other content](#1_6)

## mongoDB is a document database.I want to tell you what i know :smile: give me :star:,thanks.

- ## <p id="1">简介</p>
  mongodb 是一种强大,灵活,可扩展的数据存储方式.它扩展了关系型数据库众多有用的功能,如辅助索引,范围查询和排序.mongodb 的功能非常丰富,内置 mapreduce 式聚合支持.,以及对地理空间索引的支持.
  - ### <p id="1_1">丰富的数据类型</p>
    mongodb 是一种文档型数据库,所以对数据类型支持非常丰富,不需要像 MySQL 一样事先定义好数据类型,MongoDB 会根据传入数据自动分配类型.基于文档模式,MongoDB 一个文档就可以表示复杂的数据关系.(_文档就相当于 MySQL 数据库中的行_).
  - ### <p id="1_2">更优秀的扩展方式</p>
    MongoDB 在设计之初就考虑到了数据库的扩展性,它所采用的面向文档的数据模型可以使其自动在多台服务器之间分割数据,它还可以平衡集群的数据和负载,自动重排文档.可以让开发者更好的关注业务层面,而无需在数据库设计上花费更多的时间.
  - ### <p id="1_3">丰富的功能</p>
    - 1. **索引**
         _MongoDB 不仅支持通用辅助索引,能进行多种快速查询,也提供唯一索引,复合索引和地理空间数据的索引能力._
    - 2. **存储 JavaScript**
         _开发人员不必使用 存储过程了,可以直接在服务端存取 JavaScript 的函数和值._
    - 3. **聚合**
         _MongoDB 支持 MapReduce 和其他聚合工具_
    - 4. **固定集合**
         _集合的大小是有上限的,对于某些日志数据特别有用_
    - 5. **文件存储**
         _MongoDB 支持一种容易使用的协议存储大型文件和元数据._
  - ### <p id="1_4">不牺牲速度</p>
    MongoDB 在设计之初就以速度为目的,所以在设计时牺牲了很多关系型数据库的特性.同时 MongoDB 采用 MongoDB 协议作为服务器的交互方式,比同类型的 http or rest 更少的开销.同时 MongoDB 支持对对文档进行动态填充,预分配数据文件,用空间换取性能的稳定.默认的存储引擎中使用了内存映射文件,将内存管理工作交给操作系统去处理.动态查询优化器会记住'最高效'的查询方式.总之,MongoDB 尽可能在各个方面提高性能.
  - ### <p id="1_5">简单的管理</p>
    MongoDB 尽量让服务器自治来简化数据库的管理.除了启动数据库之外,MongoDB,几乎没有必要的管理操作.MongoDB 尽可能的满足各种异常场景的自修复.
  - ### <p id="1_6">其他内容</p>
    继续看就知道啦 :love_hotel:
