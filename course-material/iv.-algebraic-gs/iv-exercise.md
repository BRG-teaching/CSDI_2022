# Exercise

# 1. Analysis of truss bridges
A truss is composed of chords and digonal struts. In this exercise you are given a few truss options for a pedestrian bridge. 

1.1. Create a form diagram for the bridge and compute a force diagram representing the equilibrium of the bridge considering the loads on the deck.

1.2 Estimates maximum strength of the trusses considering the kind of material to use and the element’s thickness.

Given material properties -> one edge exceed the maximum force that's allowed. How to modify the form diagram to minimize the force? 

1.3 Compute the loadpath? 

1.4 what is the difference between a truss without diagonals, with one diagonals, and with X diagonals. 

---

# 2. the Chiasso Shed
The Chiasso Shed is one of Robert Maillart(1872–1940)'s most intriguing projects. In this exercise, we study how to use graphic statics to design this structure. 

## 2.1 Analysis of Howe Truss
We will start from a typical triangulated roof structure - a Howe truss. The truss has a span of 18 meters and a height of 3 meters, under constant load 10 kN on each node. Create the form and force diagram of the Howe truss. 

## 2.2 Modification of Force Diagram
You can see that the forces in the top chords are not equal. In
practice, the top chord would be made entirely of a section with sufficient capacity for the highest compressive load. Modify your force diagram, so that 1. the top chord has constant forces. 2. the diagonal elements has 0 forces. 

Hint: Use the edge inspectors to understand the corresponding edges in the form and force diagram. Use force_move_nodes to move the correct nodes. 

Doc questions:
1. explain the steps that you use to modify the force diagram
2. screen shot of the force diagram


## 2.3 Chiasso Shed
1. create form and force diagram
2. our material only allows forces less than XXX. now we want to reduce the forces inside the upper chord. Modify your foce diagram 
3. use constraints to reduce the forces in upper chord 


Doc questions: 
1. explain why we only need to choose one independent edges instead of five in the Howe Truss?
2. to reduce the forces in the upper chord, what will it influence the height of the truss
3. what constraints do you use? make screen shot of the updated form and force diagram. 

## 2.4 constant force in upper and bottom chords
use constraints to find a Chiasso Shed with constant force in both upper and bottom chords.  


# 3. Design your bridge

