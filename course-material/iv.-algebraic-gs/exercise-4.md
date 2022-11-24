# Exercise

{% hint style="info" %}
Please complete the tasks below, and submit a zipped folder that includes what is required in the [deliverables](exercise-4.md#deliverables) by **9:00 am on Friday, November 19th**.

Please follow the file naming convention as shown in the [**Syllabus**](../../syllabus.md#submissions).  &#x20;

### [Submit exercise 4 here.](https://www.dropbox.com/request/MBoYGa0qljZqrECCU1m1)
{% endhint %}

## Rhinoceros file and template <a href="#rhinoceros-file-and-template" id="rhinoceros-file-and-template"></a>

Download here the Rhinoceros file with the initial lines that should be used in the tasks

{% file src="../../.gitbook/assets/exercise-4_template.3dm" %}

Then answer the questions on the following document:

{% file src="../../.gitbook/assets/CSD1_2021_exercise-4_template (1).docx" %}

Remember to save each subtask as an individual `.igs` with the function `Save Session` as they are needed in the submission. To keep track of your progress you can duplicate the layer `IGS` (with its sublayers) after completing each task/subtask and rename it to `IGS_taskX` so the lines get stored in the Rhinofile. Optionally, you can submit this too. Check the [deliverables](exercise-4.md#deliverables) expected.

## Task 1: Analysis of a truss bridge



In the first task we will study of the following truss bridge. It is composed of 21 internal edges and supports on both extremities. The total span is 18m. The initial design is presented in Figure 1. The structure is divided into 6 modules and has a structural height of 3 m.

![FIgure 1: Geometry of the truss bridge to analyse with boundary conditions and loads applied.](<../../.gitbook/assets/image (243).png>)

&#x20;Assume that:

* The total weight applied to the central portion of the deck is 50 kN, distributed equally: 10 kN at each loaded node.
* The boundary conditions should be equivalent to the image: pin support (fixed in X and Y) in the left and a roller (fixed Y) in the right.

You will help the design team to analyse the bridge from Figure 1 using graphic statics and IGS to evaluate the forces in this preliminary design to do that:

* **A) Compute the form and force diagrams of to answer to the questions** about the structural behavior of the structure in the template and identify the member with the highest load.
* **B)** Propose a **modification in the geometry** of the structure such that the load in the member carrying the highest load is reduced.

{% hint style="info" %}
For this first task save 2 files with the structures created in parts A, and B. Rename them as `exercise-4_task1_A_Name.igs` and `exercise-4_task1_B_Name.igs` and submit together with the .pdf template.
{% endhint %}

## Task 2: Constant Force bridge(s) (2.0 pt) <a href="#rhinoceros-file-and-template" id="rhinoceros-file-and-template"></a>

In the second task we will use concepts that we learned about Force Control. The bridge design team faces a challenging project. They are requested to design a bridge with 18.0m span in an inclined valley represented in Figure 2:

![Figure 2: Inclined deck to consider for Task 2.](<../../.gitbook/assets/image (304).png>)

We will assume that:

* The total weight applied to the deck is 50 kN, assume that the deck is divided in 6 pieces such that the load of 10 kN should be applied at each loaded node.
* The deck of the proposed bridge (where the loads should be applied) must remain linear, following the profile observed (with the inclination of 15˚).
* The boundary conditions should be equivalent to the image: pin support (fixed in X and Y) in the left and a roller (fixed Y) in the right.

Besides the inclination, the contractor asks that the main supporting part of the bridge use member with a constant force so they can be all be produced exactly with the same cross section. Your design team is required to propose two designs: A, and B, such that:

* **A:** In design A the deck is **supported by below** with a structure using **constant force** members in **tension**.
* **B:** In design B the deck is **supported by above** with a structure using **constant force** members in **compression**.

For each design respond the structural questions related in the .pdf template provided.&#x20;

{% hint style="success" %}
Note: The force in the deck itself do not need to respect any force requirement. Also the members connecting the deck to the main supporting structure do not need to respect any force requirement.
{% endhint %}

{% hint style="info" %}
Save 2 files with designs A and B. Rename them as `exercise-4_task2_A_Name.igs` and `exercise-4_task1_B_Name.igs` and submit together with the .pdf template.
{% endhint %}

## Task 3: Design your bridge (2.0 pt) <a href="#rhinoceros-file-and-template" id="rhinoceros-file-and-template"></a>

In the last task the design team has a new exciting project to build a bridge in the cliff of Figure 3. Propose a new design for the bridge respecting the following assumptions:

![Figure 3: Cliff to consider for Task 3.](<../../.gitbook/assets/image (129).png>)

* The weight should be equally distributed in the bridge totalling 50 kN, you are free to divide the deck in as many slices as you want.
* In addition to the extremity points of the passage, you are free to add additional supports along the cliff in the points A, B, C, D, or E pre-defined in the template.&#x20;
* In your design the deck does not need to remain horizontal.&#x20;
* Be creative!

Add a **screenshot** of the form and force diagrams in equilibrium associated with your design and respond to the questions in the .pdf template.

{% hint style="success" %}
Note that, if the two extremities of the passage are considered as support (as in Part I), you don't need to assign forces to the supports. However, if you support elsewhere in the cliff, and the extremities of the passage are no longer supports, the total 50 kN should also be distributed to these nodes (summing the same total of 50kN).
{% endhint %}

{% hint style="info" %}
Save your design and rename it as `exercise-4_task3_Name.igs` and submit together with the .pdf template
{% endhint %}

## Deliverables

Please submit the following elements:

1. Five .igs files corresponding to the structures analysed throughout the 3 tasks.&#x20;
2. The PDF-Document with your answers and screenshots. \
   _The **formatting** must be kept **clean** and the **word limits** must be respected._
3. (optional) the Rhino (.3dm) file with the structures in separate layers.\
   _For each completed structure before clearing the scene to initiate the next one you can copy the layer_ `IGS>>FormDiagram` _and_ `IGS>>ForceDiagram` _and rename them, for example as_ `IGS_task1_A>>FormDiagram`  and `IGS_task1_A>>ForceDiagram` in _this way they will not be deleted as you move on to the next task. This is a great way to keep track of your advances in the extecise_





# 0. Static determincy
For the following structures, how many internal edges, load and nodes do they have? What is the degree of freedom? 

what is the difference between a truss without diagonals, with one diagonals, and with X diagonals. 


# 1. Analysis of truss bridges
A truss is composed of chords and digonal struts. In this exercise you are given a few truss options for a pedestrian bridge. 

1.1. Create a form diagram for the bridge and compute a force diagram representing the equilibrium of the bridge considering the loads on the deck.

1.2 Estimates maximum strength of the trusses considering the kind of material to use and the element’s thickness.

Given material properties -> one edge exceed the maximum force that's allowed. How to modify the form diagram to minimize the force? 

(1.3 Compute the loadpath? )

1.4 Compute the funicular structure under the load and compare it with the truss. 

---

# 2. the Chiasso Shed
The Chiasso Shed is one of Robert Maillart(1872–1940)'s most intriguing projects. In this exercise, we will study how to use graphic statics to design this structure. 

## 2.1 Analysis of Howe Truss
We will start from a typical triangulated roof structure - a Howe truss. The truss has a span of 18 meters and a height of 3 meters, under constant load 10 kN on each node. Create the form and force diagram of the Howe truss. 

## 2.2 Modification of Force Diagram
You can see that the forces in the top chords are not equal. Inpractice, the top chord would be made entirely of a section with sufficient capacity for the highest compressive load. Modify your force diagram, so that 1. the top chord has constant forces. 2. the diagonal elements has 0 forces. 

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

