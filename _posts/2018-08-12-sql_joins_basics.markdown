---
layout: post
title:      "SQL JOINS Basics"
date:       2018-08-12 16:08:26 +0000
permalink:  sql_joins_basics
---


SQL Joins are about relational databases. One of the primary use cases is establishing table relationships between objects that have "has many" relationships and objects that have "belong to" relationships. Key examples of this could be the relationship between en employee table and its respective manager table.

This leads us to the idea of keys used in tables. Every line item in a table is numbered by a "primary key" the respective relational id is known as a "foreign key". The Foreign key is the primary key of the respective line item of the table being called.

More specifically a SQL JOIN connects two rows from two or more different tables based on a common column between them.

There are several types of Joines: INNER, LEFT, RIGHT, FULL will be articulated in this post:

INNER JOINS: returns all the rows where there is at least one match in both tables.

We can think of Joins as a venn diagram, and an INNER JOIN means that the common values will be returned.

LEFT JOIN: Returns all rows from the left table and the matched rows from the right table.

This will in essence return two columns. All the values from the left (first table) and either the corresponding matched value or null in the right or (second table).

More specifically. When you run a left join the code will iterate over the left (first table) and return each corresponding match from the right (second) table. In the example below. You can see that the left table has multiple entries, and the right corresponding table has a unique value each time. It will iterate through the left table until all its values have been returned. For values where there is no corresponding match it returns Null.

id  teacher_name    id      name     teacher_id
--- ------------   ----    ------    -----------
1      Joe           3       Bob          1
1      Joe           1       Dave         1
1      Joe           2       Jessie       1
2      Steven        5       George       2
2      Steven        4       Sara         2
3      Jeff          NULL    NULL         NULL

RIGHT JOIN: Returns all rows from the right table and the matched rows from the left table.

When you run a RIGHT OUTER JOIN. It will iterate over the right (second table) and return the corresponding values or NULL if there is no corresponding value. The code stops once all the values of the right table have been returned (see below).

id    teacher_name   id      name     teacher_id
---   ------------  ----    ------    -----------
1        Joe         3       Bob          1
1        Joe         1       Dave         1
1        Joe         2       Jessie       1
2        Steven      5       George       2
2        Steven      4       Sara         2
NULL     NULL        6       Alexis       NULL

FULL OUTER JOIN: Returns all rows from both tables. 

Will return all rows from both tables. Where there is no match it will return Null.

This code iterates over both tables and returns all values or NULL where there is no corresponding values.

id    teacher_name   id      name     teacher_id
---   ------------  ----    ------    -----------
1        Joe         3       Bob          1
1        Joe         1       Dave         1
1        Steven      2       Jessie       1
2        Steven      5       George       2
2        Steven      4       Sara         2
3        Jeff       NULL     NULL        NULL
NULL     NULL        6       Alexis      NULL



