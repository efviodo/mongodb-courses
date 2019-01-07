**Chapter 3: Slow Queries**

## Throughput Drops

### Personal notes

#### How an update query does it works on WiredTiger?

First of all, MongoDB creates a new version of the document. Onces the new document is inserted (which is done in a single CPU operation) the pointer to the first document is replaced to the second. In this way you can make reads and write at the same time.  While the new version of the document is being written, incoming reads are performed on the old document version. 
This is called *Multi-version Concurrency Control*.
More info see: https://www.youtube.com/watch?v=nE8a3RNeH5E&feature=youtu.be
 
#### Write Contention
From MongoDB [FAQs](https://docs.mongodb.com/manual/faq/concurrency/) we can see what happens when two or more process attempt to modify the same document: conflicts!! MongoDB with WiredTiger uses optimistic concurrency control so eventually one process will lock the document and make the write operation while the other process will get lock.
If you have these issue you will see a bunch of slow queries for example in mongo logs, using profiler or may be ``db.currentOp()``. Particularly pay attention to the followings in mongo log:

 - writeConflicts
 - numYields
