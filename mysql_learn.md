## Learn about mysql:yum:

- ## [Introduction](#1)
  - ### [What is db?](#1_1)
  - ### [Mysql? database client and database server](#1_2)
- ## [what is mysql?](#2)
  - ### [MyISAM](#2_1)
  - ### [InnoDB](#2_2)
  - ### [Use MyISAM or InnoDB?](#2_3)
  - ### [HEAP](#2_4)
  - ### [MySQL data type](#2_5)
- ## [How to use sql?](#3)
  - ### [Basic sql](#3_1)
  - ### [Advanced sql](#3_2)
- ## [How to optimize your sql?](#4)
  - ### [Create an index](#4_1)
  - ### [How to use table relationships?](#4_2)
  - ### [Query must be careful](#4_3)
- ## [Use java to manage your mysql](#5)
  - ### [connect by java](#5_1)
  - ### [use transaction by java to manage you crud](#5_2)

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

**_mysql functions_**:

- **关系数据库系统**
- **客服/服务器体系** MySql 是一种客户/服务器系统,整个系统由一个数据库服务器(MySQL)和任意多个客户(应用程序)构成.客户通过与服务器通信的方式来完成数据查询保存修改等操作.客户既可以与服务器运行在同一台计算机上,也可以运行在另一个计算机上.
- **sql 兼容性** Mysql 支持 sql(Structured Query language,结构化查询语言) 作为自己的数据库语言.SQL 是一种专门用于查询和修改数据库里数据以及对数据库进行管理和维护的标准化语言.(Mysql 遵循最新的 sql 标准)
- **子查询** Mysql 具备了对以下形式的查询进行处理的能力:

```sql
SELECT * FROM TABLE1 WHERE X IN (SELECT Y FROM TABLE2)
```

- **视图(view)** 简单地说,视图(view) 与一个被视为数据库对象并且能反应出数据库某个特定方面的 sql 查询关系. start at mysql 5.0
- **存储过程** 存储过程(stored procedure,简称 SP)用于处理被存储在数据库系统内部的 SQL 代码.存储过程常见用途是把一系列特定的连续步骤--如插入删除 and so on 简化为一个函数调用.存储过程向编写客户软件的程序员提供了这样一种便利;在程序里只需要调用一个存储过程就可以完成一系列操作,用不着直接与数据表打交道了.存储过程可以提高工作效率.mysql 5.0 开始支持存储过程.(慎用)

  1. 优点:

     1. _在生产环境下可以通过直接修改存储过程的方式修改业务逻辑(or bug),而不是重启应用服务器.但这个操作是不安全的,很多人在修改存储过程后没有经过严格的测试,可能导致出现脏数据,严重可能导致数据丢失._
     2. _执行速度快,存储过程在经过编译之后比单独一条一条执行要快.但这个效率几乎可以忽略不计.如果做大量数据的导入,同步等操作,我们可以采用其他手段_.
     3. _减少网络传输,尤其是在高并发情况下.存储过程直接在 mysql-server 中执行,所有的数据访问都在服务器内部进行,不需要传输到其他端.但基本上用户服务和数据库在同一个子网下,大数据的访问其实是受影响的是硬盘的速度,而不是网速(可使用现在的缓存数据库解决)_
     4. _方便 DBA 优化,所有的 sql 集中在一个地方,dba 会非常高兴,这一点也算是 ORM 的软肋._
        > <font style="color:red;">还不太了解 CQRS 框架的思想</font>

  2. 缺点:

     1. _SQL 本身是一种结构化查询语言,加上一些控制(赋值,循环 or 异常处理),但不是 OO 的,本质上还是过程化.面对复杂的业务逻辑,过程化语言会很吃力,即只能应用在逻辑简单的业务上._
     2. _不便于调试,SP 基本上没有很好的调试器,很多时候都是采用 print 进行调试,但这种调试对于几百行的存储过程非常不合实际._
     3. _没办法应用缓存.虽然全局临时表的方法可以做缓存,但这种方式加重了数据库的负担.如果缓存并发严重,要经常加锁,严重影响数据库效率._
     4. _无法适应数据库的切割(水平或者垂直切割),数据库切割之后,存储过程并不知道需要的数据存在哪个数据库中,在现在的业务场景中有非常大的局限性_.

