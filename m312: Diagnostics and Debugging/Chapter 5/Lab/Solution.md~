**Chapter 4: Connectivity**

## Lab: Diagnosing unknown issues

One of the best and first places you should look for information is in the log file.

In data/m312rs/rs1/mongod.log we begin to notice a lot of similar entries that should be alarming.

>2017-04-10T20:07:53.842+0000 I NETWORK  [thread1] connection accepted from 127.0.0.1:43791 #36 (21 connections now open)
2017-04-10T20:07:53.842+0000 I NETWORK  [conn36] received client metadata from 127.0.0.1:43791 conn36: { driver: { name: "PyMongo", version: "3.4.0" }, os: { type: "Linux", name: "Ubuntu 14.04 trusty", architecture: "x86_64", version: "3.13.0-108-generic" }, platform: "CPython 2.7.6.final.0" }


Reading down through our log further we can see the number of "connections now open" continually grows.

An application that continually opens new connections and never closes them rather than sharing a connection pool will eventually cause resource issues on the MongoDB server.

Aside from the log, there are other diagnostic methods. Using mongostat, we can also see a growing number of connections and an ever increasing consumption of memory.

>mongostat --host m312rs/m312 --port 30000
insert query update delete getmore command dirty used flushes vsize   res qrw arw net_in net_out conn    set repl                time
  *0    *0     *0     *0       0     4|0  0.0% 0.0%       0  986M 47.0M 0|0 0|0   521b   46.8k  136 m312rs  PRI Apr 11 01:31:33.118
  *0    *0     *0     *0       0    18|0  0.0% 0.0%       0  987M 47.0M 0|0 0|0  1.35k   53.5k  137 m312rs  PRI Apr 11 01:31:34.123
  *0    *0     *0     *0       0     4|0  0.0% 0.0%       0  987M 47.0M 0|0 0|0   470b   47.0k  137 m312rs  PRI Apr 11 01:31:35.119
  *0    *0     *0     *0       0     2|0  0.0% 0.0%       0  987M 47.0M 0|0 0|0   158b   46.0k  137 m312rs  PRI Apr 11 01:31:36.117
  *0    *0     *0     *0       2     7|0  0.0% 0.0%       0  987M 47.0M 0|0 0|0  2.91k   47.6k  137 m312rs  PRI Apr 11 01:31:37.117
  *0    *0     *0     *0       0     1|0  0.0% 0.0%       0  987M 47.0M 0|0 0|0   157b   45.9k  137 m312rs  PRI Apr 11 01:31:38.118
  *0    *0     *0     *0       0   120|0  0.0% 0.0%       0  988M 47.0M 0|0 0|0  7.41k    100k  138 m312rs  PRI Apr 11 01:31:39.118
  *0    *0     *0     *0       0     2|0  0.0% 0.0%       0  988M 47.0M 0|0 0|0   158b   45.9k  138 m312rs  PRI Apr 11 01:31:40.118
  *0    *0     *0     *0       0     4|0  0.0% 0.0%       0  988M 47.0M 0|0 0|0   468b   46.8k  138 m312rs  PRI Apr 11 01:31:41.118
  *0    *0     *0     *0       0     2|0  0.0% 0.0%       0  988M 47.0M 0|0 0|0  1.04k   46.2k  138 m312rs  PRI Apr 11 01:31:42.119

Using  mloginfo  we can also diagnose this problem easily. Run the command about 15 seconds apart and the delta in open connections is clearly visible. Of particular note is the number of total open connections, and the number of unique IPs.

>vagrant@m312:~$ mloginfo data/m312rs/rs1/mongod.log --connections
   source: data/m312rs/rs1/mongod.log
     host: m312:30000
    start: 2017 Apr 11 01:18:24.828
      end: 2017 Apr 11 01:51:05.745
date format: iso8601-local
   length: 2213
   binary: mongod
  version: 3.4.2
  storage: wiredTiger

>CONNECTIONS
   total opened: 356
   total closed: 5
  no unique IPs: 1
socket exceptions: 0

>127.0.0.1        opened: 356       closed: 5

**Methods to rule out incorrect answers**

-   The replica set has no primary. Connecting to the replica set with  mongo  --host  m312rs/m312  --port  30000  will always connect you to the primary in a replica set. Additionally, once connected to any mongod in the replica set and running  rs.status()  will show if there is a primary or not.
-   {w: "majority"}  is being specified and it's taking too long for the mongods to acknowledge writes. Inspecting the oplog we can see there are no writes being made.
-   The amount of operations has caused the mongods to reach the CPU limit for the server. Running  top  we can clearly see this is not the case.
