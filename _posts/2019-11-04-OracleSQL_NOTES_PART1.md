---
title: ORACLE SQL 学习笔记 PART 1
description: 一些基础的ORACLE SQL的概念
categories:
 - 教程
tags:
---

> 主要Focusing on四个重要的讨论点，When， How， Why， What

<!-- more -->

# SQL Basic
## WHAT IS SQL?
  SQL stands for Structured Query Language.  
  SQL lets you access and manipulate databases.  
## RDBMS
  RDBMS stands for Relational Database Management System.  
  RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.  
  The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.  
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

* DEFAULT  

  DEFAULT 约束用于向列中插入默认值。  
  如果没有规定其他的值，那么会将默认值添加到所有的新记录。  
  The DEFAULT constraint is used to provide a default value for a column.  
  The default value will be added to all new records IF no other value is specified.  

## VARCHAR, VACHAR2, CHAR
* CHAR  

  The CHAR datatype stores fixed-length character strings. When you create a table with a CHAR column, you must specify a string length (in bytes or characters) between 1 and 2000 bytes for the CHAR column width. The default is 1 byte. Oracle then guarantees that:  
    1. When you insert or update a row in the table, the value for the CHAR column has the fixed length.  
    2. If you give a shorter value, then the value is blank-padded to the fixed length.  
    3. If a value is too large, Oracle Database returns an error.   

* VARCHAR, VARCHAR2

  The VARCHAR2 datatype stores variable-length character strings. When you create a table with a VARCHAR2 column, you specify a maximum string length (in bytes or characters) between 1 and 4000 bytes for the VARCHAR2 column. For each row, Oracle Database stores each value in the column as a variable-length field unless a value exceeds the column's maximum length, in which case Oracle Database returns an error.  
  1. Varchar can identify NULL and empty string separately.	Varchar2 cannot identify both separately. Both considered as same for this.   
  2. Varchar is ANSI Sql standard. Varchar2 is Oracle standard.   

## AGGREGATION FUNCTIONS (MIN / MAX / AVG / SUM / COUNT)  
  Aggregate functions return a single result row based on groups of rows, rather than on single rows. Aggregate functions can appear in select lists and in `ORDER BY` and `HAVING` clauses. They are commonly used with the `GROUP BY` clause in a `SELECT` statement, where Oracle Database divides the rows of a queried table or view into groups. In a query containing a `GROUP BY` clause, the elements of the select list can be aggregate functions, `GROUP BY` expressions, constants, or expressions involving one of these. Oracle applies the aggregate functions to each group of rows and returns a single result row for each group.  
  
  Many (but not all) aggregate functions that take a single argument accept these clauses:  
  1. The syntax diagrams for aggregate functions in this chapter use the keyword `DISTINCT` for simplicity.  
  2. ALL causes an aggregate function to consider all values, including all duplicates.  
  
  For example, the `DISTINCT` average of 1, 1, 1, and 3 is 2. The `ALL` average is 1.5. If you specify neither, then the default is `ALL`.

## DROP / TRUNCATE / DELETE
* DROP  

  DROP is used to delete a whole database or just a table.The DROP statement destroys the objects like an existing database, table, index, or view.  

  - The DROP command removes a table from the database.
  - All the tables' rows, indexes and privileges will also be removed.
  - No DML triggers will be fired.
  - The operation cannot be rolled back.
  - DROP and TRUNCATE are DDL commands, whereas DELETE is a DML command.
  - DELETE operations can be rolled back (undone), while DROP and TRUNCATE operations cannot be rolled back.  
  
* TRUNCATE  

  TRUNCATE SQL query removes all rows from a table, without logging the individual row deletions.   
  
  - TRUNCATE is executed using a table lock and whole table is locked for remove all records.
  - We cannot use WHERE clause with TRUNCATE.
  - TRUNCATE removes all rows from a table.
  - Minimal logging in transaction log, so it is faster performance wise.
  - TRUNCATE TABLE removes the data by deallocating the data pages used to store the table data and records only the page deallocations in the transaction log.
  - TRUNCATE TABLE通过取消分配用于存储表数据的数据页来删除数据，并仅在事务日志中记录页面的解除分配。
  - Identify column is reset to its seed value if table contains any identity column.
  - Truncate uses less transaction space than the Delete statement.
  - Truncate cannot be used with indexed views.
  - TRUNCATE is faster than DELETE.  

* DELETE  

  To execute a DELETE queue, delete permissions are required on the target table. If you need to use a WHERE clause in a DELETE, select permissions are required as well.

   - DELETE is a DML command.
   - DELETE is executed using a row lock, each row in the table is locked for deletion.
   - We can use where clause with DELETE to filter & delete specific records.
   - The DELETE command is used to remove rows from a table based on WHERE condition.
   - It maintain the log, so it slower than TRUNCATE.
   - The DELETE statement removes rows one at a time and records an entry in the transaction log for each deleted row.
   - Identity of column keep DELETE retains the identity.
   - To use Delete you need DELETE permission on the table.
   - Delete uses the more transaction space than Truncate statement.
   - Delete can be used with indexed views.

