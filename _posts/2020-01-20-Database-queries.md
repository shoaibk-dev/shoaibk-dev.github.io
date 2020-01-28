---
layout: post
title: Database Queries
---

Uses for pagination
```
int page = 1;
int page_limit = 20;
int page_offset = page* 20;
SELECT * FROM `tbl_all` ORDER BY id ASC LIMIT page_offset,page_limit
page = page + 1;
```
