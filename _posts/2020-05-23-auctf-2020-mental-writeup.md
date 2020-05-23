---
title: AUCTF 2020 – Mental Writeup
category: hacking
tags: ctf-writeup
---

> Password Format: Color-Country-Fruit
>
> Hash: 17fbf5b2585f6aab45023af5f5250ac3

By analyzing the information provided we realized that the hash is probably a MD5 one because it is 32 characters long and hex-encoded.

Using hash-identifier on Kali Linux returns the same result:

![Output](/images/auctfmental1.png)

The first thing we tried was a rainbow table attack where we compared the hash with pre-computed hashes to see if there is a match.

However, this type of attack failed:

![Output](/images/auctfmental2.png)

So, we moved on and decided to brute-force the password.

We downloaded some wordlists containing a bunch of color, country and fruit names.

Here are the links to them:

- [Colors](https://raw.githubusercontent.com/imsky/wordlists/master/adjectives/colors.txt)
- [Countries](https://gist.githubusercontent.com/kalinchernev/486393efcca01623b18d/raw/daa24c9fea66afb7d68f8d69f0c4b8eeb9406e83/countries)
- [Fruits](https://raw.githubusercontent.com/imsky/wordlists/master/nouns/fruit.txt)

Then we converted every word in those files to the title format, which means that the first letter of the words will be capitalized. You can use a website like [ConvertCase](https://convertcase.net/) to achieve that.

We also built a Python program to concatenate the words together using the format given (Color-Country-Fruit), create a MD5 hash using the string and then compare it to the given hash:

```
import hashlib

for color in open("colors.txt", "r"):
    color = color.strip()
    for country in open("countries.txt", "r"):
        country = country.strip()
        for fruit in open("fruit.txt", "r"):
            fruit = fruit.strip()
            passwd = "{}-{}-{}".format(color, country, fruit)
            passwd_hash = hashlib.md5(passwd.encode()).hexdigest()
            if (passwd_hash == "17fbf5b2585f6aab45023af5f5250ac3"):
                print(passwd)
```

If there is a match, we print the password to the screen. Simple as that:

![Output](/images/auctfmental3.png)

That way we could determine the password and, consequently, the flag.

This challenge was solved by my team, [ducks0ci3ty](https://ctftime.org/team/114402).