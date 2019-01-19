**Chapter 4: Connectivity**

## Hostnames and Cluster Configuration

**Problem**

When connecting to a MongoDB Cluster, I should guarantee that:

Check all answers that apply:

- [ ] All mongos's and replica set members are addressable by the client and application hosts

- [ ] The application should use more than one replica set member in the connection string

- [ ] We can set any NIC or hostname for our replica set configuration set, since MongoDB will figure things out for us.

___

**Answer**

The following are true:

All mongos's and replica set members are addressable by the client and application hosts
The application should use more than one replica set member in the connection string
Confirming these can avoid problems with hostnames later on.

The following is false:

We can set any NIC or hostname for our replica set configuration set, since MongoDB will figure things out for us.
Definitely not the case. MongoDB will use the hostnames given, which may seem to work fine until a part of the cluster (or the application) can no longer rely on its hostnames.
