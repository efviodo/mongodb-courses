**Chapter 2: Tooling Overview**

# $indexStats, Part 5

**Problem**

You have a sharded cluster with 4 shards. The products collection is sharded on { name : 1, dateCreated : 1 }. There are 4 chunks, one on each server, and here is the range of the shard key:

s1: { name: MinKey, dateCreated: MinKey}  - { name: "e", dateCreated: MinKey}
s2: { name: "e", dateCreated: MinKey}  - { name: "g", dateCreated: MinKey}
s3: { name: "g", dateCreated: MinKey}  - { name: "m", dateCreated: MinKey}
s4:{ name: "m", dateCreated: MinKey}  - { name: MaxKey, dateCreated: MaxKey}

You have the following indexes:

{ _id: 1 }
{ name: 1, dateCreated: 1 }
{ price : 1 }
{ category: 1 }

You perform the following query:

db.products.find( { name : { $in : [ "iphone", "ipad", "apple watch" ] } } )

Which of the shards will increment their value of $indexStats for an index as a result of this query?

Check all answers that apply:

- [ ] s1
- [ ] s2 
- [ ] s3
- [ ] s4

_______________

s1
s3
