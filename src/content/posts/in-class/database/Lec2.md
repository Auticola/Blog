---
title: 'Lec 2 - Relational Model'
pubDate: 2026-04-05
author: 'Acola'
category: '课业'
tags: ['数据库', 'Computer Science']
---

## 一、基本概念
关系模型: 简单优雅，用表格形式表示数据。
关系 (Relation): 对应数学概念，在数据库中表现为二维表。
元组 (Tuple): 表中的一行数据。
属性 (Attribute): 表中的一列字段。
域 (Domain): 属性允许的取值集合，要求值必须是原子的（不可拆分，满足第一范式）。
关系模式 (Relation Schema): 描述关系的逻辑结构，如表名和列名。
关系实例 (Relation Instance): 关系在特定时间点的实际数据快照。

## 二、关系的性质
1. 元组的排列顺序无关紧要。
2. 关系中不允许存在重复的元组。
3. 属性值必须是不可分割的原子值。

## 三、码与键 (Keys)
超码 (Superkey): 能够唯一标识关系中某一个元组的属性或属性集。
候选码 (Candidate key): 最小的超码，它的任意真子集都不能成为超码。
主码 (Primary key): 由用户显式指定的候选码，通常用下划线标出。
外码/外键 (Foreign key): 关系参照的另一表的主码，参照关系中的外码值必须在被参照关系中存在或为 null。

## 四、关系代数 (Relational Algebra)
纯查询语言，SQL 的理论基础。接收一个或两个关系作为输入，返回一个新关系。

1. 六个基本运算:
选择 (Select): $\sigma_p(r)$，根据条件 $p$ 筛选出符合要求的行。
投影 (Project): $\Pi_{A_1,A_2,\dots,A_k}(r)$，提取指定的列，并自动去除重复行。
并 (Union): $r \cup s$，要求两关系元数（列数）相同且对应属性域兼容。
差 (Set difference): $r - s$，要求两关系兼容，返回在 $r$ 中但不在 $s$ 中的元组。
笛卡儿积 (Cartesian product): $r \times s$，两个关系所有元组的无条件拼接。
更名 (Rename): $\rho_x(E)$，为关系代数表达式的结果重命名。

2. 附加运算 (可由基本运算推导):
交 (Set intersection): $r \cap s$。
自然连接 (Natural join): $r \bowtie s$，在共有属性上做等值连接，并消除重复的列。
Theta 连接 (Theta join): $r \bowtie_\theta s$，带任意条件 $\theta$ 的连接。
除运算 (Division): $r \div s$，主要用于处理包含“所有” (for all) 语意的查询需求。
赋值 (Assignment): $\leftarrow$，将复杂查询分解为按顺序执行的步骤，赋给临时变量。

3. 扩展运算:
广义投影 (Generalized Projection): 允许在投影的列表中使用算术函数或表达式。
聚集函数 (Aggregate Functions): avg, min, max, sum, count。支持结合分组进行运算。

## 五、数据库修改
所有修改操作在关系代数中均通过赋值运算符表示。
删除 (Deletion): $r \leftarrow r - E$，只能删除整行，不能仅删除特定属性值。
插入 (Insertion): $r \leftarrow r \cup E$，可插入单条记录或查询结果集。
更新 (Updating): $r \leftarrow \Pi_{F_1,F_2,\dots,F_n}(r)$，利用广义投影操作来改变元组中特定属性的值。