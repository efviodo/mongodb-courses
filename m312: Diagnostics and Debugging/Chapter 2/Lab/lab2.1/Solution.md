**Chapter 2: Tooling Overview**

# Lab: Analyze Log Components

From configuration file we extrtac the location of mongo logs file:

```
cat single.cfg 

systemLog:
  destination: file
  path: /home/vagrant/single.log
processManagement:
  fork: true
net:
  port: 27000
  maxIncomingConnections: 10
storage:
  dbPath: /home/vagrant/data

```

Then we analyse the logfile and read what is happening:

```
cat /home/vagrant/single.log
```

Eureka!!

```
2019-01-09T20:55:43.239+0000 I NETWORK  [thread1] connection refused because too many open connections: 10
```

Mongo server is no longer accepting connections due to max open connections was reached. From log message we can affirm that the component is *NETWORK*

**Answer**

NETWORK
