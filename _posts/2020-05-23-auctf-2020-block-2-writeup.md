---
title: AUCTF 2020 – Block 2 Writeup
category: hacking
tags: ctf-writeup
---

> Billy runs a minecraft server. He wants to know which block was rolled back. Can you help him?

The challenge also provided an archive called co_block.sql.gz

The first step is extracting the files from the gz file.

We can see that there was just one file compressed, called co_block.sql

We can analyse the first lines of the file using head command:

![Output](/images/auctfblock1.png)

At this point, we realised that the file contains some queries that can be run by MySQL.

So, let’s go ahead and start MySQL:

![Output](/images/auctfblock2.png)

Now, we need to create a new database and run the queries in the sql file by issuing the following commands:

![Output](/images/auctfblock3.png)

Now that we have successfully imported the database, we can enumerate its tables and columns by executing some SHOW and DESCRIBE queries:

![Output](/images/auctfblock4.png)

To conclude we just need to retrieve the row where rolled_back is set to 1:

![Output](/images/auctfblock5.png)

And now we have the flag.

This challenge was solved by my team, [ducks0ci3ty](https://ctftime.org/team/114402).