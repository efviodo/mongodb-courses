**Chapter 3: Slow Queries**

## Using Mtools to Find Slow Queries

### Personal notes

#### mloginfo
Returns information about the logfile like count of lines and etc.

```
mloginfo mongo.log
```

Also you can return a top of queries that must be optimized
```
mloginfo --queries --no-progressbar mongo.log 
```
