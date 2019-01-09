**Chapter 2: Tooling Overview**

# currentOp and killOp

db.currentOp() is useful for finding which of the following?

Check all answers that apply:

- [ ] Any long-running operations on the server
- [ ] Connections that have been open for a long time
- [ ]Operations that are individually short-lived, but which are hammering the server and causing performance issues

__________

**Answer**

"Long-running operations" is the only answer to which one could give an unqualified yes.

Connections that have been open for a long time may not be associated with any particular operation, so they won't show up in currentOps unless they are running an operation currently.

Short-lived operations may show up in currentOp, but they will only be present if it is run when the operation is in progress. In general, db.currentOp is bad at finding short-lived processes, even ones that are numerous.

