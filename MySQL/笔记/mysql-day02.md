# mysql-day01

### 1.数据库发展历史

数据库技术是应数据管理任务的需要而产生的。

在应用需求的推动下,在计算机硬件、软件发展的基础上，数据管理技术经历了人工管理、文件系统、数据库系统三个阶段。

1)人工管理阶段

20世纪50年代中期以前,计算机主要用于科学计算.当时硬件的状况是,只有纸带、卡片、磁带，没有磁盘等直接存取的存储设备；软件的状况是，没有操作系统，没有管理数据的专门软件。

2)文件系统阶段

20世纪50年代后期到60年代中期,这时硬件方面已经有了磁盘、磁鼓等直接存取存储设备。软件方面，操作系统中已经有了专门的数据管理软件，一般称为文件系统来处理方式上不仅有了批处理而且能够联机实时处理。

3)数据库系统阶段

20世纪60年代后期以来,计算机管理的对象规模越来越大,应用范围越来越广,数据量急剧增长,同时多种应用、多种语言互相覆盖的共享数据集合的要求越来越强烈。这是硬件已有大容量磁盘，硬件价格下降；软件价格则上升，为编制和维护系统软件及应用程序所需的成本相对增加，数据库技术便应运而生。



|                | 人工管理阶段          | 文件系统阶段             | 数据库系统阶段                                             |
| :------------: | --------------------- | ------------------------ | ---------------------------------------------------------- |
|    应用背景    | 科学计算              | 科学计算、数据管理       | 大规模数据管理                                             |
|    硬件背景    | 无直接存取存储设备    | 磁盘、磁鼓               | 大容量磁盘、磁盘整列                                       |
|    软件背景    | 没有操作系统          | 有文件系统               | 有数据库管理系统                                           |
|    处理方式    | 批处理                | 联机实时处理、批处理     | 联机实时处理、分布处理、批处理                             |
|  数据的管理者  | 用户(程序员)          | 文件系统                 | 数据库管理系统                                             |
| 数据面向的对象 | 某一应用程序          | 某一应用                 | 现实世界（一个部门、企业、跨国组织等）                     |
| 数据的共享程度 | 无共享,冗余度极大     | 共享性差,冗余度大        | 共享性高,冗余度小                                          |
|  数据的独立性  | 不独立,完全依赖于程序 | 独立性差                 | 具有高度的物理独立性和一定的逻辑独立性                     |
|  数据的结构化  | 无结构                | 记录内有结构、整体无结构 | 整体结构化,用数据模型描述                                  |
|  数据控制能力  | 应用程序自己控制      | 应用程序自己控制         | 有数据库管理系统提供数据安全性、完整性、并发控制和恢复能力 |

### 2.数据库常用术语、概念

数据:可以被计算机识别的信息.

数据库:存储数据

数据库管理系统:组织管理数据库

### 3.常用数据库对比

几种主流关系型数据库对比：

- Oracle：收费的大型数据库，Oracle公司的产品。Oracle收购了SUN公司，收购MySQL。
- MySQL：开源免费的小型数据库，已经被Oracle收购了，6.x版本也开始收费。
- DB2：IBM公司的数据库产品，收费的。常应用在银行系统中。
- SQL Server：Microsoft公司收费的中型数据库。C#、.Net等语言常使用。
- SQLite：嵌入式的小型数据库，应用在手机端。

