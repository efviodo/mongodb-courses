**Chapter 3: Slow Queries**

## What Slow Queries Look Like in an Application
 Talking about what is an what isn't a slow query have in mind the following facts:
- A normal API REST service must respond under 200 milliseconds. After that it would be considering slow.
- In MongoDB any query with a response time over 100 milliseconds is considered as slow.

## Response Time Degradation

### Personal notes

- If working set does not fix in server RAM we would note application response time degradation. So may be this is the first thing to look when your application is not working properly.

- In the video we can see the following metrics from mongostats:

```
time | dirty | used | I | qrw | arw
```

- Column *used* represents the amount of memory used by MongoDB, tipically dominated by cache utilization. Column *dirty* represents the amount of memory already used from cache. So if we have a healthy set up of MongoDB, *dirty* and *used* values should be in armony (tipically used a bit bigger than dirty). On the contrary, if *used* is far bigger than *dirty* and in particularly *dirty* is a very tiny value, we probably have some problems. For example the size of the cache is to small to fit the entire working set.

If server cache is to tinny, server will spend a lot of time making enough space to allocate incoming data, particularly if the size of cache is smaller than recommended minimum.

- Talking about response time degradation vs data growth, we wish a log(N) relation in contrast to a linear relation. Of course it would be desirable that the response time of our application is always the same, no matter how much data we have but without increasing the processing power of the MongoDB server this is impossible.

The good thing is that, as long as we have correctly designed queries, appropriate indexes and a healthy MongoDB installation, the relationship between response time and data should be logarithmic.

### Analyse response time degradation
We can analyse response time degradation and find slow queries in multiples ways:

- Enabling mongo profile and sort queries by descending response time.

- Using *mlogvis* to analyse MongoDB logs and plot slow queries over 100ms in response time: 
```
mlogvis mongod.log
```
