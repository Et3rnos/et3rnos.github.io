---
title: Advanced TI-BASIC Quadratic Formula
---

One of the most useful programs you can have in your TI calculator is the Quadratic Formula.

During this tutorial, I will teach you how you can do your own program to calculate the solutions of any equations of the following type:

```
ax^2+bx+c=0
```

First, we need to get **a**, **b** and **c** values from user. To achieve this we will use some Input instructions preceded by a ClrHome one, that tells the processor to clear the screen.

```
ClrHome
Input "A=",A
Input "B=",B
Input "C=",C
```

These “inputs” retrieve the values from the user and store them in the variables A,B and C.

![Inputs](/images/quadform1.png)

Then we will clear the screen once more and add some Disp “” instructions that will be discussed later.

```
ClrHome
Disp ""
Disp ""
Disp ""
Disp ""
Disp ""
```