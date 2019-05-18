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
  **_client_** 负责 mysql server 的数据表格(table)的管理,以及 sql 语句的执行和数据表的展示.通俗来讲 mysql-client 是 mysql-server 的管理工具,仅限于将把数据库操作命令发送给 mysql-server 服务器和把那些命令的执行结果显示给用户.
  **_server_** mysql-server 负责数据的存储,以及 sql 语句的编译和执行.通常所说的 mysql 是包含 client 和 server 的. 通俗来讲 我们的 table 都是由 mysql-server 管理的.

## <p id="2">什么是 mysql?</p>

**MySQL** 是一种客户\服务器体系的数据库系统,它的服务器端部分在启动运行后是不提供人机交互界面的,所以终端用户无法直接使用 msql,只能通过 mysql 客户端或者 WEB 站点访问数据库进行管理以及 crud 操作.

**_连接 mysql_** : `mysql -u name -p password -h host -P port -defautl-character-set=encode databasename`

**_mysql-client_** 客户端操作

```SQL
\c clear 放弃正在输入的命令
\h help 显示一份命令清单
\q exit or quit 退出 mysql 程序,Unix/linux 用户还可以用使用 CRTL-D 快捷键
\s status 查看 mysql 服务器的状态信息
\T[f] tee[filename] 把输入输出记载到指定文件里
\t notee 停用 tee 功能,此后,随时可以用 tee or \t 命令 把输入和输出继续记录到刚才的指定文件中,用不着再给出文件名
\u [db] use database 另行指定一个默认数据库
\. fn source filename 读取并执行某给定文件里的 sql 命令.那些命令以分号分隔
```

**_mysql-client_** 用 mysql 处理 sql 文件

```sql
mysql -u root -p dbname < backupfile.sql --将数据库导出为 sql 文件
```

**_mysqladmin_** 命令用法:

```sql
mysqladmin -uroot -p create newdb --创建一个数据库
mysqladmin -uroot -p drop olddb --删除一个数据库
```

**_mysqldump_** 数据备份:

```sql
mysqldump [options] dbname > backupfile.sql -- -u -h -p 此外,还可以通过许多其他的选项来调控备份工作的细节.mysqldump 默认编码为 utf8,如果想要指定字符集,可以使用 -default-character-set=[encoded_mode] 选项来设置
```

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
