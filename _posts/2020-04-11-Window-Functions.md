---

layout:     post
title:      Window Functions
subtitle:   Mysql, Database
date:       2020-04-11
author:     Xiangke
header-img: img/tag-bg-o.jpg
catalog: true
tags:
    - Data Analysis
    - SQL
    - DataBase
---







# Window Functions

- `row_number()` / `rank()` / `dense_rank()`
- `persent_rank()` / `cume_dist()`
- `lag()` / `lead()`
- `first_val()` / `last_val()`
- `nth_value`  / `nfile()`

---



**There is a frame window. Sometimes you only want to select the previous two values to do rank, or the row before and the row after the current row, How?** 



**CURRENT ROW** || boundary is the current row, generally used with other range keywords

**UNBOUNDED PRECEDING** || boundary is the first row in the partition

**UNBOUNDED FOLLOWING** || The boundary is the last line in the partition

**expr PRECEDING** || boundary is the value of expr for the current row

**expr FOLLOWING** || boundary is the current line plus the value of expr

# Number Functions

TBD



# Distribution Functions

TBD



# 