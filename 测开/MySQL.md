关系、设计过程、范式、er图、约束、完整性规则、连接左右内自然、union&join、
事务acid、并发一致性（脏读-撤回修改、丢失修改-同时修改、不可重复读-读两次——修改、幻读-读两次-新增删除）、隔离级别——没别读取到哪一步串行化。

锁-保证完整一致、锁粒度-行表页、封锁类型-读写-乐观悲观锁-版本号时间戳、一级二级三级封锁、两段锁协议-加锁解锁、
多版本控制协议

char-varchar
视图 view-本身无数据-可操作
连接池
***
DML、DDL；
sql
create database XXX;
use XXX
create table XXX (字段1 类型 约束, 字段2 类型，PRIMARY KEY(id))
删除表drop table XXX;
insert into 表XXX （字段XXX，，，）【vlaues(XX,XXX)】【select 】
删除列alter table  XXX  drop【add】 column  字段XXX
alter table XXX change/add  col col INT not null;
拼接表字段   select (xXX,XXX,XXX) as XXX from 表XXX
删除单个数据  delete  from XXX表 where  XXX
create table XXX as （selelct *  from）
update 表XXX set  XX=XX where Xx=X'X 
select    asc   desc；limit；
通配符  
where   is null、过滤行
group by 列、order by 列；
having XXX>3，过滤分组，需要先分组；
分组规定：顺序要求：where ——group by——order by_having
子查询：
	where   XXX in  （select 。。。）
去重 distinct
join
show tables；
UNION  将两个select的结果放到一个结果集中；select （。。） union  select （。。。。）
***
mysql设计
根据业务和数据特点确定相关的表字段和类型，来定义主键、外键和相关的 一些约束保证数据的完整性；

- 引擎
	- 支持事务、外键、异常崩溃的安全恢复；
- 索引的作用和类型；
	- 结构为树红黑树hash
	- 底层存储：聚簇索引、非聚簇
	- 应用维度；主键索引、多个组成一个联合索引、前缀索引、
	- 索引的选择：主键、外键、频繁、

- 事务
	- 逻辑上的一组操作；

索引+事务
锁是为了实现事务；
如何查找数据的，更新的？知道整体架构-查找—索引—事务—日志；
b+，结构，什么时候走索引，、优化？




