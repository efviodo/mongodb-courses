**Chapter 3: Slow Queries**

## Lab: Building an Index in the Foreground in Production

**Problem:**

In this lab, you're going to simulate a foreground index build, in production.

Setup:

    Download the handouts, and unpack. Place the following in your vagrant VM's shared directory:
        set_up_building_index_in_foreground.sh
        building_index_in_foreground.py
    Download and unpack the employees.zip dataset and place it in your vagrant's /shared directory.
    Run set_up_building_index_in_foreground.sh from the /shared directory within your VM, which will do each of the following:
        Kill any mongod server processes running in the VM
        Delete the ~/data directory
        Start a replica set listening on ports 30000, 30001, and 30002.
        Ensure that the server on port 30000 has the highest priority
        Sleep for 20 seconds to ensure that a Primary has been elected
        mongoimport the employees.json file into the m312.employees namespace.
    Next, you'll want to simulate your application, and trigger your index build. If you've set everything up as described here, run building_index_in_foreground.py.

While this is going on, feel free to run mongostat against your server to get a feel for what's going on while your "application" is running.

The python script will do the following:

Your job is to go in and find the index build, plus any evidence of long-running read/update operations that occur as a result of the index build. Be careful not to mistake other operations (such as the mongoimport) for the index build.

Note:

You may find it helpful to rotate your log files , expecially if you run the python script more than once.

To demonstrate that you've identified both the index build, and the long-running operations, answer the following question:

When do the long-running operations begin to appear in the log files, based on their timestamps?

Choose the best answer:

- [ ] More than a minute before the index build began.
- [ ] Less than one second before the index build began.
- [ ] Less than one second after the index build began.
- [ ] More than one second after the index build began, and also more than one second before the index build ended.
- [ ] Less than one second before the index build ended.
- [ ] Less than one second after the index build ended.
- [ ] More than one second after the index build ended.
- [ ] More than a minute after the index build ended.

**Answer**

Less than one second after the index build ended
