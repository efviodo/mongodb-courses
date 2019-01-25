**Chapter 4: Connectivity**

## Write Concern and Timeouts

**Problem**

For a 7-member replica set with one arbiter and one delayed secondary, how many members are needed in order to acknowledge { w : "majority" } before the wtimeout is hit?

Choose the best answer:

- [ ] 1
- [ ] 2
- [ ] 3
- [ ] 4
- [ ] 5
- [ ] 6
- [ ] 7

___

**Answer**

For a 7-member replica set, the answer is always 4. The arbiter and the delayed secondary don't change that fact.

The danger is that, if there's both an arbiter and a delayed secondary, there are only 5 other servers that are providing availability. If two data-bearing servers go down, your replica set will be able to elect a primary, but will not be able to acknowledge writes with { w : majority }.
