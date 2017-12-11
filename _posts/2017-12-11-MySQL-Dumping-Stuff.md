---
layout: post
title: (MySQL) Dumping stuff
---

```
mysqldump -h <HOST> --port=3306 -u <USER> -p --lock-tables=false --databases <DATABASE> --tables <TABLE> > <TABLE>.sql;
```

