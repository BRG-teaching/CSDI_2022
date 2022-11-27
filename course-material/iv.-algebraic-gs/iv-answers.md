## Task 1: Analysis of trusses

Truss 1: 
![Fig-1-1](../../.gitbook/assets/4ex_1.1.png)
Compared with the truss in tutorial 2. Analysis of a truss, the members in tension are in compression; the members in compression are in tension. A truss under uniform loading behaves like a beam, the top is always in compression and the bottom is always in tension. 


Truss 2: 
![Fig-1-2](../../.gitbook/assets/4ex_1.2.png)
A cantilever truss will have tension in the top chord and compression in the bottom chord. Here are some possible solutions. 
![Fig-1-3](../../.gitbook/assets/4ex_1.2_1.png)
![Fig-1-3](../../.gitbook/assets/4ex_1.2_2.png)

Truss 3: 
![Fig-1-3](../../.gitbook/assets/4ex_1.3.png)
The largest forces in the top chord and the bottom chord are located in the middle of the span. The force magnitude is 40 kN. The largest forces in the diagonals are near the supports. The force magnitude is 28 kN. 
![Fig-1-3](../../.gitbook/assets/4ex_1.3_1.png)
The forces in the members can be reduced by increasing the height of the truss, 


## Task 2: Cantilever arch-cable structure
The cantilever arch-cable structure can be constructed in the following steps: 

Part 1: 
1. Find the intersection point of the reaction force and the load on the most right location. Draw a curve, and find the intersection between the curve and the external loads loads. Redraw the curve as segments. 

![Fig-1-3](../../.gitbook/assets/4ex_2.1.png)

2. Conmpute the form diagram. Assign one force, and compute the force diagram. The external loads are not constant. 
   
![Fig-1-3](../../.gitbook/assets/4ex_2.2.png) 

1. Assign default constraint. Assign target edge magnituede 10kN to the external loads. 
   
![Fig-1-3](../../.gitbook/assets/4ex_2.3.png)

1. Update the diagrams. Note that if your horizontal reaction force is very large, sometimes the solver cannot converge perfectly. The tolerance difference is accepted for this exercise. 
   
![Fig-1-3](../../.gitbook/assets/4ex_2.4.png)

5. Use the form-found arch to construct the input lines for the arch-cable. The upper chord needs to be segments. The top support should be drawn as one horizontal reaction force and one vertical reaction force. 
   
![Fig-1-3](../../.gitbook/assets/4ex_2.5.png)

1. Compute the form and force diagram. 
   
![Fig-1-3](../../.gitbook/assets/4ex_2.6.png)

Part 2: 
Adding diagonals can help the arch-cable to resist non-uniform loadings. 

![Fig-1-3](../../.gitbook/assets/4ex_2.7.png)

Part 3:
For the arch-cable in tutorial 4. The rise of the arch changes to achieve constant force in the upper chord. Similarly, to allow constant force in the lower chord, the rise of the bottom chord needs to move. Thus, we need to unfix the bottom support and add a line constraint to the support so that it remains on the vertical cliff. 

1. We can use edge inspector to find a reasonable edge magnitude to assign to the bottom chord. 
![Fig-1-3](../../.gitbook/assets/4ex_2.8.png)

1. Now assign the constraints. 
   A. Fix the top support on the cliff.
   B. Add default constraint, this will:
   - fix orientation of reactional forces and external loads
   - vertices where external loads are applied remain on the line of action of the load
   - fixed support remain in place
   C. The bottom support is not fixed but should remain on the vertical cliff. Use vertex constraint, select the support, and keep it in y-direction. 
   D. Assign a target constant force in the bottom chord.

![Fig-1-3](../../.gitbook/assets/4ex_2.9.png)

3. Update both diagrams. 
   
![Fig-1-3](../../.gitbook/assets/4ex_2.10.png)

