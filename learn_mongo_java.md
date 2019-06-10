## Learn about Mongo. :smile:

- ## [Introduction](#1)
  - ### [Rich data types](#1_1)
  - ### [Easily Extendable](#1_2)
  - ### [Rich functionalities](#1_3)
  - ### [Without sacrificing speed](#1_4)
  - ### [Simple management](#1_5)
  - ### [Other content](#1_6)
- ## [Elementary](#2)
  - ### [Document](#2_1)
  - ### [Collection](#2_2)
  - ### [Database](#2_3)
  - ### [Start up MongoDB](#2_4)
  - ### [MongoDB Shell](#2_5)
  - ### [Data Type](#2_6)
- ## [Insert,Update and Delete document](#3)
  - ### [Insert and save Document](#3_1)
  - ### [Delete Document](#3_2)
  - ### [Update Document](#3_3)
  - ### [Instant Completion](#3_4)
  - ### [Request and Connection](#3_5)
- ## [Query](#4)
  - ### [Find introduction](#4_1)
  - ### [Query condition](#4_2)
  - ### [Specific type of query](#4_3)
  - ### [\$where query](#4_4)
  - ### [Cursor and cursor inside](#4_5)
- ## [Index](#5)
  - ### [Index introduction](#5_1)
  - ### [Unique index](#5_2)
  - ### [Index analysis](#5_3)

## mongoDB is a document database.I want to tell you what I know. :smile: give me :star:,thanks.

:smile: :bird: :love_hotel: :house: :hammer:

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
- ## <p id="2">入门</p>
  - 文档是 MongoDB 中的数据单元,类似于关系型数据库中的行(_但比行要复杂的多_).
  - 集合可以看做是没有模式的表.
  - MongoDB 单个实例可以容纳多个独立的数据库,每一个都有自己的集合和权限.
  - MongoDB 自带简洁而功能强大的的 JavaScript shell,对于 MongoDB 的管理和操作非常强大.
  - MongoDB 每个文档中都包含一个特殊的键 \_id,它在文档所处的集合中唯一.
  - ### <p id="2_1">文档</p>
    文档是 MongoDB 中的核心概念.多个键及其关联的值有序地放置在一起便是文档.例子
    ```json
    {"_id":ObjectId(""5a6a1d787c00f2a8e85f7a18"),"cid":NumberLong(50008898)}
    ```
    - 1. 文档中的键/值对是有序的,文档中的值不仅可以是字符串(_Default utf-8_),还可以是其他几种数据类型.文档中的键均是字符串.
  - ### <p id="2_2">集合</p>
    - 1. **无模式** 集合就是一组文档.类似于关系型数据库中的表.(_集合可以放置任何文档_),But,建议将同类型的集合放置在一个集合中,这样既容易分辨,又能有好的查询效率.
    - 2. **命名**
      1. 集合名不能是空字符串"".
      1. 集合名不能含有\0 字符(空字符),这个字符表示集合名的结尾.
      1. 集合名不能以"system."开头,这是系统保留前缀.
      1. 用户创建的集合名字不能含有保留字符\$.
         > 任何的骚操作建议都不要用,老老实实写个正常的名字吧.:alien:
  - ### <p id="2_3">数据库</p>
    MongoDB 中多个文档组成集合,集合组成数据库.一个 MongoDB 实例可以承载多个数据库,每个数据库都有独立的权限控制,即便在磁盘上,不同的数据库也放置在不同的文件中.建议将一个应用的所有数据都存储在一个数据库中.
    > 数据库名也不要有骚操作.不然真出问题了,你就炸了.:imp:
    > MongoDB 自带数据库:
    - **admin**
      从权限的角度看,这是"root"数据库.在这个数据库中,可以进行用户的添加删除,权限控制.
    - **local**
      这个数据库永远不会被复制,可以用来存储限于本地单台服务器的任意集合.
    - **config**
      当 MongoDB 用于分片设置时,config 在数据库内部使用,用于保存分片的相关信息.
  - ### <p id="2_4">启动 MongoDB</p>
    ```shell
    $ ./mongod 启动 MongoDB,使用默认数据目录,端口号.
    ```
  - ### <p id="2_5">MongoDB shell</p>
    MongoDB 自带一个 JavaScript shell,可以从命令行与 MongoDB 实例交互.这个 shell 非常有用,通过它可以执行管理操作,检查运行实例.
  ```mongo
  ./mongo --运行 mongo client
  > x=200
  > x/5;
  40
  > Math.sin(Math.PI/2) --调用 JavaScript 的库.
  > new Date("2010/1/1")
  > function factorial(n){
    if(n <= 1 ) return 1;
    return n * factorial(n-1);
  }
  > factorial(5) --定义 JavaScript 函数,并调用.
  ```
