# Exercise


{% hint style="warning" %}
Complete the tasks below, and submit **by 9:00am on Friday, December 2nd one zipped folder** that includes:

1. the Rhinoceros file.
2. 3 IGS session file.
3. The completed questionnaire (PDF).

Please follow the file naming convention as shown in the [**Syllabus**](../../syllabus.md#submissions).

### ****[**Submit here**](https://polybox.ethz.ch/index.php/s/xB0jt4XbfkHXWIk)**** (TODO)
{% endhint %} 

{% hint style="info" %}
For **each task** save the IGS session file. Rename them as `exercise-4_task_1_Name.igs`.

{% endhint %}

## Tasks
Complete the following three tasks.&#x20;

# Task 0: Theory: Static determinacy
![Fig-1-1](../../.gitbook/assets/dof.png)
In the lecture, we have learned the concept of static determincy. 
Identify the following structures. Is it a cable / arch, arch-cable or truss? Is it unstable 




# Task 1: Analysis of truss bridges

In the first task, you will analyse and modify 3 trusses. 

Assume that: 
* The total weight applied to the central portion of the deck is 50 kN. They are distributed equally: 10 kN at each loaded node.
* All the trusses have a pin support (fixed in X and Y) in the left and a roller support (fixed Y) in the right.
* The position of the supports can be either on the upper chord or on the lower chord. 

Here are the three truss(Fig-1-1): 
1. Truss bridge with N diagonals
2. Truss bridge with V diagonals
3. Truss bridge with K diagonals
![Fig-1-1](../../.gitbook/assets/3_truss_bridges.png)

You need to: 
* Compute the form and force diagrams of the three trusses. 
* Compare the truss 1 with the truss we have analysed in tutorial 2. Analysis of a truss. List the difference between the two trusses.
* Change the support locations of truss 2 so that the top chord is in tension and the bottom chord is in compression. Modify the input lines for truss 2 and compute the form and force diagram.
* In truss 3, which members of the top and bottom chord have the largest forces? Which members in the diagonals have the largest forces? What are the force magnitudes in these members? Perform a geometric modification of truss 3 so that the internal forces in the members are reduced. 



# Task 2: Cantilever arch-cable structure under uniformly distributed load 

The design team faces a challenging project to build a 15.0m cantilever arch-cable viewing platform on a cliff. 

![Fig-1-3](../../.gitbook/assets/diagram_cantilever.png)

Assume that:
* The total weight applied to the deck is 50 kN, assume that the deck is divided in 5 pieces such that the load of 10 kN should be applied at each loaded node.
* The cliff is vertical and the platform can be anchored anywhere on the cliff. 

The design team decide to use the following step to design the platform. 

1. Form-find the arch under the weight of the deck so that the horizontal span of the arch is equal to the span of the platform. 

2.  Construct the arch-cable using the form-found arch. Transfer the load on the arch to the upper chord. Compute the form and force arch to varify the design. 


The design team wants to modify the design so that the platform will keep a flat deck but have constant force in the lower chord. Is it possible to find a design solution considering the current support locations? If it's possible, compute the final results. If it's not possible, could you propose a solution so that constant force can be achieved? Hint: changing the support locations and cantilevering span is allowed.


# Task 3: Design your bridge

In the last task the design team is going to build a bridge connecting the left cliff and the right island(Fig-1-4). The distance between the left cliff and the middle island is 30 meters. The distance between the middle island and the right island is 15 meters. 


![Fig-1-4](../../.gitbook/assets/bridge_design.png)

Assume that:
* The weight of the deck is 5 kN/m. The weight should be equally distributed along the span. However, you are free to divide the deck in as many slices as you want.

* Due to the soil property, the bridge cannot be anchored on the right island. You are allowed to anchor anywhere on the left cliff, and on the peak of the middle island. The deck that is supported by the middle island and hangs over the right island can be longer than 15 m. 

* In your design the deck does not need to remain horizontal.
  
* Be creative :) 

Propose two bridge designs. One should be made of trusses, and the other one of arch-cable. 


## Deliverables

Please submit the following elements:

1. Five .igs files corresponding to the structures analysed throughout the 3 tasks.&#x20;
2. The PDF-Document with your answers and screenshots. \
   _The **formatting** must be kept **clean** and the **word limits** must be respected._
3. (optional) the Rhino (.3dm) file with the structures in separate layers.\
   _For each completed structure before clearing the scene to initiate the next one you can copy the layer_ `IGS>>FormDiagram` _and_ `IGS>>ForceDiagram` _and rename them, for example as_ `IGS_task1_A>>FormDiagram`  and `IGS_task1_A>>ForceDiagram` in _this way they will not be deleted as you move on to the next task. This is a great way to keep track of your advances in the extecise_