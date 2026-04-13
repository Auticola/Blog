---
title: 'Lec 1 - Introduction'
pubDate: 2026-04-04
author: 'Acola'
category: '课业'
tags: ['数据库', 'Computer Science']
---

## 〇、写在前面
第一讲的内容比较泛比较虚，对专有名词有大体了解即可。

## 一、基本概念与介绍
Database (数据库): 计算机内长期存储、有组织、可共享的数据集合。
DBMS (数据库管理系统): 存储、管理和访问数据库的软件系统。
Enterprise: 现实世界模型，包含实体（Entities）和关系（Relationships）。
Instance (实例): 数据库在特定时间点的内容，类似变量的值。
Schema (模式): 数据库的结构设计，类似类型信息。

## 二、数据库的特征与文件处理系统的缺陷
Data redundancy and inconsistency: 数据冗余和不一致
Difficulty in accessing data: 存取困难
Data isolation: 数据孤岛
Integrity problems: 完整性问题
No atomicity of updates: 更新缺乏原子性
Concurrent access anomalies: 并发访问异常
Security problems: 安全问题

## 三、数据库的三级抽象与数据独立性
View level (视图层/外模式): 展示部分数据，隐藏细节以保证安全。
Logical level (逻辑层/模式): 描述存储的数据及其逻辑关系。
Physical level (物理层/内模式): 描述数据实际存储方式。
其中层级之间存在 map 映射

### 数据独立性 (Data Independence)：
1. Physical data independence (物理数据独立性): 修改物理模式不影响逻辑模式，隔离应用与底层存储。
2. Logical data independence (逻辑数据独立性): 修改逻辑模式不影响应用程序（较难实现）。

## 四、数据模型与关系模型
数据模型用于描述数据结构、关系、语义和约束。
E-R Model (实体-关系模型): 用于概念层，包含实体、属性和关系。
Relational Model (关系模型): 常由E-R图转换而来，用表格形式表示数据。
Relation / Table: 关系即表格。
Tuple: 元组，即表格中的行。
Attribute / Column: 属性，即表格中的列（字段）。

## 五、数据库语言
DDL (Data Definition Language / 数据定义语言): 定义数据库模式、存储结构和约束。
DML (Data Manipulation Language / 数据操纵语言): 用于访问和更新数据。分为过程化（需说明如何获取）和非过程化（仅指明需获取什么）。
SQL (结构化查询语言): 最常用的非过程化语言，基于集合、声明式。

## 六、数据库设计步骤
1. Requirement analysis (需求分析): 确定所需数据、应用和操作。
2. Conceptual database design (概念设计): 使用E-R模型等描述数据。
3. Logical database design (逻辑设计): 转换为数据库模式。
4. Schema refinement (模式细化): 关系规范化，消除冗余和异常。
5. Physical database design (物理设计): 索引、聚簇和调优。
6. Security design & Initialization (安全设计与初始化): 识别用户角色，加载数据。

## 七、数据库用户与系统架构
用户分类: Naive users (普通用户)、Application programmers (程序员)、Sophisticated users (分析师)、Specialized users (专业用户)。
DBA (数据库管理员): 具有最高权限，控制数据库活动和用户访问。
### 核心组件:
Query Processor (查询处理器): 包含DDL解释和DML编译，负责查询优化与执行评估。
Storage Manager (存储管理器): 提供底层接口，含事务、授权、文件及缓冲管理器。

## 八、事务管理 (Transaction Management)
Transaction (事务): 完成单一逻辑功能的指令集合。
ACID 特性: 原子性 (Atomicity)、一致性 (Consistence)、隔离性 (Isolation)、持久性 (Durability)。
故障与并发: 保障系统故障后的状态一致性，控制并发交互。