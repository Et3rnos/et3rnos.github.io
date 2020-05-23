---
title: Juni0r Dashboard Writeup
category: hacking
tags: ctf-writeup
---

For this challenge we are only given this link:

[http://ctf1.epizy.com](http://ctf1.epizy.com)

By navigating to the page and analysing its source we find a comment with the challenge instructions.

![Output](/images/custjunior1.png)

So, we must find a way to log in into Juni0r Dashboard.

Juni0r also gives us a clue:

> PS: I hope Google won’t index this page…

Probably the site has a robots.txt file. This type of file is used to define what directories/files should the crawlers index and what they should not.

It is time to go to robots.txt and see its content.

![Output](/images/custjunior2.png)

We realize that the directory \_LOGS\_ is being prevented of becoming indexed by crawlers like Google.

We go to that directory and we find out that there is a log file inside of it, so we also open it.

![Output](/images/custjunior3.png)

By analysing it, we see that a MD5 hash (the authentication one) is being compared with a bunch of 0s (because Juni0r forgot to add his real hash) using == operator.

The fact that the hashes are being compared with == operator instead of === makes possible that different string values be evaluated to the same values because == only checks if the hashes have the same value and === checks if they have the same type and value.

This is called a Type Juggling Vulnerability.

This implies that if the user submit a password whose hash is something like “0e39821391823128” it will evaluate into 0^39821391823128 and consequently 0.

By the same reason, “00000000000000000” evaluates to 0. So, “0e39821391823128” = “00000000000000000” because 0 = 0.

But now we need to find passwords whose MD5 hashes are in this form.

By searching for magical MD5 hashes (hashes that come in the form 0e98329183…), I came with this page:

[https://github.com/spaze/hashes/blob/master/md5.md](https://github.com/spaze/hashes/blob/master/md5.md)

So, let’s test the first password:

```
240610708:0e462097431906509019562988736854
```

By inputting 240610708 into the password field we are congratulated with the flag because “0e462097431906509019562988736854” == “00000000000000000000000000000000” returned true!

![Output](/images/custjunior4.png)