## Learn about mysql:yum:

- ## [Introduction](#1)
  - ### [What is db?](#1_1)
  - ### [Mysql? database client and database server](#1_2)
- ## [what is mysql?](#2)
  - ### [MyISAM](#2_1)
  - ### [InnoDB](#2_2)
  - ### [HEAP](#2_3)
- ## [How to use sql?](#3)
  - ### [Basic sql](#3_1)
  - ### [Advanced sql](#3_2)
- ## [How to optimize your sql?](#4)
  - ### [Create an index](#4_1)
  - ### [How to use table relationships?](#4_2)
  - ### [Query must be careful](#4_3)

# Give me :+1:. Thanks

# My english is not good! hahhha:smiling_imp:

## <p id="1">简介</p>

- ### <p id="1_1">什么是数据库?</p>

  **数据库** 就是一个有一批由一批数据构成的有序集合,这个集合通常保存在一个或多个彼此相关的文件中.这些数据被分门别类的存放在一些结构化的数据表(_tables_)中,而数据又存在种种内在的交叉引用关系.存在于数据表之间的这种关系使数据库又被称为关系(型)数据库. 关系型数据库有以下几个(_mysql_ , _oracle_ _sql server_) :smile:
  **数据表** : 用来存放有关数据的框架结构.这种数据表里的每一行称为数据记录(_data record_),简称记录,每条记录的结构和格式是由人们在定义数据表时决定的.在数据表中,每条记录包含多个字段,每个字段对自己的所存储的数据类型有一定的要求(_example : it is a number field or a string field or a date field and so on. and it must less than maximum limit._)

- ### <p id="1_2">mysql? 数据库客户端还是数据库服务器</p>

  **MYSQL** 我们通常所说的 mysql 一般包含一个客户端(client)和一个服务端(server).
  **_client_** 负责 mysql server 的数据表格(table)的管理,以及 sql 语句的执行和数据表的展示.通俗来讲 mysql-client 是 mysql-server 的管理工具,负责传输用户的 crud 操作.
  **_server_** mysql-server 负责数据的存储,以及 sql 语句的编译和执行.通常所说的 mysql 是包含 client 和 server 的. 通俗来讲 我们的 table 都是由 mysql-server 管理的.

## <p id="2">什么是 mysql?</p>

- ### <p id="2_1">MyISAM</p>
  **introduction _MyISAM_ here**
- ### <p id="2_2">InnoDB</p>
  **introduction _InnoDB_ here**
- ### <p id="2_3">HEAP</p>
  **introduction _HEAP_ here**

## <p id="3">如何使用 sql?</p>

- ### <p id="3_1">基础 sql</p>
  **introduction _basic sql_ here**
- ### <p id="3_2">高级 sql</p>
  **introduction _advanced sql_ here**

## <p id="4">如何优化你的 sql?</p>

- ### <p id="4_1">创建一个索引</p>
  **introduction _index_ here**
- ### <p id="4_2">如何使用表关系</p>
  **introduction _table relationships_ here**
- ### <p id="4_3">小心你的查询</p>
  **introduction _query problem_ here**