| 数据库    | 优势                                                         | 缺点                                              |
| --------- | ------------------------------------------------------------ | ------------------------------------------------- |
| MySQL     | 1）MySQL性能卓越，服务稳定，很少出现异常宕机。<br/>2）MySQL开放源代码且无版权制约，自主性及使用成本低,版本更新较快。<br/>3）MySQL软件体积小，安装使用简单，并且易于维护，安装及维护成本低。<br/>4）MySQL支持多种操作系统，提供多种API接口，支持多种开发语言，特别对流行的PHP语 | 数据量大时处理性能不及Oracle                      |
| SqlServer | 1)真正的客户机/服务器体系结构<br/>2)图形化的用户界面，使系统管理和数据库管理更加直观、简单<br/>3)丰富的编程接口工具，为用户进行程序设计提供了更大的选择余地<br/>4)与WinNT完全集成，利用了NT的许多功能，如发送和接受消息，管理登录安全性等，SQL Server也可以很好地与Microsoft  BackOffice产品集成。<br/>5)提供数据仓库功能，这个功能只在Oracle和其他昂贵的DBMS中才有。 | 只能在Windows系统下运行                           |
| Oracle    | 1）Oracle 能在所有主流平台上运行<br/>2）Oracle 性能高，保持开放平台下TPC-D和TPC-C世界记录  <br/>3）获得最高认证级别的ISO标准认证 | 价格昂贵                                          |
| SQLite    | 1）零配置，SQlite3不用安装,不用配置，不用启动，关闭或者配置数据库实例。当系统崩溃后不用做任何恢复操作，再下次使用数据库的时候自动恢复 <br/>2）SQLite是被设计成轻量级，自包含的，不依赖服务进程  <br/>3）采用无数据类型，所以可以保存任何类型的数据，SQLite采用的是动态数据类型，会根据存入值自动判断<br/>4）可移植，可运行在不同操作系统上 | 数据量不宜过大，sql语句执行相比其他数据库效率较低 |

几种主流非关系型数据库对比：

| 数据库  | 优势                                                         | 缺点                                                         |
| ------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Redis   | 1）支持内存缓存，这个功能相当于Memcached<br/>2）支持持久化存储，这个功能相当于MemcacheDb，ttserver<br/>3）数据类型更丰富。比其他key-value库功能更强<br/>4）支持主从集群，分布式<br/>5）支持队列等特殊功能 |                                                              |
| MongoDB | 1）弱一致性（最终一致），更能保证用户的访问速度<br/>2）查询与索引方式灵活，是最像SQL的Nosql<br/>3）内置GridFS，支持大容量的存储<br/>4）内置Sharding，支持复制集、主备、互为主备、自动分片等特性<br/>5）第三方支持丰富 6）性能优越 | 1）单机可靠性比较差 2）磁盘空间占用比较大<br/>3）大数据量持续插入，写入性能有较大波动 |

架构设计有一句流行语：不以业务模型为基础的架构设计都是耍流氓。同样数据库选型也应该**根据自己业务需求选择最适合自己的数据库**。

数据库排名:https://db-engines.com/en/ranking

### MySQL简介

MySQL是一个小型的关系型数据库,开发者为瑞典MySQL AB公司.这个公司在2008年被Sun公司收购,2009年Sun公司又被Oracle收购.所以现在MySQL属于Oracle公司.

体积小、速度快、开放源码、免费等原因，被广泛应用于中小型网站

目前 MySQL 被广泛地应用在 Internet 上的中小型网站中。由于其体积小、速度快、总体拥有成本低，尤其是开放源码这一特点，使得很多公司都采用 MySQL 数据库以降低成本。

MySQL 数据库可以称得上是目前运行速度最快的 SQL 语言数据库之一。除了具有许多其他数据库所不具备的功能外，MySQL 数据库还是一种完全免费的产品，用户可以直接通过网络下载 MySQL 数据库，而不必支付任何费用。

#### 登录-退出

#### 登录

1.mysql -u root -p

2.mysql -u root -p12345

3.mysql -u root  -h127.0.0.1 -P3306 -p1223456

#### 退出

exit

#### 启动服务

net start mysql

此电脑->属性->服务->mysql->启动

win+r:services.msc



## SQL

struct query language:结构化查询语言

定义了操作所有关系型数据库的规则.



## show语句

1.show databases;查看所有数据库	

​	use dbname 选择一个数据库

2.show tables;查看数据库下所有的数据表

3.show columns from tbname;查看数据表的列信息

​	desc tbname

4.show status;查看系统运行状态

5.show processlist; 查看当前的进程列表

6.show create table tbname;查看表的创建过程.

7.show engines;	查看引擎

### 存储引擎

MySQL的核心就是存储引擎。不同的存储引擎提供不同的存储机制、索引技巧、锁定水平等功能，使用不同的存储引擎，还可以 获得特定的功能。现在许多不同的数据库管理系统都支持多种不同的数据引擎。

**为什么要合理选择数据库存储引擎：**

