**Chapter 4: Connectivity**

## Closing and Dropping Connections, Part 4

**Problem**

Which of the following will affect the number of available incoming connections a mongod instance will allow to be established?

Check all answers that apply:

- [ ] OS ulimits

- [ ] net.maxIncomingConnections  configuration file parameter

- [ ] 65536 is the max number of connections, no other limit will apply
___
**Answer**


The following are true:

-   OS ulimits
    -   The number of allowed open files will affect the number of connections that a mongod will be allowed to establish
-   net.maxIncomingConnections  configuration file parameter
    -   This configuration option will allow the system administrator to determine a max number of incoming connections

This is false:

-   65536 is the max number of connections, no other limit will apply
    -   Obviously, this can't be true, since the others are.
