
**Chapter 5: Schema Issues**

## Investigate Schema Issues

**Problem**

In this homework assingment we are expecting you to have the **m312RS** Replica Set cluster up and running in your VM. To get it started you can run the following command:

>mlaunch init --replicaset --wiredTigerCacheSizeGB 0.3 --host localhost \ --port 30000 --oplogSize 100 --name m312RS --dir /data/m312

Download the handout, and add it to the VM. Initialize the database by running the following:

>./library_db_simulator.py --init

This will drop the m312 database, populate its collections, and create indexes. You can run it with --help to control some of the parameters it uses.

Next, run it in the following mode:

>./library_db_simulator.py --simulate

After the first batch of queries, each time you hit enter, it will simulate someone checking out a book. Your task is to determine which of the following are issues:

Check all answers that apply:

- [ ] The schema suffers from excessive normalization.

- [ ] The application is triggering many more queries than are necessary for each operation.

- [ ]  The application is creating too many connections to the replica set without closing them.