- **触发器** 触发器是由数据库服务器在一些特定的数据库操作(_insert_ _update_ and _delete_ )过程中自动执行的一组 sql 命令. mysql supports it from 5.1.
- **全文搜索** 全文搜索(full-text search)简化并加快了对文本字段内单词的搜索操作.
- **镜像复制** 镜像复制(_replication_) 允许数据库管理员把某个数据库的内容动态地复制到其他计算机中,这样做的理由有两个:避免因为系统故障而中断服务,二是为了加快数据库查询速度.
- **事务** 事务是指把多个数据库操作当成一个整体(块)来对待.数据库确保操作要么全部执行要么全部不执行.即时在事务过程中出现停电,计算机崩溃或其它灾难事件发生也是如此.事务机制还可以让程序员安全地,及时地终止一组命令的执行(_并把数据库恢复到这组命令执行前的状态_) 目前 mysql 中只有 INNODB 支持事务机制.
- **外键约束** 它们是程序员为了确保彼此关联的数据表里没有找不到目标的交叉引用而定义的一些规则.MySQL 系统中的 Innodb 数据表都支持外键约束.
- **GIS 函数** MySQL 从 4.1 版本开始支持二维地理数据的存储和处理.因此 MySQL 适合用来开发 GIS (_Geographic Information System 地理信息系统_)应用程序
- **程序设计语言** 在开发 MySQL 应用程序的时候,有一大批的 api(_application programming interface 应用编程接口_) 和软件开发库可供使用.本文只讨论 java.
- **ODBC** MySQL 支持 ODBC 接口 connector/ODBC.能够在 Microsoft Windows 环境里运行的常用编程语言.**_在 unix 系统中没有必要_**.
- **平台独立性** MySQL 客户应用程序可以在多种操作系统下运行,Mysql 本身(_即 mysql-server_) 也可以在多种操作系统中运行.
- **速度** 人们普遍认为 Mysql 是一个非常快的数据库程序,有大量的性能测试报告支持这一结论.

**_连接 mysql_** : `mysql -u name -p password -h host -P port -defautl-character-set=encode databasename`

**_mysql-client_** 客户端操作