- ### <p id="2_6">数据类型</p>
  - 1. **基本数据类型**
       MongoDB 的文档类似于 json,在概念上和 JavaScript 中的对象神似.MongoDB 在保留 json 基本的键值对特性的基础上,添加了其他一些数据类型.
    - 1.  null 用于表示空值或者不存在的字段.
    - 2.  布尔 布尔类型有 true 和 false.
    - 3.  32 位整数.
    - 4.  64 位整数.
    - 5.  64 位浮点数
    - 6.  字符串
    - 7.  符号
    - 8.  对象 id
    - 10. 日期
    - 11. 正则表达式
    - 12. 代码
    - 13. 二进制数据
    - 14. 最大值
    - 15. 最小值
    - 16. 未定义
    - 17. 数组
    - 18. 内嵌文档
  - 2. **数字** JavaScript 只支持一种数字类型,但是 MongoDB 支持 3 中,所以建议不要再 MongoDB 自带的 shell 中使用这些东西.
  - 3. **日期** 在 JavaScript 中,Date 对象用作 MongoDB 的日期类型.
  - 4. **数组** 数组是一组值,既可以作为有序对象,也可以作为无序对象.数组是一种无模式的数组,可以存储 string,integer 等类型的数据.
  - 5. **内嵌文档** 内嵌文档就是把整个 MongoDB 文档作为另一个文档中键的一个值.这样数据可以组织得更自然些.
  - 6. **\_id and ObjectId** MongoDB 的文档中必须包含一个\_id 的键,键值可以是任意类型的数据,如果没有指定,就是一个 ObjectId 对象.
    - 1. ObjectId ObjectId 是\_id 的默认类型,因为 MongoDB 在设计之初就是为了支持分布式数据库的,自增 ID 在分布式数据库中还是有很大的问题的,所以 ObjectId 的概念应运而生.
         ObjectId 使用 12 个字节的存储空间,每个字节每位 16 进制数字,是一个 24 位的字符串. ObjectId 生成方式
         0|1|2|3|4|5|6|7|8|9|10|11
         时间戳 |机器 | pid|计数器
         前 4 个字节是从标准纪元开始的时间戳,单位为 秒.
      - 1. 时间戳,与随后的 5 个字节组合起来,提供了秒级别的唯一性.
      - 2. 这 4 个字节隐含了文档创建的时间.可以用来获取创建时间 :tea:.
           接下来的 3 字节是所在主机的唯一标识符.通常是主机名的散列值,主要为了确保不同主机生成不同的 ObjectID,
      - 3. pid 表示产生 ObjectId 的进程标识符(PID)
      - 4. 后 3 个字节就是自增的计数器.确保相同进程同一秒产生的 ObjectId 是不一样的,每一秒钟最多允许每个进程拥有 256^3(_16777216_)个不同的 ObjectId.
    - 2. 自动生成\_id
      - 1. 让 MongoDB 服务端生成 \_id 这个事情,是会产生开销的.尽量让客户端生成.
      - 2. 在客户端生成 ObjectId,可以有更多方便的操作.比如说可以直接拿到插入数据的 id,如果让 MongoDB server 生成 id,就需要再执行一次查询才能拿到 \_id.
