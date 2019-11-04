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