## UNION / UNIONALL / MINUS / INTERSECT  
* UNION / UNIONALL  

  1. UNION  
    The UNION command combines the result set of two or more `SELECT` statements (only distinct values).  
    ![Union.gif](/assets/images/04_sql_union.gif)
  2. UNIONALL  
    The UNION ALL command combines the result set of two or more `SELECT` statements (allows duplicate values).  
    ![Unionall.gif](/assets/images/05_sql_union_all.gif)
* MINUS / INTERSECT  

  1. MINUS  
    MINUS returns the difference between the first and second `SELECT` statement. It is the one where we need to be careful which statement will be put first, cause we will get only those results that are in the first `SELECT` statement and not in the second.  
    ![Minus.gif](/assets/images/06_sql_minus_12.gif)
  2. INTERSECT  
    INTERSECT is opposite from MINUS as it returns us the results that are both to be found in first and second `SELECT` statement.  
    ![Intersect.gif](/assets/images/08_sql_intersect.gif)
    
## VIEW & TEMPORARY TABLE
* VIEW  
  Views in SQL are kind of virtual tables. A view also has rows and columns as they are in a real table in the database. We can create a view by selecting fields from one or more tables present in the database. A View can either have all the rows of a table or specific rows based on certain condition.  

  What's the advantages?  
    1. Improves the performance of data retriving.  
    2. Limit the degrees of exposure of the underlying tables to the outer world.  


* Temporary Table  
  In Oracle Database, global temporary tables are permanent objects whose data are stored on disk and automatically deleted at the end of a session or transaction. In addition, global temporary tables are visible to all sessions currently connected to the database.  
  ![Global/Private.jpeg](/assets/images/WechatIMG64.jpeg)

* VIEW vs. TEMPORARY TABLE  
  Modifications on view could change the original table data. However, the modification on temp will keep the original table intacted. And the modification on oringal table after create the view will have effects on the view. On the other hands, temp table would not be affected.  

# Transaction
## What's transaction?
  A transaction is a sequence of operations performed (using one or more SQL statements) on a database as a single logical unit of work.  
## Transaction Principles
* Atomic  
  A transaction is a logical unit of work which must be either completed with all of its data modifications, or none of them is performed.  
  一个事务中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚到事务开始前的状态，就像这个事务从来没有执行过一样。  

* Consistent  
  At the end of the transaction, all data must be left in a consistent state.  
  在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。  

* Isolate  
  Modifications of data performed by a transaction must be independent of another transaction. Unless this happens, the outcome of a transaction may be erroneous.  
  数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。  

* Durable  
  When the transaction is completed, effects of the modifications performed by the transaction must be permanent in the system.  
  事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。  

## Transaction Statements
* `COMMIT`：提交更改；  
* `ROLLBACK`：回滚更改；  
* `SAVEPOINT`：在事务内部创建一系列可以 ROLLBACK 的还原点；  
* `SET TRANSACTION`：命名事务, 用来设置事务隔离级别。  

## Isolation Level
![Iso_level](/assets/images/WechatIMG3.jpeg)
* 未提交读(Read Uncommitted)：允许脏读，也就是可能读取到其他会话中未提交事务修改的数据  
* 提交读(Read Committed)：只能读取到已经提交的数据。Oracle等多数数据库默认都是该级别 (不重复读)  
* 可重复读(Repeated Read)：可重复读。在同一个事务内的查询都是事务开始时刻一致的，InnoDB默认级别。在SQL标准中，该隔离级别消除了不可重复读，但是还存在幻象读  
* 串行读(Serializable)：完全串行化的读，每次读都需要获得表级共享锁，读写相互都会阻塞  

## Concurrency Anomalies
* Dirty Read  
  A dirty read occurs if one transaction reads data that has been modified by another transaction.  
  就是指当一个事务正在访问数据，并且对数据进行了修改，而这种修改还没有提交到数据库中，这时，另外一个事务也访问这个数据，然后使用了这个数据。  

* Non-Repeatable Read  
  A non-repeatable read occurs when a object is read twice within a transaction; and between the reads, it is modified by another transaction, therefore, the second read returns different values as compared to the first.  
  是指在一个事务内，多次读同一数据。在这个事务还没有结束时，另外一个事务也访问该同一数据。那么，在第一个事务中的两次读数据之间，由于第二个事务的修改，那么第一个事务两次读到的的数据可能是不一样的。这样就发生了在一个事务内两次读到的数据是不一样的，因此称为是不可重复读。  

* Phantom Read  
  Phantom reads are of a totally different nature than the anomalies introduced previously.  
  第一个事务对一个表中的数据进行了修改，这种修改涉及到表中的全部数据行。同时，第二个事务也修改这个表中的数据，这种修改是向表中插入一行新数据。那么，以后就会发生操作第一个事务的用户发现表中还有没有修改的数据行，就好象发生了幻觉一样。  

# PL/SQL
## Stored Procedure / Function / Trigger
* Stored Procedure vs. Function  
![SPF](/assets/images/SP:F.jpg)
