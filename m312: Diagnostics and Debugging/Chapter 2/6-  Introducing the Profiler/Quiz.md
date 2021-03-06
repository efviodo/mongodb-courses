**Chapter 2: Tooling Overview**

# Introducing the Profiler

You have a three-member replica set, capturing time-series data and serving queries. When you turn on the profiler, you find that the application immediately sees high response time on its queries.

Why does profiling interact poorly with this high-volume production workload?

Choose the best answer:

Turn off profiling, now!

____

**Answer**

In this quiz, we're being a little silly, but seriously, the profiler is a diagnostic tool, and you should expect it to routinely attenuate performance on a production system.

Don't turn it on unless you're willing to accept that, and turn it off when you're done.

