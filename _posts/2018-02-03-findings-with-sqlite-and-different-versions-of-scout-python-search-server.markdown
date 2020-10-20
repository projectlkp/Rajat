---
layout: post
title:  Findings with sqlite and different versions of scout  python search server  
date:   2018-02-03 21:15:04 +0000
---


* Sqlite has full text search support via modules fts3, fts4, fts5             
By default all three are added in sqlite package, but fss5 is disabled as it is experimental.


* Scout uses Sqlite for search
* Scout 0.4.0 uses fts5 if available, else fallback to fts4.
* Scout 3.0.0 is fixed on fts4, even if fts5 is available


* Substring search doesn't work on both fts4 and fts5 for English text. 
Means "hell" will not give results for content containing string "hello".
```
create virtual table idx4 using "fts4" (content);
create virtual table idx5 using "fts5" (content);
insert into idx4 (content) values ('hello world');
insert into idx5 (content) values ('hello world');
select * from idx4 where idx4 match 'hell';
select * from idx5 where idx5 match 'hell';
//no results in both case
```

* But funny enough Substring search work for Hindi text only on fts5.
```
create virtual table idx5 using "fts5" (content);
insert into idx5 (content) values ("पाकिस्तान नीरजा भनोट के");
select * from idx5 where idx5 match "पाकि";
// give result- पाकिस्तान नीरजा भनोट के
```
* So Substring search works for "hindi" content on scout 0.4.0 when your sqlite fts5 module is enabled, Quite coincidental, but happens. :)

ok



