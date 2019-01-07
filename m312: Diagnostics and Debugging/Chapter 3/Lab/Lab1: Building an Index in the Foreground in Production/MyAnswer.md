## Setting up logPath

``` 
logPath=$(ps -ef | grep mongo | grep 30000 | awk '{ print $14}')
``` 

## Viewing logs
``` 
mlogfilter $logpath --component INDEX
```

``` 
mlogfilter $logpath --component COMMAND
```

## Display slow queries
```
mloginfo $logpath --queries
```

**Answer**

Less than one second after the index build ended
