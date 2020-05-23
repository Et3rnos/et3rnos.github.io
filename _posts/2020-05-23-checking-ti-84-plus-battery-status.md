---
title: Checking TI-84 Plus Battery Status
tags: ti-basic
category: programming
---

In this tutorial, I am going to create a program that will automatically check your battery status and retrieve this value to you.

To achieve this result, you will need to create two programs, one written to be executed directly into the calculator processor and another written in TI-BASIC.

## Retrieving battery status

First, create a program called HACKS with the following contents in it:

```
AsmPrgm
EF6F4C3D280A78FE1E
3805
EF21521808
EFB3503E042001AF
EF8C47EFBF4AC9
```

Note that you must write that code exactly, otherwise, the calculator might crash.

Now execute it by going to Catalog and locating the Asm( function. Then just go to the programs index and execute BAT one.

![Output](/images/tibat1.png)

Now a value from 0 to 4 is stored into Ans. This corresponds to your battery level.

## Prettyfying the result

Now, you must create a program that will execute the HACKS one and present the value in the form of a progress bar.

First, we clear the screen and execute HACKS:

```
ClrHome
Asm(prgmHACKS
```

Then we create the program graphical part, and we output the sum of Ans to 1 so that now 1 means very low battery and 5 fully charged:

```
Output(2,4,"BATERRY( )"
Output(2,12,Ans+1
Output(3,2,"+------------+"
Output(4,2,"I            I"
Output(5,2,"+------------+"
```

And for the progress bar, we check the value of Ans and output different number of \* for each case.

```
If Ans=0
Output(4,3,"*"
If Ans=1
Output(4,3,"****"
If Ans=2
Output(4,3,"*******"
If Ans=3
Output(4,3,"**********"
If Ans=4
Output(4,3,"************"
```

After that, all we have to do is to add some Disp “” instructions to pad the program appropriately and add “” to the final in order to suppress Done message.

```
Disp ""
Disp ""
Disp ""
Disp ""
Disp ""
""
```

## Final Effect

![Output](/images/tibat2.png)