MySQL中的数据用各种不同的技术存储在文件（或者内存）中。这些技术中的每一种技术都使用不同的存储机制、索引技巧、锁定水平并且最终提供广泛的不同的功能和能力。通过选择不同的技术，你能够获得额外的速度或者功能，从而改善你的应用的整体功能。

**如何选择 MySQL 存储引擎**

不同的存储引擎都有各自的特点，以适应不同的需求，如表所示。为了做出选择，首先要考虑每一个存储引擎提供了哪些不同的功能。

#### **MyISAM**

MyISAM没有提供对数据库事务的支持，也不支持行级锁和外键，因此当INSERT(插入)或UPDATE(更新)数据时即写操作需要锁定整个表，效率便会低一些。

使用这个存储引擎，每个MyISAM在磁盘上存储成三个文件。

（1）frm文件：存储表的定义数据

（2）MYD文件：存放表具体记录的数据

（3）MYI文件：存储索引

#### **InnoDB**

使用多表空间存储：表结构放在frm文件，数据和索引放在IBD文件中。分区表的话，每个分区对应单独的IBD文件。使用分区表的好处在于提升查询效率。

#### **Memory**

使用存在内存中的内容来创建表。每个MEMORY表只实际对应一个磁盘文件。MEMORY类型的表访问非常得快，因为它的数据是放在内存中的，并且默认使用HASH索引。

但是一旦服务关闭，表中的数据就会丢失掉。 HEAP允许只驻留在内存里的临时表格。驻留在内存里让HEAP要比ISAM和MYISAM都快，但是它所管理的数据是不稳定的，而且如果在关机之前没有进行保存，那么所有的数据都会丢失。在数据行被删除的时候，HEAP也不会浪费大量的空间。HEAP表格在你需要使用SELECT表达式来选择和操控数据的时候非常有用。

将数据存在内存，为了提高数据的访问速度，每一个表实际上和一个磁盘文件关联。文件是frm。

| 功能         | MylSAM | MEMORY | InnoDB(default) | Archive |
| ------------ | ------ | ------ | --------------- | ------- |
| 存储限制     | 256TB  | RAM    | 64TB            | None    |
| 支持事务     | No     | No     | Yes             | No      |
| 支持全文索引 | Yes    | No     | No              | No      |
| 支持树索引   | Yes    | Yes    | Yes             | No      |
| 支持哈希索引 | No     | Yes    | No              | No      |
| 支持数据缓存 | No     | N/A    | Yes             | No      |
| 支持外键     | No     | No     | Yes             | No      |



## select

1.select * from tbname;全部查询

select id,name fron tbname;

2.select 1+1 as newname ,as可以省略

3.时间

now():语句执行的时间

sysdate():当前时间(实时)

current_date:获取当前日期

current_time:获取当前的时间

select now(),sysdate(),sleep(),now(),sysdate();



## 数据类型

整形-int

tinyint 1字节 unsigned zerofill

samllint 2字节 2^16

mediuint 3字节

int	4字节

bigint	8字节

```sql
create table tbname(id tinyint);
insert into tbname(id) values(0);
```

浮点型

float  4字节

double	8字节

double(m,d)

定点型

decimal(m,d)  m+2字节

字符型

char:定长字符串 	char(50)

varchar:可变字符串  varchar(50)

text

enum 枚举

插入的值只能从给定的值中选择一个,可以使用字符插入,也可以使用下标插入,下标从1开始,依次向后排.25535

```sql
create table enum_test(gender enum('男','女'));
```

set集合

可以一次插入多个给定集合中的选项,可以使用字符插入,也可使用下标插入,下标从2 的0次方开始,依次是2的1次方......,插入时下标值相加即可.64

```sql
create table set_test(hobby set('唱歌','跳舞','玩游戏'));
1,2,4
```

日期时间

date

time

datetime

bool布尔类型-true false

## 数据类型

