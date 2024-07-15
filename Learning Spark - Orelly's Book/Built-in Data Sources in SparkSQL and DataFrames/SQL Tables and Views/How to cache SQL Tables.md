It is able to cache and uncache SQL tables and views. In Spark 3.0, in addition to other options, you can specify a table as _lazy_, meaning that it should be cached when it is cached when it is first used instead of immediately:

```sql
CACHE [LAZY] TABLE <table_name>
```

If in _lazy_, when the first time you call an action, the data is cached.
