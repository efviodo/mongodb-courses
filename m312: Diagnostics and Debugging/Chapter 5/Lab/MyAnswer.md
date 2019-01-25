# Solution

1. Enable mongo profiling
```
db.setProfilingLevel(2);
```

2. Each enter you get over 10 new queries.

```
db.system.profile().count()
```

3. Try to understand queries

```
db.system.profile.find({}, {planSummary: 1});
```

```
db.system.profile.find({}, {planSummary: 1, op: 1, query: 1, ns: 1}).pretty();
db.system.profile.aggregate([{$group: {"_id": { op: "$op", ns: "$ns"}}}]);
```

4. Understanding schema design

```
db.users.find({}).limit(1).pretty();
```
And so on...

**Answer**

From mongostat we can see that application is not using to many open connections.

In the other side, looking into differents collections we can deduce that the schema is right and there is not normaliaztion problems.

How ever we from mongostat we can deduce that there is a huge amount of queries for a small amount of application interactions. 

So my answer is:

- [ ] The application is triggering many more queries than are necessary for each operation.

