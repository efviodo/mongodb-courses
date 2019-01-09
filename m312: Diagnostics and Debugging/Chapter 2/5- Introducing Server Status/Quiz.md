**Chapter 2: Tooling Overview**

# Introducing Server Status, Part 2

Can I suppress information from the serverStatus command output?

Check all answers that apply:

- [ ] I can, by specifying in the command syntax which output document fields to omit.
- [ ] No, serverStatus is an administration command therefore it's not possible to suppress information.

___

The correct answer is:

I can, by specifying in the command syntax which output document fields to omit.

```
db.runCommand({ "serverStatus": 1, "repl": 0, "locks": 1})
```

Neither of the others are correct. As shown in the video for Part 1, you can explicitly include or omit fields from serverStatus in the command. Adding repl: 0, for example, omits it.
s
