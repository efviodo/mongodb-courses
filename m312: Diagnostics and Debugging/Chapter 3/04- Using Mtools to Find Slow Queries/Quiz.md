**Chapter 3: Slow Queries**

## Using Mtools to Find Slow Queries

**Problem:**

Which of the following is/are true?

Check all answers that apply:

- [ ] Mtools has a command line tool to list the slow queries from a mongod log.
- [ ] Mtools has a command line tool to list the slow queries from the profiler.
- [ ] Mtools lets you see and slow queries in a two dimensional plot.
- [ ] Both mloginfo and mplotqueries have the ability to filter the slow queries per-collection, as well as other criteria.
- [ ] Mtools is not officially supported by MongoDB.

___
**Answer**

Incorrect answers:

-   mtools has a command line tool to list the slow queries from the profiler.
    -   The set of tools in mtools is using the mongod log, it can't interpret results from the collections saved by "mongod" profiler.
-   Both mloginfo and mplotqueries have the ability to filter the slow queries per-collection, as well as other criteria.
    -   mplotqueries let you do it from its UI, however for mloginfo, you will have to rely on mlogfilter to do it before processing the file.

Correct answers:

-   Mtools has a command line tool to list the slow queries from a mongod log.
-   Mloginfo will do this, and it can be done with mplotqueries, as well.
-   Mtools lets you see and slow queries in a two dimensional plot. * Yes, mplotqueries and mlogvis will both allow you to do this.
-   Mtools is not officially supported by MongoDB. * Mtools is an open source project that is very useful, but it is not officially supported by MongoDB.

