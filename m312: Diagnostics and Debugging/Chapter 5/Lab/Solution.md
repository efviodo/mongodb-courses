**Chapter 4: Connectivity**

## Quiz

The correct answer is:

The application is triggering many more queries than are necessary for each operation.

You can see this in a number of ways. The most apparent way is to turn on the profiler:

>db.setProfilingLevel(2)

and then hitting "enter" on the simulated application.

Then turn off the profiler and count the queries.

>db.setProfilingLevel(0)
db.system.profile.count()

Far too many operations (read AND write) are occurring.

You can also see this if you run mongostat.

The following are not correct:

- The schema suffers from excessive normalization.

You can look at the fact that there are only 4 collections to see this.

You will also notice that the book's "checked out" status is logged in the "users" collection. Each user has a list of checked-out books, with a unique index on the book_id. If you query this, you can determine if a book is checked out or not.

- The application is creating too many connections to the replica set without closing them.

You can see that this is not a problem by looking at mongostat, or by examining the logs, where you can see that the number of connections doesn't spike.

