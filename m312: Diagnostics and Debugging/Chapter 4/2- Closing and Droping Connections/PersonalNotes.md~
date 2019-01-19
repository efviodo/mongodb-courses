**Chapter 4: Closing and dropping connections**

## Connections refused
Defaul maximun allowed connections is **65536** but some times our server host are poorly configured:

1. Take a look to server logs and try if you can see som "Connection Refused" Network error
2. Take a look to your server congiguration and check the value of *maxIncomingConnections*

## Memory utilization
Open as many connection as you can is a poorly practise if you take into consideration the server memory utilization from both sides: your application side and MongoDB server side. You must considering limit the maximun number of connections from your application to a realistic number and perhaps use a library with a connection pool.

## Ulimits
There is something that could actually limit the maximum number of connections and is the maximum number of file descriptors or open files that your operating system allows. You can check this using `ulimit -a` command.

Particularly check *file descriptors* (may be the name is *open files*) value:

```
$ ulimit -a
-t: cpu time (seconds)              unlimited
-f: file size (blocks)              unlimited
-d: data seg size (kbytes)          unlimited
-s: stack size (kbytes)             8192
-c: core file size (blocks)         0
-m: resident set size (kbytes)      unlimited
-u: processes                       63733
-n: file descriptors                1024
-l: locked-in-memory size (kbytes)  64
-v: address space (kbytes)          unlimited
-x: file locks                      unlimited
-i: pending signals                 63733
-q: bytes in POSIX msg queues       819200
-e: max nice                        0
-r: max rt priority                 0
-N 15:                              unlimited
``` 

Try to connect to your MongoDB server and type the following command:

```
db.serverStatus().connections
```

You will see a very smaller number of 65536 and this is because the limitation of *file descriptors* which is actually set to 1024.

## Mongostat --discover

There is a very interesting flag of `mongostat` called *--discover*. With this flag mongostat will discover all replica set member and even shards members of the group to which the server you are attempting to connect belongs.

```
mongostat --discover --port 27000
```

