**Chapter 4: Connectivity**

## Timeouts

**Problem**

wtimeout can be set by the application to guarantee that:

Check all answers that apply:


- [ ] If a write is acknowledged, the replica set has applied the write on a number of servers within the specified wtimeout.

- [ ] MongoDB will roll back the write operations if the nodes do not acknowledge the write operation within the specified wtimeout.

- [ ] The application will learn how many servers have performed the write within wtimeout.

___
**Answer**

The correct answer is:

-   If a write is acknowledged, the replica set has applied the write on a number of servers within the specified wtimeout.

Incorrect answers are:

-   MongoDB will roll back the write operations if the nodes do not acknowledge the write operation within the specified wtimeout.
    -   MongoDB does not roll back writes that fail to achieve the write concern's "w" parameter within the specified wtimeout. If the primary has received them, they are most likely on the primary, and possibly other servers. Any further writes will need to be done by the application.
-   The application will learn how many servers have performed the write within wtimeout.
    -   All the application knows is that it has not received acknowledgment within wtimeout. No further information is known at this time.
