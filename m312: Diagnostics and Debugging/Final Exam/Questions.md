# Final Exam

## Question 1
**Problem**
Which of the following is/are true of performance drops in MongoDB?

Check all answers that apply:

- [ ] Background index builds may result in a drop in performance.
- [ ] `db.currentOp()` can be used to find long-running processes.
- [ ] If the `.explain()` plan is showing that a query is using an index, then that query has definitely been fully optimized.

**Answer**
- db.currentOp() can be used to find long-running processes.

>**Correct!**

- Background index builds may result in a drop in performance.

> **False**, a foreground index build may cause performance issues due to more memory consumption and collection locks. A background index build avoid locks in a collection, performing the operation when the server can lock the collection for a short periods of time. For this reason this strategy takes longer than foreground but is more safe for production enviroments where you can not disable it for applications in a maintainance window.

- If the `.explain()` plan is showing that a query is using an index, then that query has definitely been fully optimized.

> A query actually could be using an existing index but in a poorly way. To be sure that the query is fully optimized you must analyze the plan summary with `.explain()` and even using the "executionStats" parameter (`.explain("executionStats")`)to get fully information about how long is taking to perform the query.


## Question 2

**Problem**

You have a replica set with the following parameters:

- All members have 1 vote
- Any delayed secondaries, if present, are delayed by 24 hours
- The wtimeout is set to 60 seconds (60,000 ms) for all writes
- Unless specified, all replica set members use the default settings in MongoDB 3.4.
- The replica set has 3 members
   - Including any delayed Secondaries
   - Including at most one Arbiter
- You are using a write concern of { w : "majority" } for all writes

You should also assume the following, in order to keep the problem simple:

- All parts of the system (the network, the servers, etc.) work as intended
- You will never lose enough servers to prevent a Primary from getting elected
- Any server can go down, and if it does, assume that it will stay down until any writes referenced in this problem have occurred on a Primary, and at least 60 seconds have passed.
    If a Primary goes down, a Secondary will be elected Primary in `<` 10 seconds
   - Any choices offered apply only to writes performed after a new Primary is elected, if applicable.
- "Any one server" can mean any single mongod server process: Primary, Secondary, Delayed Secondary, or Arbiter.

Which of the following is/are true?

Check all answers that apply:

- [ ] For a replica set with two data bearing members and one Arbiter (no delayed Secondaries), the application can receive acknowledgment for writes if any one server is lost
- [ ] For a replica set with two standard data bearing members plus one delayed Secondary, the application can receive acknowledgment for writes if any one server is lost
- [ ] For a replica set with three standard data-bearing, non-delayed members, the application can receive acknowledgment for writes if any one server is lost

**Answer**

- For a replica set with two data bearing members and one Arbiter (no delayed Secondaries), the application can receive acknowledgment for writes if any one server is lost

>Wrong, if a bearing node fails, then the application will not be able to receive write acknowledgment for two nodes wichs is the majority within a configuration of 3 nodes.

- For a replica set with two standard data bearing members plus one delayed Secondary, the application can receive acknowledgment for writes if any one server is lost

>Wrong, if a bearing node fails and the other standard node remains plus the delayed secondary node, 60 seconds will not be enough to get write acknowledgment for delayed node, since the delay is about 24 hours.

- For a replica set with three standard data-bearing, non-delayed members, the application can receive acknowledgment for writes if any one server is lost

>Correct!

## Question 3

**Problem**

Which of the following is/are signs that there may be a schema design problem?

Check all answers that apply:

- [X] Lots of collections with flat structures in the database (i.e., no subdocuments or arrays).
- [X] Many (e.g., more than 5) operations are sent to the database in order to load one piece of frequently accessed content in the application.
- [ ] Fields in your documents that are not included in any indexes.

## Question 4

**Problem**

Which of the following is/are true of chunks in a sharded cluster?

Check all answers that apply:

- [X] Chunks that contain documents that all share a single value of the shard key cannot be split.
- [X] It is possible to change the chunk size in a sharded cluster.
- [X] The sharded cluster balances the number of chunks on each shard, not the amount of data.

## Question 5

**Problem**

Given that we don't change the chunkSize settings, which of the following is/are true of jumbo chunks?

Check all answers that apply:

- [X] Jumbo chunks can be moved automatically by MongoDB.
- [X] Jumbo chunks can be split automatically, if the shard key allows it.
- [X] Jumbo chunks can be split manually, if the shard key allows it.
- [X] Jumbo chunks can be moved manually.

## Question 6

**Problem**

To detect applications that are causing problems from our debugging tools, we should:

Check all answers that apply:

- [X] Review historical monitoring information
- [X] Look for spikes in connections
- [X] Review db.currentOp() and check for long running queries
- [ ]  Use a continuous integration tool