| 名称         | 类型           | 说明                                                         |
| ------------ | -------------- | ------------------------------------------------------------ |
| INT          | 整型           | 4字节整数类型，范围约+/-21亿                                 |
| BIGINT       | 长整型         | 8字节整数类型，范围约+/-922亿亿                              |
| REAL         | 浮点型         | 4字节浮点数，范围约+/-1038                                   |
| DOUBLE       | 浮点型         | 8字节浮点数，范围约+/-10308                                  |
| DECIMAL(M,N) | 高精度小数     | 由用户指定精度的小数，例如，DECIMAL(20,10)表示一共20位，其中小数10位，通常用于财务计算 |
| CHAR(N)      | 定长字符串     | 存储指定长度的字符串，例如，CHAR(100)总是存储100个字符的字符串 |
| VARCHAR(N)   | 变长字符串     | 存储可变长度的字符串，例如，VARCHAR(100)可以存储0~100个字符的字符串 |
| BOOLEAN      | 布尔类型       | 存储True或者False                                            |
| DATE         | 日期类型       | 存储日期，例如，2018-06-22                                   |
| TIME         | 时间类型       | 存储时间，例如，12:20:59                                     |
| DATETIME     | 日期和时间类型 | 存储日期+时间，例如，2018-06-22 12:20:59                     |



## sql分类

DDL 数据库定义语言

​		create创建

​		drop删除

​		alter修改

​		rename重命名

​		truncate清空

DML数据库操作语言

​		create

​		delete

​		insert

​		select

DQL数据库查询语言

​		select

DCL数据库控制语言

​		grant授权

​		revote撤权

事务

​		begin开始事务

​		commit提交事务

​		roll back回滚

​		save point回滚点

​	

创建数据库

```sql
create datebase dbname;
```

删除数据库

```sql
drop database dbname;
```

创建表

```sql
create table tbname(id int not null,......);
```

语法:

create table tbname(

colname1 coltype 列的约束条件1 列的约束条件2,

colname2 coltype 列的约束条件1 列的约束条件2,

colname3 coltype 列的约束条件1 列的约束条件2,

......

)option;

option:引擎   编码  自增

空和非空:null/not null 一般建议所有列都是非空

is null 或者is not null

default:默认值,需要和数据类型进行匹配

int   0

char  ''--->null

```sel
create table default_test(
	name varchar(20) default 'zhangsan'
);
```

unique  唯一

```sql
create table unique_test(
	id int not null unique,		#列级约束
    name varchar(20)
)

create table unique_test(
	id int not null,		
    name varchar(20),
    unique(id)		#表级约束
)

create table unique_test(
	id int not null,		
    name varchar(20),
    unique(id,name)		#表级约束-联合唯一
)
insert into unique_test values(1,'kitty');
insert into unique_test values(2,'kitty');#yes
insert into unique_test values(1,'zhangsan');#yes
insert into unique_test values(1,'kitty');#no
```

primary key主键   非空  唯一  索引

```sql
create table pri_test(
id int primary key,		#列级约束
name varchar(20)
);

create table pri_test(
id int,
name varchar(20),
primary key(id)		#表级约束
);
```

外键

主表-外表:先有主表,再有外表

数据:先插入主表数据,再插入外表数据

删除:先删外表,再删主表

引擎:innodb

外键的列类型和关联主表的列类型必须一致,业务是一致的

班级表-主表

1	一班

2	二班

3	三班

学生表-外表

1	张三	1

2	李四	1

3	王五	2

4	周六	3

```sql
create table class(
id int primary key
name varchar(20));

create table stu(
id int primary key,
name varchar(20),
class_id int,
foregin key(class_id) references class(id)#只有表级约束
)
```

auto_increment 自增    

1.默认+1,起始值为1

2.可以使用unsigned使自增值翻一倍;超过自增范围,自增失效

3.delete删除一条数据,自增顺序不会发生改变,只有清空truncate表格后,自增恢复初始值.

```sql
create table increnment_test(
id int primary  auto_increment
name varchar(20));

create table increnment_test(
id int primary
name varchar(20)
......
)auto_increment=100;

delete from tbname where id=11; 
insert into tbname(name) values('hh');  //11删掉了,11,12
```

key/index  索引:加快查询的速度

```sql
create table index_test(
	id int key,
    name varchar(20)
)
create table index_test1(
	id int,
    name varchar(20),
    key(id)
)
key作为列级约束,会被作为主键,而表级约束只是索引
create table index_test1(
	id int,
    name varchar(20),
    index(id)
)
```



#### 练习

* 练习：总结关键字 是否是  表级约束   列级约束  联合约束

