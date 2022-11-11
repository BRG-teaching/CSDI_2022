# Exercise 1

This exercise is meant for you to practice a bit of Python programming. This exercise is not mandatory and will not be graded.

{% hint style="warning" %}
The tasks of this exercise can be solved in several ways!
{% endhint %}

## Task 1: loop

Create an algorithm using a for loop that generates the following list: \[7, 14, 21, 28, 35, 42, 49, 56, 63, 70].&#x20;

## Task 2: loop and conditional

Given the following list L1=\[\[5,3],\[0,3],\[0,7],\[6,-6],\[10,-3],\[11,8],\[6,0],\[1,1]], create a new list (L2) **only** with the lists from L1 **if** the two items add up to 7 or more than 7. For example: item "\[5,3]", 5+3 >= 7, so this list is good!

## Task 3: geometry

Create an algorithm that draws a spiral in 2D. To do this create a for loop that adds a point, rotates it around \[0,0,0] and stores it in a list. After, outside the for loop, use rs.AddPolyline to create a polyline connecting the spiral dots.

## Task 4: loop and conditional

Given the following list L1=\[\[3,4],\[5,3,4,5,1],\[0,3,-2,3],\[0,7],\[6,-6,1],\[10,-3],\[11],\[6,0,5,6],\[1,1,3],\[0,8]], create a new list (L2) only with the lists from L1 that have 3 or more items.

## Task 5:  loop and conditional

Given the following list L1=\[\[3,4],\[5,3,4,5,1],\[0,3,-2,3],\[0,7],\[6,-6,1],\[10,-3],\[11],\[6,0,5,6],\[1,1,3],\[0,8]], create **inside of one single loop**:&#x20;

* a new list (L2) only with the lists from L1 that have 3 or more items.&#x20;
* a new list (L3) only with the lists from L1 that have 3 or more items and whose items add up to 5 or more.&#x20;
* a new list (L4) only with the lists from L1 that have 3 or more items and whose items add up to less than 5.&#x20;

{% hint style="success" %}
Hint:&#x20;

Use the sum() function to add all the items from a list. For example:&#x20;

L=\[3,4,-4]&#x20;

print sum (L)

Output: 3
{% endhint %}

## Task 6: geometry

Create an algorithm that draws a 3D helicoidal curve as the one shown in the mage below. To do this, create a "for" loop that adds a point, rotates it around another point, moves it in the z direction, and stores it in a list. After, outside the for loop, use rs.AddPolyline to create a polyline connecting the helicoid dots.





### Solutions:

{% file src="../../.gitbook/assets/CSDI_III_exercise1_solution (1).gh" %}