- ## <p id="3">创建,更新及删除文档</p>

  - ### <p id="3_1">插入并保存文档</p>
    `db.foo.insert({"bar":"baz"})`
    - **批量插入**
      如果要插入多个文档,批量插入是最快的.一次批量插入只是单个 TCP 请求,避免了许多零碎的请求带来的开销.由于无需处理大量的消息头,这样就能够减少插入时间. 单个文档发送到数据库时,会带一个头部信息,告诉数据库要进行什么操作,批量插入时只需要带一个头部信息就可以了,不用一遍又一遍地处理每一个文档的这种信息了.
      > 当前版本的 MongoDB 支持的最大消息长度是 16 MB.
    - **插入:原理和作用**
      当数据库执行插入时,先将数据序列化成 BSON 形式,然后将其送入数据库.数据库解析 BSON,检验是否包含\_id 键,并且文档不超过 16 MB.除此之外,不做别的数据验证,就只是简单地将文档原样存入数据库中.这样避免了传统的注入式攻击.
  - ### <p id="3_2">删除文档</p>

  ```sql
  db.users.remove() -- 删除 users 集合中所有的文档.但不会删除集合本身.原有的索引也会保留.
  db.users.remove({"_id":ObjectId("id")}) -- remove 可以接受一个查询条件
  ```

  - **删除速度**
    删除文档通常会很快,但是要清除整个集合,直接删除集合(_然后重建索引_)会更快.
  - ### <p id="3_3">更新文档</p>

    文档存入数据库以后,就可以用 update 方法来修改它.update 有两个参数,一个是查询文档,用来找出要更新的文档,另一个是修改器(modifier)文档,描述对找出的文档做哪些更改.更新操作是原子的,若是两个更新同时发生,FIFO 执行.

    - **文档替换**
      更新最简单的情形就是完全用一个新文档代替匹配的文档.这适用于模式结构发生较大变化的时候,不介绍,建议在应用层适用.
    - **使用修改器**
      通常文档只会有一部分更新.利用原子的更新修改器,可以使得这种部分更新极为高效.

      ```sql
      db.users.update({query},{"$set":{"userName":"哇咔咔"}) -- 将查询出来的数据的 userName 都改为哇咔咔.
      db.users.update({query},{"$unset":{"userSex":1}}) --删除这个键,当然 value 也被删了.
      db.users.update({query},{"$inc":{"score":50}}) -- 跟查询到的 user 的分数加 50,清华北大不是梦. 只能作用于 number 类型.
      db.users.update({query},{"$push":{"userCard":"ICBC"}}) -- 为用户添加一个银行卡.定个小目标,日赚一个亿 哇咔咔.
      db.users.update({"money":{"$ne":"0"}},{"$push":{"money":"50000000000000000"}) -- 如果你的钱在库中为 0,你可以用这种方式把它加进去,而且是数组哦.
      db.users.update({query},{"$addToSet":{"cardId":{"4232422424442442424"}}}) -- 如果你忘记了你的卡号是不是已经被保存在库中了,可以用这种方式将卡号再放进去一次,如果存在就不做任何操作,如果不存在就加一个卡号.真土豪,自己几张卡都记不清了.
      db.users.update({query},{"$addToSet":{"cardId":{"$each":["cardId1","cardId2"]}}}) -- 如果你忘记的卡太多,就一次性这样玩吧.每一个不存在库中的卡号都能被添加哦.
      db.users.update({query},{"cardId":{"$pop":{key:1}}})
      -- 删除一个卡号,最近消费有点高啊,竟然把卡都刷废了.
      db.users.update({query},{"$pull",{"cardId":1})
      -- 删除匹配项,会将所有的匹配到的数据删除掉.
      db.users.update({query},{"$inc":{"userInfo.0.money":1}})-- 数据数据里面包含 json,先找到数据的数组下标,然后找到对应字段,进行原子+1
      db.users.update({query},{"$inc":{"cardMoney":20}},true) --upsert 懂了吗?
      db.users.update({query},{$set:{"gift":"Happy birthday"}},false,true) false 代表不是 upsert,不用插入文档,true 代表查到的都更新
      db.users.save({bson}) --save 是一个 shell 函数,可以在文档不存在时插入,存在时更新.它只有一个参数(文档),if document contain _id, it will be upserted,else it will be insert.
      db.update({"_id":"ObjectId()"},x) --if you don`t want to use save method, you can do same thine by it.
      db.update({query},{$set:{column:value}},false,true) -- By default,The update operation updates only the first document found. --默认情况下,更新操作只会更新查找到的第一个文档,可以在 update 方法中第四个值传 true 来更新多个文档.

      ```

    - **修改器速度**
      有的修改器运行速度很快,例如 \$inc,因为不需要改变文档的大小,但是数组修改器更改了文档的大小,就会慢一些(_\$set 能在文档大小不发生改变时立即修改,否则性能会有所下降._).
      MongoDB 预留了一些补白给文档,来适应大小变化(_事实上,系统会根据文档通常的大小变化情况来相应的调整补白的大小._),但是要是超出了原来的预留空间,最后还是要分配新的空间.空间分配会减慢速度,也会随着数组变长,MongoDB 也会因为需要更长的时间遍历,对每个数组的修改也会慢下来.

  - ### <p id="3_4">瞬间完成</p>
    上面讨论的插入更新删除操作都是瞬间完成的,也就是说客户端只管提交,不管返回结果.这样就导致我们无法知道数据是否被成功操作.(_离弦之箭_),这个特点的优点很明显,速度快,这些操作都会非常快地执行,它只会受客户端发送的速度和网络速度的制约.如果出现服务器崩溃等异常情况,客户端还是会发送写操作到服务器的,完全不理会到底有没有服务器.
    安全的代价就是性能,即便忽略了客户端处理异常的开销(_不同语言的开销不一样,但一般都不是轻量级的_),等待数据库响应本身的时间比只发送消息的时间多一个数量级.所以,应用程序需要权衡数据的重要性(_以及丢失后的后果_)及速度需求.
    - 如果不考虑安全性的话,就采用离弦之箭的方式,使用场景(_日志等对数据完整性有要求的方面_).
    - 想要活的稍长一点,就把重要的数据(账号,信用卡号,电子邮件)用安全的方式操作,其余的数据就是采用离弦之箭的方式.
    - 安全操作不仅能应付世界末日的场景,也可以用来调试数据库的一些奇怪场景,这样可以避免很多常见的数据库错误.
  - ### <p id="3_5">请求和连接</p>
    数据库会每一个 MongoDB 数据连接创建一个队列,存放这个连接的请求.
    注意,每个连接都有单独的队列,要是有两个 shell ,就有两个数据库连接.在一个 shell 中执行插入,另一个不一定能够看到,But,in the same shell,you can see the data changes made by the last connection. (_但是,在同一个 shell 中,你可以看到上次连接对数据的更改._)
    使用 Java 连接池的时候要特别注意这个事情,因为连接池和服务器建立了多个连接,并将请求分散到这些连接中,好在提供了一些机制来确保一系列的请求均由一个连接来处理.

- ## <p id="4">Query</p>
  - ### <p id="4_1">find 简介</p>
    MongoDB 中使用 find 进行查询.查询就是返回一个集合中文档的子集.
    > db.collectionName.find({query});
    - **指定返回的键**
      > db.collectionName.find({query},{"userName":1,"email":1})
      > db.collectionName.find({query},{"userName":0}) _排除某个键_
    - **限制**
      查询文档的值必须是常量.
  - ### <p id="4_2">查询条件</p>
    查询不仅能像前面说的那样精确匹配,还能匹配更复杂的查询条件,比如范围,or 子句和取反.
    - **查询条件**
      \$lt,\$lte,\$gt,和\$gte 都是全部的比较操作符,分别对应<,<= > and >= 可以组合起来以便查找一个范围的值.
      > db.collectionName.find("key":{"\$gte":value(Integer/date/string/double),"\$lte":value(integer/date/string/double)})
      > 对于文档的键值不等于某个特定值的情况下,就要使用另外一个条件操作符"\$ne"
      > db.collectionName.find("key":{"\$ne":"value"/value}) _查询某个 key 的值不等于 value 的文档_
    - **OR 查询**
      MongoDB 中有两种方式进行 or 查询."\$in" 可以用来查询一个键的多个值,"\$or"更通用一些,用来完成多个键值的任意给定值.
      > db.collectionName.find({"key":{"$in":[value1,value2,value3]}}) _查询某个 key 的 value 是否是其中一个,并返回符合条件的文档._
      > db.collectionName.find({"key":{"\$nin":[value1,value2,value3]}}) _查询某个 key 不包含这些 value 的文档._
      > db.collectionName.find({"\$or":[{"key1":"value1"},{"key2":"value2"}])
    - **\$not 查询**
      \$not 是元条件句,可以用在任何其他条件之上,
      > db.users.find({"key":{"\$not":value})
  - ### <p id="4_3">特定于类型的查询</p>
    - **null**
      null 不仅会匹配值为 null 的文档,还会匹配不存在这个键的文档.
      如果仅仅是想要匹配值为 null 的文档,还要判断当前键是否存在
      > db.c.find({"key":null})
      > db.c.find({"key":{"\$in":[null],"\$exists":true}})
    - **正则表达式**
      正则表达式能够灵活有效地匹配字符串.
      > db.collectionName.find({"key":regular})
    - **查询数组**
      查询数组中的元素非常简单.
      > db.collectionName.find({"key":"value"})
      > db.collectionName.find({"key":{"\$all":["value1","value2"]}}) 查询包含所有值的文档.
      > db.collectionName.find({"key":{"\$size":Integer}}) 查询指定长度的数组,但不能与范围查找共同使用.
      > db.collectionname.update("\$push":{"fruit":"strawberry"},{"$inc":{"size":1}}) 可以使用一个键值维护数组的增减.
      > db.collectionName.find({query},{"key":{"\$slice":10}})指定字段返回数组的前 10 条数据.
      > db.collectionName.find({query},{"key":{"\$slice":[23,10]}}) 从第 23 个开始,向后查找 10 个.返回第 24~33 个元素.
    - **查询内嵌文档**
      > db.people.find({"name":{"first":"joe","last":"schmoe"}}) 查询整个内嵌文档,如果顺序不对,或者查询条件没有指定全部的键,就会造成查询不到.
      > db.people.find({"name.first":"Joe","last":"Schmoe"})
      > db.blog.find({"comments":{"\$elemMatch":{"author":"joe","score":{"\$gte":5}}}})
  - ### <p id="4_4">\$where</p>
    $where 可以执行 JavaScript 子句,没用过,不熟悉.效率很低,不建议使用,要先把 bson转换成 JavaScript 对象,然后通过\$where 的表达式运行.
  - ### <p id="4_5">游标和游标内幕</p>
    - **游标**
      从 shell 中创建一个游标,首先要对集合填充一些文档,然后对其执行查询,并将结果分配给一个局部变量.
      > var cursor = db.collection.find();
      > 迭代结果:
      ```JavaScript
      while (cursor.hasNext()){
      obj = cursor.next();
      //do something.
      }
      // 游标还实现了迭代器接口,所以可以在 foreach循环中使用.
      cursor.foreach(function(x){
      //do something
      });
      ```
      当调用 find 的时候,shell 并不会立即查询数据库,而是等待真正要求获得结果时才发送查询,这样在执行之前可以给查询附加额外的选项.基本上所有游标对象的方法都返回游标本身.
    - **游标内幕**
      看待游标有两种角度:客户端游标以及客户端游标表示的数据库游标.
      在服务器端,游标消耗内存和其它资源.游标遍历尽结果后,或者客户端发送过来消息要求终止的,数据库将会释放这些资源.所以要尽量保证尽快释放游标.以下情况会导致游标终止并被清理:
      1. 游标完成匹配结果的迭代时.
      2. 游标在客户端已经不在作用域内了,驱动会向服务器发送专门的消息,让其销毁游标.
      3. 即便用户没有迭代完成所有的结果,并且游标还在作用域内,10 分钟不使用,数据库游标也会自动销毁.
- ## <p id="5">索引</p>

  - ### <p id="5_1">索引简介</p>

    MongoDB 的索引几乎与传统的关系数据库索引一模一样,所以如果已经掌握了那些技巧,可以忽略本章节.

    > db.people.ensureIndex({"username":1}) 创建索引

    对某个键创建的索引会加速对该键的查询.然而,对于其他查询可能没有帮助,即便是查询了包含了被索引的键.下面的查询就不会从先前简历索引中获得任何的性能提升.

    > db.people.find({"date":date1}).sort({"date":1,"username":1})

    服务器必须查找整本书找到想要的日期.这个过程称作表扫描,就是在没有索引的书中找内容,要从第一页开始,从前翻到后.通常来说,要尽量避免让服务器做表扫描,因为当集合很大时会非常慢.对于上面的查询,应该建立日期和用户名的索引.

    > db.ensureIndex({"date":1,"username":1})

    传递给 ensureIndex 的文档其形式与传递给 sort 的文档形式一样:一组值微微 1 或者-1 的键,表示索引创建的方向.若索引只有一个键,则方向无关紧要.单键索引有点像一个按照字母顺序组织的书籍索引:无论从 A 到 Z,还是从 Z 到 A,显然都要从 M 开始查找.

    - **扩展索引**
      假设我们有个集合,保存了用户的状态信息.现在想要查询用户和日期,取出某一用户最近的状态.以我们目前所学,我们会像下面这样创建一个索引:

      > db.status.ensureIndex({user:1,date:-1}) 排序方式 先根据用户名的 acci 码值进行排序,然后根据日期排序.

      这会使对用户和日期的查询非常快,但是并不是最好的方式. 如果应用会有数百万的用户,每人每天有数十条状态更新.若是每条用户状态的索引值占用类似一页纸的磁盘空间,那么对于每次"最新状态"的查询,数据库都会将不同的页载入内存.若是站点太热门,内存放不下所有的索引,就会非常慢.
      要是改变索引的顺序,变成{date:-1,user:1},则数据库可以将最后几天的索引保存在内存中,可以有效减少内存交换,这样查询任何用户的最新状态会快很多. **根据业务本身去思考索引的创建顺序**
      建立索引前最好先考虑到如下问题,并提出方案

      - 1. 会做什么样的查询?其中哪些键需要索引?
      - 2. 每个键的索引方向是怎样的?
      - 3. 如何应对扩展?有没有种不同的键的排列可以使常用数据更多地保留在内存中?
           要是能满足上述场景,说明你的索引创建的没有问题.

    - **索引内嵌文档中的键**
      为内嵌文档的键和普通的键创建索引没有什么区别.

      > db.blog.ensureIndex({"comments.date":1})

      对内嵌文档的键索引与普通的索引并无差异,两者也可以联合组成复合索引.

    - **为排序创建索引**
      随着集合的增长,需要针对查询中大量的排序做索引.如果对没有索引的键调用 sort,MongoDB 需要将所有数据提取到内存来排序.因此,可以做无索引排序是有上限的,那就是不可能在内存里面做 T 级别数据的排序.一旦集合大到不能在内存中排序,MongoDB 就会报错.
      按照排序来索引以便让 MongoDB 按照顺序提取数据,这样就能排序大规模数据,而不必担心用光内存.
    - **索引名称**
      集合中的每个索引都有一个字符串类型的名字,来唯一表示索引,服务器通过这个名字来删除或者操作索引,索引名为字段名 1dir1\_字段名 2_dir2 这种形式,也可以采用通过 ensureIndex 的选项来指定自定义的名字.

      > db.foo.ensureIndex({"a":1,"b":1,"c":1,...,"z":1},{"name":"indexName"})

      **索引名称有字符个数的限制,所以特别复杂的索引在创建时一定要使用自定义名字.可以用 getLastError 来检查索引是否成功创建了或者未成功创建的原因.**

  - ### <p id="5_2">唯一索引</p>

    唯一索引可以确保集合的没一个文档的指定键都有唯一值.

    > db.people.ensureIndex({"userName":1},{"unique":true})

    \_id 也是唯一索引.切记 **被 unique 的字段只能有一个包含 null 的字段**
    **消除重复**
    在创建唯一索引的时候,已经确认该字段在每个 document 的值都是唯一的,如果不能保证唯一,可以用一下方式清除重复的值.

    > db.people.ensureIndex({"userName":1},{"unique":true,"dropDups":true}) 这种做法非常粗暴,如果数据很重要的话,还是写个代码做个预处理比较好.
    > **复合唯一索引**
    > 创建复合唯一索引的时候,单个键的值可以相同,只要所有键的组合起来不同就好.如果数据中已经存在复合键相同的值,再次插入会提示存在重复键.

  - ## <p id="5_3">使用 explain 和 hint</p>

    explain 是一个非常有用的工具,会帮助我们获得查询方面诸多有用的信息.只要对游标调用该方法,就可以得到查询细节.explain 会返回一个文档,但不是游标本身,这是与多数游标不同之处.

    > db.foo.find().explain();

    explain 会返回查询使用的索引情况(如果有的话),耗时及扫描文档数的统计信息.
    example:

    > db.people.find({"age":18}).sort({"username":1})

    这种时候如果搞不准数据库在查询时到底有没有索引,或者到底效率如何.使用 explain 就会得到当前查询所使用的索引,消耗了多少时间,以及数据库需要扫描多少文档才能得到结果.
    **修改索引**

    > db.people.ensureIndex({"userName":1},{"background":true})
    > 建立索引是非常耗时和费力的(_尤其是在数据量很大的时候_).使用{"background":true}选项可以使这个过程在后台完成,同时处理正常请求.要是不包含这个参数,数据库会阻塞建立索引期间的所有请求.(_这对于线上数据是很致命的._)

    思考点:

      <p style="color:red">为何先创建索引在插入文档会比先插入文档再创建文档慢?</p>
     解释:
     先创建索引,然后再插入文档,数据库的操作流程为先保存文档->为当前文档创建索引.
     先插入文档,再创建索引 保存所有文档->为所有文档创建index.

    > db.collectionName.getIndexes(); 查看所有的索引
    > db.collectionName.totalIndexSize();查看所有的索引所占的空间.
    > db.runCommand({"dropIndexes":"foo","index":"\*"}) 删除所有索引,慎用!!!.
