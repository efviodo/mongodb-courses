**Chapter 3: Slow Queries**

## Response Time Degradation

### Personal notes

- In the video we can see the following metrics from mongostats:

```
time | dirty | used | I | qrw | arw
```

- Column *used* represents the amount of memory used by MongoDB, tipically dominated by cache utilization. Column *dirty* represents the amount of memory already used from cache. So if we have a healthy set up of MongoDB, *dirty* and *used* values should be in armony (tipically used a bit bigger than dirty). On the contrary, if *used* is far bigger than *dirty* and in particularly *dirty* is a very tiny value, we probably have some problems. For example the size of the cache is to small to fit the entire working set.
