
**Chapter 3: Slow Queries**
## Throughput Drops, Part 4

**Problem:**
Where is the first place to look when you notice a sudden drop in throughput?

 - [ ] The logs
 - [ ] mongotop
 - [ ] mongooplog
___
**Response**

The logs are the correct place to look. There, you can find information on slow queries, as well as connections.

*Mongotop* is useful for telling you _where_ you're spending your time, but isn't the first place to look.

*Mongooplog* is used to replay an oplog from another machine, locally, and isn't useful for this task in any way.