```SQL
\c clear 放弃正在输入的命令
\h help 显示一份命令清单
\q exit or quit 退出 mysql 程序,Unix/linux 用户还可以用使用 CTRL-D 快捷键
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

**_数据库设计概论_** 一切应用程序的第一阶段工作都是对数据库进行设计,这项工作的好坏对应用程序执行效率的高低,前期编程和后期维护工作的难易程度以及能否在今后灵活修改设计方案等问题将产生巨大的影响.在设计阶段埋下的隐患会在其后给开发者和使用者带来无穷的烦恼和痛苦.数据库设计方案的好坏与设计者的知识和经验是否丰富有着很大的关系.

- ### <p id="2_1">MyISAM</p>
- **MyISAM** 数据类型的特点是成熟,稳定和易于管理.只要没有特殊理由选择其他类型,就应该选用这个类型.这种数据表类型在 MySQL 内部又被分为两种,MySQL 将自行选择它认为最适当的一种来使用:
- **MyISAM Static(_静态 MyISAM_)**: 如果数据表里的数据列各自都有预先定义好的固定长度,MySQL 服务器将自动选择这种数据表类型.这种表的数据存取效率非常高,而且即使对数据表的修改非常频繁(_suck it in lots of INSERT,UPDATE and DELETE command_) 也是如此.another,这种数据库的安全性非常高,即使出现文件受损或其它问题,数据记录的提取和恢复工作也比其它类型的数据表容易.
- **MyISAM Dynamic(动态 MyISAM)**: 如果数据表中有且只有一个 VARCHAR,xxxText 或 XXBlob 字段.MySQL 将自动选择这种数据表类型.与静态 MyISAM 类型相比,这种类型的突出优点是数据表的空间需求往往小的多;存储字符串和二进制对象需要的字节数仅仅使他们的实际长度(再加上几个字节的开销).这就是数据记录可能不都是同样的长度.这样一来,如果记录被修改了,它们在数据库文件里的存储位置就可能发生变化并在原先的位置留下一个空洞.于是,在数据库文件里,同一条记录的各个字段就不一定存储在一个连续的字节块里,而是会散步在各处,当被编辑的数据表变得越来越碎片化后,数据的存取时间就会变得越来越长.因此这种类型人们经常使用 SQL 命令 _OPTIMIZE TABLE_ 或者某个优化工具进行碎片整理
- **MyISAM Compressed(压缩 MyISAM)**:动态和静态的 MyISAM 数据表都可以用 myiasmchk 工具压缩.这种压缩的效果往往可以使数据表的空间占用量减少到原来的一半以下(_与数据表的具体内容有关_).虽说以后在读取数据记录的时候需要解压缩,但在某些场合,数据表的访问速度甚至更快 - 低速硬盘+高速 cpu 的系统上体现尤其明显.压缩 MyISAM 最大的缺点就是不能对数据进行修改.
- ### <p id="2_2">InnoDB</p>

  > > MyISAM 的更新换代-InnoDB

- **事务** InnoDB 数据表里的数据库操作可以被执行为一个事务.这将允许把几条存在内在逻辑关系的 sql 命令当做一个整体来执行.如果执行时发生错误,所有的命令(而不仅仅是触发错误的命令) 都将失效.就好像从未执行过这些命令一样.another,事务机制还能改善数据库应用程序的安全性.
  > _MySQL 支持 ANSI-SQL/92 标准里定义的全部 4 中事务级别(READ UNCOMMITTED(读未提交),READ COMMITTED(读提交),REPEATABLE READ(重复读),SERIALIZABLE(顺序))_
- **数据行级锁定机制** 在执行一个事务的时候,InnoDB 数据表的驱动程序使用的是它自己内建的数据行级锁定机制(_不是 MySQL 提供的数据表级锁定机制_).也就是说,在事务执行过程中,数据表是不会被锁定的,其他用户仍可以访问它,被锁定的只是正在接受事务处理的数据记录(_而 MyISAM 数据表在执行 lock table 命令期间会将整个表锁定_).如果有许多用户正在同时对一个大数据表进行修改,数据行级锁定机制将会大大提高人们的工作效率.
  > InnoDB 驱动程序能够自动识别"死锁"现象(_两个进程各自占用着一项 对方需要的资源,同时又都在等待对方释放所占用的资源,结果是谁也不能继续执行_),并自动终止两个进程中的一个.
- **外键约束条件** 如果在数据表之间定义了关系,InnoDB 驱动程序将自动保证数据表的引用一致性在执行过 delete 后还能保持.也就是说不可能出现数据表 A 里的一条记录引用了数据表 B 里一条已经不复存在的记录的问题.专有名词:**_外键约束条件_**
- **崩溃恢复** 在发生崩溃后,InnoDB 数据表能够迅速地自动恢复到一个稳定可用的状态(_前提是计算机的文件系统没有被破坏_).
- **<span style="color:red">问题和缺陷</span>**

  - **表空间的管理** MyISAM 数据表驱动程序把每个数据表分别保存在它自己的文件里,这些文件会根据实际情况增大或缩小.InnoDB 数据表驱动程序却是把所有的数据和索引都保存在一个表空间(tablespace)里.表空间由一个或多个文件构成,它们形成了一个虚拟的文件系统.这些文件在创建之后只能增大不能缩小.在管理 InnoDB 数据表时,mysqldump 命令的使用频率要比管理 MyISAM 数据表的时候高很多.
  - **数据记录的长度** InnoDB 数据表中的单条数据记录最多可以占用 8000 个字节的空间.这一限制并不包括 TEXT 和 BLOB 数据列,它们只有前 512 个字节是随其他数据列一起存储在数据库里的,超过这个长度的数据将被存放在表空间的其他页面.
  - **存储空间占用量** InnoDB 数据表的空间占用量要比同样内容的 MyISAM 数据表大很多(_最多时会有后者的两倍,这个先不做拓展,我自己也没有看过 InnoDB 的存储方式_)
  - **全文索引** InnoDB 数据表不支持全文索引
  - **GIS 数据** InnoDB 数据表不能用来保存二维地理数据
  - **COUNT 问题** 因为支持事务,InnoDB 数据表驱动程序在统计一个数据表里的记录个数时经常会遇到困难,MyISAM 会记录表中的数据量,而 Innodb 在 count(\*)的时候要逐行去统计,所以在 InnoDB 数据表上执行
    ```sql
    SELECT COUNT(*) FROM TABLE -- 命令的速度要比在 MyISAM 上慢很多
    ```
  - **数据表锁定** Innodb 驱动程序在执行事务时使用的是它自己的锁定算法. 因此要尽量避免使用 lock table ... read/write 命令.应该使用 select ... in share mode 或 select ... for/update 命令,它们将只锁定个别记录而不是锁定整个表.
  - **MySQL 数据表** 用于管理 MySQL 访问权限的 mysql 数据表不能被转化为 Innodb 数据表,必须使用 MyISAM 格式.
  - **许可证费用** 在商用 MySQL 许可证里增加 Innodb 支持将收取双倍的费用.

- ### <p id="2_3">使用 MyISAM 还是 InnoDB?</p>

  - 可以把数据库里的不同数据表设置为不同的类型,也就是说 MyISAM 数据表和 InnoDB 数据表可以同时存在同一个数据库里,这就使用户能够根据每一张表的内容数据和具体用途为它们分别选定最佳的数据类型.
    - 如果希望减少数据的空间和时间占用,MyISAM 数据表应该是首选.从另一个方面讲如果应用程序需要使用事务,需要更高的安全性,或者需要同时多个用户对数据表进行操作,InnoDB 数据表更值得考虑.

- ### <p id="2_4">HEAP</p>
  HEAP 数据表只存在于内存中,它们使用了一个散列索引(hash index),所以数据记录的存取速度非常快.HEAP 数据表主要充当临时数据表.与普通的数据表相比,HEAP 数据表在功能上受到了许多限制,其中最重要的是不允许使用 xxxBlob,xxxText,只允许使用 = 和 <=> 操作符来搜索记录(不允许使用 &lt;,&gt; &lt;= 或 &gt;= 操作符);不支持 auto_increment 属性;只允许对 not null filed 进行索引.
  与普通的数据表相比,HEAP 数据表适用于数据量相对较小,但对访问速度要求很高的场景.(HEAP 数据表只存在于内存),所以一旦 MySQL 停止运行,HEAP 数据表也会消失.
  > MySQL 还支持其他类型的数据表,因为不常用,本文不做概述.
- ### <p id="2_5">MySQL 数据类型</p>
  在默认情况下,INT 数据类型包括正数 and 负数,但如果给 INT 定义了 UNSIGNED 属性,它的取值范围仅限于正数,对 unsigned 数据列做减法计算,返回值仍将是 unsigned 整数.
  | MySQL 数据类型 | 含义|
  |----------------------------|------------------|
  |TINYINT(m)| 8 位整数(_1 个字节,-128~+127_),可选参数 m 给出的是 select 查询结果中的数据列宽度(Maximum Display Width,最大显示宽度),对取值范围没有影响. |
  |SMALLINT(m)| 16 位整数(_2 个字节,从-32768~+32767_)|
  |MEDIUMINT(m)|24 位整数(_3 个字节,从-8388608~+8388607_)
  |INT(m),INTEGER(m) | 32 位整数(4 个字节,-2147483648~+2147483467)|
  |BIGINT(m) |64 位整数(8 个字节,~-2^~64 \~ ~2^~64 - 1)|
  |SERIAL | BIGINT AUTO_INCREMENT NOT NULL PRIMARY KEY 的简写
  > 在一个整数字段的定义里,可以选择为它定义一个数据列宽度,比如 INT(4).这个参数表示最大显示宽度,它可以帮助 mysql 和各种用户操作界面把查询结果以一种整齐易读的格式显示.

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

## <p id="5">使用 java 管理你的 MySQL</p>

- ### <p id="5_1">java 连接 mysql</p>
  **write your java code here**
- ### <p id="5_2">使用 java 对 MySQL 的 curd 进行事务管理</p>
  **write your java code here**
