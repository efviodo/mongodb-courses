**Chapter 4: Connectivity**

### Lab: Diagnosing unknown issues

**Problem**

In this lab, you are asked to diagnose an unknown issue. Developers relying on a MongoDB deployment you administer are complaining that database is taking longer and longer to respond. Additionally, the server which the  **current primary**  is on crashes after an unspecified amount of time. This happens on every server.

You can download the required dataset,  [companies.json](https://s3.amazonaws.com/m312/companies.json), here.

Let's go ahead and setup the environment.

-   First, launch a replica set using mtools with the name "m312rs"

>cd m312-vagrant-env
vagrant up
vagrant ssh
mlaunch --replicaset --name "m312rs" --port 30000 --wiredTigerCacheSizeGB 0.5 --oplogSize 100

-   The following step is to download the necessary handouts and make them available in your  **m312**  virtual machine:

>cp Downloads/lab1_chapter4.py m312-vagrant-env/shared
cp Downloads/companies.json m312-vagrant-env/dataset

_The command line example is set for Unix but a simple copy of this file will suffice_

-   Next, we will load the dataset into our replica set. Let's load the data into a collection named  **companies**

>vagrant ssh
mongoimport --host m312rs/m312 --port 30000 -d m312 -c companies /dataset/companies.json

-   Now execute the homework script

>/shared/lab1_chapter4.py

-   Open a new terminal window and make sure to ssh in to your vagrant box.
-   Let the script run for a minute and begin checking the replica set. What is the primary issue?

Check all answers that apply:

- [ ] {w: "majority"}  is being specified and it's taking too long for the mongods to acknowledge writes.
- [ ] The connection pool continually grows, ultimately starving the server of resources.
- [ ] The replica set has no primary.
- [ ] The amount of operations has caused the mongods to reach the CPU limit for the server.
