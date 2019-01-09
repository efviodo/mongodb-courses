**Chapter 2: Tooling Overview**

# Introducing Server Logs

**Problem**

Which of the following are best learned from the server logs?

Check all answers that apply:

- [ ] Attempts Remaining:∞Unlimited Attempts
- [ ] How many connections your server has
- [ ] Which of your queries have been long-running
- [ ] Which indexes you have

___

The correct answers are:

How many connections your server has

Which of your queries have been long-running

The incorrect answer is:

Which indexes you have

Just to be clear, you might be able to find information on indexes you recently built from your server logs, since they store which indexes you build, but this is better learned from the db.collection.getIndexes() command in the administrative shell.

