**Chapter 2: Tooling Overview**

# Overview: Server Diagnostic Tools

From the following list, which tool(s) can I use to know, in real time, the number of queries / second occurring in a given replica set?

Check all answers that apply:

- [ ] mongoperf
- [ ] mongostat
- [ ] mongotop
- [ ] mongoreplay
____

**Answer**

Only mongostat has this functionality. mongoreplay can capture the queries, but doesn't let me know how many are coming in each second in real-time. mongotop looks at time spent in each namespace, but doesn't count queries. mongoperf only looks at simulating a disk I/O load, not at monitoring performance at all.
