---
title: ORACLE SQL 学习笔记 PART 1
description: 一些基础的ORACLE SQL的概念
categories:
 - 教程
tags:
---

> 主要Focusing on四个重要的讨论点，When， How， Why， What

<!-- more -->

# SQL (Structured Query Language) Basic
## Non-relational Databases vs. Relational Databases
## SQL
* DQL / DRL (Data Query Language) :   
  SELECT, FROM, WHERE, ORDER, GROUP, HAVING
* DDL (Data Definition Language) :  
  CREATE, ALTER, DROP, TRUNCATE, RENAME
* DML (Data Manipulation Language) :  
  INSERT, UPDATE, DELETE
* DCL (Data Control Language) :  
  GRANT, REVOKE
* TCL (Transaction Control Language):  
  COMMIT, ROLLBACK, SAVEPOINT

# SQL Common Key Words
## Constraint
* NOT NULL  

  NOT NULL 约束强制列不接受 NULL 值。  
  NOT NULL 约束强制字段始终包含值。这意味着，如果不向字段添加值，就无法插入新记录或者更新记录。  
  The NOT NULL constraint enforces a column to NOT accept NULL values.  
  This enforces a field to always contain a value, which means that you cannot insert a new record, or update a record without adding a value to this field.  
  
* UNIQUE  
  UNIQUE 约束唯一标识数据库表中的每条记录。  
  UNIQUE 和 PRIMARY KEY 约束均为列或列集合提供了唯一性的保证。  
  PRIMARY KEY 拥有自动定义的 UNIQUE 约束。  
  请注意，每个表可以有多个 UNIQUE 约束，但是每个表只能有一个 PRIMARY KEY 约束。  
  The UNIQUE constraint ensures that all values in a column are different.  
  Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns.  
  A PRIMARY KEY constraint automatically has a UNIQUE constraint.  
  However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table.  
  
* PRIMARY KEY
  PRIMARY KEY 约束唯一标识数据库表中的每条记录。主键建立时自带聚集索引。  
  主键必须包含唯一的值。主键列不能包含 NULL 值。  
  每个表都应该有一个主键，并且每个表只能有一个主键。  
  The PRIMARY KEY constraint uniquely identifies each record in a table. The PRIMARY KEY will automatically have a cluster index.  
  Primary keys must contain UNIQUE values, and cannot contain NULL values.  
  A table can have only ONE primary key; and in the table, this primary key can consist of single or multiple columns (fields).  
  
* FOREIGH KEY
  一个表中的 FOREIGN KEY 指向另一个表中的 PRIMARY KEY。  
  包含外键的表称为子表，包含候选键（Candidate Key）的表称为引用表或父表。  
  FOREIGN KEY 约束用于预防破坏表之间连接的动作。  
  FOREIGN KEY 约束也能防止非法数据插入外键列，因为它必须是它指向的那个表中的值之一。  
  A FOREIGN KEY is a key used to link two tables together. A FOREIGN KEY is a field (or collection of fields) in one table that refers to the PRIMARY KEY in another table.  
  The table containing the foreign key is called the child table, and the table containing the candidate key is called the referenced or parent table.  
  The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.  
  The FOREIGN KEY constraint also prevents invalid data from being inserted into the foreign key column, because it has to be one of the values contained in the table it points to.  

* CHECK
  CHECK 约束用于限制列中的值的范围。  
  如果对单个列定义 CHECK 约束，那么该列只允许特定的值。  
  如果对一个表定义 CHECK 约束，那么此约束会在特定的列中对值进行限制。  
  The CHECK constraint is used to limit the value range that can be placed in a column.  
  If you define a CHECK constraint on a single column it allows only certain values for this column.  
  If you define a CHECK constraint on a table it can limit the values in certain columns based on values in other columns in the row.  
