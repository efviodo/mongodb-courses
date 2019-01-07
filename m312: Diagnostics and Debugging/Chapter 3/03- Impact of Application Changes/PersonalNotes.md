
**Chapter 3: Slow Queries**

## Impact of Application Changes

### Personal notes

#### Exhausting Connections Pool
It is very important pay attention in connection pool size of your application. Be sure that if your application makes an intensive use of your database you are using an appropriate connection pool size.

Beside be aware about the pool utilization from MongoDB server size. You can monitor the number of connections from ``db.serverStatus()``
