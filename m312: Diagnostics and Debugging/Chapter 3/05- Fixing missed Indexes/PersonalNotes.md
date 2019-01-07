**Chapter 3: Slow Queries**

## Fixing missed Indexes

### Personal notes


#### How to see the creation of an index in the mongo log?

``` 
mlogfilter $logpath --component INDEX
```

I can also see the trace of the operations of creating an index, filtering by the COMMAND component in logfile:

``` 
mlogfilter $logpath --component COMMAND
```

In order to find logPath value you can use the following bash script snippet:

``` 
logPath=$(ps -ef | grep mongo | grep 30000 | awk '{ print $14}')
``` 