| 关键字        | 表级约束 | 列级约束 | 联合约束 |
| ------------- | -------- | -------- | -------- |
| null/not null | N        | Y        | N        |
| default       | N        | Y        | N        |
| unique        | Y        | Y        | Y        |
| primary key   | Y        | Y        | Y        |
| foreign key   | Y        | N        | N        |
| key           | Y        | Y        | N        |
| index         | Y        | N        | N        |

* 练习：创建两张表，一张学生信息表，一张学生成绩表

信息表：student_info

​				编号：id int 自增，从10000开始

​				姓名：name varchar(20) 非空

​				性别：gender enum 取值为（0，1）非空 

​				年龄：age tinyint unsigned 非空

​				学号：number int，非空 唯一 索引

```sql
create table student_info(
	id int auto_increment,
    name varchar(20) not null,
    gender enum('0','1') not null,
    age tinyint unsigned not null,
   	number int not null unique,
    key(number)
)auto_increment=10000;
```

成绩表：student_mark

​				编号：id int 自增，从1开始

​				科目：mark_name varchar(255) 非空

​				成绩：grade int 非空 非负数 默认值为0

​				学号： 外键关联信息表中的学生number

```sql
create table student_mark(
	id int,
    mark_name varchar(255) not null,
    grade int unsigned not null default 0,
    no int,
    foreign key(no) references student_info(number)
);
```

删除

```sql
#删除数据库
drop database dbname;
#删除表
drop table tbname;
#删除索引
drop index idname;
```

重命名表

```sql
rename table old_name to new name;
```

清空

```sql
truncate tbname;
```



修改alter

#### 练习

创建一张alter_test表，列id int

* 需求1：往alter_test表中增加一列name varchar(20) 非空唯一  
  目的：增加列

```sql
1.
create table alter_test(id int);
2.
alter table alter_test add name varchar(20) not null unique;
```



- 需求2：将name列设置为索引列，索引名字为name_index  

  目的：增加索引（2种方法）

```sql
1.
alter table alter_test add index name_index(name);
2.
create index name_index1 on alter_test(name);
```



- 需求3：将id列设置为主键列  
  目的：增加主键

```sql
alter table alter_test add primary key(id);
```



- 需求4：往alter_test表中先增加一列no int,然后用alter语句更新表中的no列，加上唯一约束。
  目的：增加唯一性  

```sql
1.
alter table alter_test add no int;
2.
alter table alter_test add unique(no);
```



- 需求5：将name列的默认值设置为'aaa'  
  目的：单独修改已经存在列属性：新增默认值

```sql
alter table alter_test alter name set dufault 'aaa';
```



- 需求6：将name的默认值删除  
  目的：单独修改已经存在列属性：删除默认值

```sql
```



* 需求7：将no列修改成alter_test_no int(20) not null unique. 
  目的：整体修改已经存在列属性（同时重命名列） 

```sql
```



* 需求8：将alter_test_no列修改成int(21) not null unique  
  目的：整体修改已经存在列属性

```sql
```



* 需求9:删除alter_test_no列  
  目的：删除列

```sql
```



* 需求10：删除name列的索引约束  
  目的：删除索引(2种方法)

```sql
```



* 需求11：删除id的主键约束  
  目的：删除主键

```sql
```



* 需求12：将表的名字alter_test改成alter_test2  
  目的：修改表名(2种方法)

```sql
```



* 需求13：将表alter_test2的数据引擎改成myisam
  目的：修改数据引擎

```sql
```



创建一张alter_test1表，列id int 主键      
		插入数据1,2,3; 

再次插入1

* 需求14：将id列设置为主键列  
* 插入重复数据不报错

```sql

```



怎样增加外键约束？

实现：创建两张表alter_pk和alter_fk

alter_pk中id int 为主键

alter_fk中id int 为主键,pk_id int


*  需求15：将alter_fk中的pk_id列外键关联alter_pk表中的id列  
   一定要注意条件（数据完整性：主表中不存在的数据，外表中也不能存在，外表中只能存在主表的数据或者为空）

```sql

```



**注意：**使用ALTER TABLE要极为小心，应该在进行改动前做一个完整的备份（模式和数据的备份）。
  	数据库表的更改不能撤销，如果增加了不需要的列，可能不能删除它们。
  	类似地，如果删除了不应该删除的列，可能会丢失该列中的所有数据。





