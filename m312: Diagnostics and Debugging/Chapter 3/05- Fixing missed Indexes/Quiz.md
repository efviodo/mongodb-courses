**Chapter 3: Slow Queries**

## Fixing Missing Indexes

**Problem:**
Which of the following are true?

Check all answers that apply:

 - [ ]  If your system is under load, using a "rolling upgrade" is the recommended way to build an index.
 - [ ] If you have a heavy write load, it is recommended to build indexes in the foreground on the Primary.
 - [ ] Compass does not help with indexes.
 - [ ] We can use Ops Manager to rebuild our indexes
 - [ ] mtools is another tool that can help you build indexes.

___
**Answer:**

Here are the incorrect answers:

-   If you have a heavy write load, it is recommended to build indexes in the foreground on the Primary.
    -   First, you should avoid building indexes on a Primary with a lot of traffic, and certainly not in the foreground, which blocks the writes to the collection.
-   Compass does not help with indexes.
    -   You can visualize your indexes, and even create new ones, with Compass.
-   mtools is another tool that can help you build indexes.
    -   mtools is great, but it does not help for managing indexes.

Here are the correct answers:

-   If your system is under load, using a "rolling upgrade" is the recommended way to build an index.
    -   The rolling upgrade will prevent undue load on the primary during the index building process. You can do this either manually, or with Cloud/Ops Manager.
-   We can use Ops Manager to rebuild our indexes
    -   This is correct, Ops Manager has the functionality to rebuild and create new indexes.

