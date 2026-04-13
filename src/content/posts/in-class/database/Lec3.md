---
title: 'Lec 3 - SQL'
pubDate: 2026-04-06
author: 'Acola'
category: '课业'
tags: ['数据库', 'Computer Science']
---

## 一、SQL概述
SQL包含数据定义语言(DDL)、数据操纵语言(DML)和数据控制语言(DCL)。
具有非过程化、面向集合操作的特性。

## 二、数据定义语言 (DDL)
基本类型: char, varchar, int, numeric, real, float, date, time, timestamp等。
创建表: CREATE TABLE，可定义主键(primary key)、非空(not null)和检查约束(check)。
修改表: ALTER TABLE ADD / DROP / MODIFY 属性。
删除表: DROP TABLE。
索引操作: CREATE INDEX，创建唯一索引使用 UNIQUE。

## 三、查询基本结构
SELECT: 指定查询的列，使用 distinct 去重，默认允许重复(all)。
FROM: 指定查询的表，多个表联合查询时等价于笛卡尔积。
WHERE: 指定查询条件，支持逻辑连词和 BETWEEN 范围。
更名操作: 使用 AS 为表或列重命名。
字符串操作: 使用 LIKE 进行模糊匹配，% 匹配任意子串，_ 匹配任意单个字符。
排序: ORDER BY，默认升序(asc)，降序使用 desc。

## 四、集合操作
并集: UNION
交集: INTERSECT
差集: EXCEPT (Oracle中为MINUS)
默认自动去重，若要保留所有重复项需追加 ALL (如 UNION ALL)。

## 五、聚集函数与分组
基本函数: avg(平均), min(最小), max(最大), sum(总和), count(计数)。
GROUP BY: 将结果按属性分组，聚集函数将作用于每个分组。
HAVING: 对分组后的结果进行条件筛选。
执行顺序: FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> DISTINCT -> ORDER BY。

## 六、空值 (Null Values)
表示缺失或未知的信息。
涉及 null 的算术运算结果为 null，比较运算结果为 unknown (三值逻辑)。
判断空值必须使用 is null 或 is not null。
聚集函数（除 count(*) 外）会自动忽略 null 值。

## 七、嵌套子查询与派生关系
集合成员测试: in, not in。
集合比较: > some (大于其中某一个), > all (大于全部)。
空关系测试: exists (子查询非空则返回真), not exists。
派生关系: 可在 FROM 子句中嵌套子查询，但必须为其指定别名。
WITH子句: 用于定义仅在当前查询中有效的局部临时视图，简化复杂查询。

## 八、视图 (Views)
视图是虚表，用于隐藏数据细节、提高安全性。
创建: CREATE VIEW 视图名 AS 查询语句。
更新限制: 只有结构简单的视图（如建立在单表上且无聚集函数的行列视图）才允许被更新(Insert/Update/Delete)。

## 九、数据库修改
删除: DELETE FROM 表名 WHERE 条件。
插入: INSERT INTO 表名(列名) VALUES(值) 或直接插入子查询的结果集。
更新: UPDATE 表名 SET 列名=新值 WHERE 条件，支持 CASE WHEN 条件更新。

## 十、连接查询 (Joined Relations)
自然连接 (Natural Join): 自动基于同名属性做等值连接并去除重复的同名列。
内连接 (Inner Join): 仅保留匹配成功的元组，可使用 ON 或 USING 指定条件。
外连接 (Outer Join): 保留未匹配的元组，未匹配部分补 null。分为左外(Left)、右外(Right)和全外连接(Full)。

## 十一、事务 (Transactions)
事务是作为单个逻辑单元执行的一系列操作，必须保证要么全做，要么全不做（原子性）。
COMMIT WORK: 提交事务，使更新永久生效保存在数据库中。
ROLLBACK WORK: 回滚事务，撤销该事务进行的所有未提交的更新。